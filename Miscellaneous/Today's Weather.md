#Functional 
## Initialization

```python 
import requests
import json

def request_weather_now():
    results = []
    response = requests.get("https://devapi.qweather.com/v7/weather/now?key=95c1d04eb0434a298e0a5cc7fb7c8471&location=101011200&lang=en&unit=m")
    results = response.json()
    weather_text = {}
    weather_text["temp"] = float(results.get("now").get("temp"))
    weather_text["feelsLike"] = float(results.get("now").get("feelsLike"))
    weather_text["text"] = results.get("now").get("text")
    weather_text["wind360"] = float(results.get("now").get("wind360"))
    weather_text["windDir"] = results.get("now").get("windDir")
    weather_text["windScale"] = float(results.get("now").get("windScale"))
    weather_text["windSpeed"] = float(results.get("now").get("windSpeed"))
    weather_text["humidity"] = float(results.get("now").get("humidity"))
    weather_text["precip"] = float(results.get("now").get("precip"))
    weather_text["pressure"] = float(results.get("now").get("pressure"))
    weather_text["vis"] = float(results.get("now").get("vis"))
    weather_text["cloud"] = float(results.get("now").get("cloud"))
    weather_text["dew"] = float(results.get("now").get("dew"))
    weather_df = pd.DataFrame(weather_text,index = ["value"]).T.reset_index()
    return weather_df 
    
def request_rainfall_future():
    results = []
    response = requests.get("https://devapi.qweather.com/v7/minutely/5m?key=95c1d04eb0434a298e0a5cc7fb7c8471&location=115.90,39.60&lang=en")
    results = response.json()
    weather_text = {}
    weather_text["summary"] = results.get("summary")
    return weather_text
def request_weather_future():
    results = []
    response = requests.get("https://devapi.qweather.com/v7/weather/7d?key=95c1d04eb0434a298e0a5cc7fb7c8471&location=101011200&lang=en")
    results = response.json()
    # print(results)
    weather_text = []
    weather_text= results.get("daily")
    fxDate_list = []
    sunrise_list = []
    sunset_list = []
    sunrisetime_list = []
    sunsettime_list = []
    moonrise_list = []
    moonset_list = []
    moonPhase_list = []
    tempMax_list = []
    tempMin_list = []
    textDay_list = []
    textNight_list = []
    humidity_list = []
    precip_list = []
    cloud_list = []
    for ith in range(0,7):
        fxDate_list.append(weather_text[ith].get("fxDate"))
        sunrise_list.append(weather_text[ith].get("sunrise"))
        sunset_list.append(weather_text[ith].get("sunset"))
        sunrisetime_list.append(int(weather_text[ith].get("sunrise")[0:2])*60+int(weather_text[ith].get("sunrise")[3:5])*1)
        sunsettime_list.append(int(weather_text[ith].get("sunset")[0:2])*60+int(weather_text[ith].get("sunset")[3:5])*1)
        moonrise_list.append(weather_text[ith].get("moonrise"))
        moonset_list.append(weather_text[ith].get("moonset"))
        moonPhase_list.append(weather_text[ith].get("moonPhase"))
        tempMax_list.append(float(weather_text[ith].get("tempMax")))
        tempMin_list.append(float(weather_text[ith].get("tempMin")))
        textDay_list.append(weather_text[ith].get("textDay"))
        textNight_list.append(weather_text[ith].get("textNight"))
        humidity_list.append(float(weather_text[ith].get("humidity")))
        precip_list.append(float(weather_text[ith].get("precip")))
        cloud_list.append(float(weather_text[ith].get("cloud")))
    weather_dict = {"date":fxDate_list,"sunrise":sunrise_list,"sunset":sunset_list,
                    "sunrisetime":sunrisetime_list,"sunsettime":sunsettime_list,
                   "moonrise":moonrise_list,"moonset":moonset_list,"moonphase":moonPhase_list,
                   "maxtemp":tempMax_list,"mintemp":tempMin_list,"dayweather":textDay_list,"nightweather":textNight_list,
                   "humidity":humidity_list,"rainfall":precip_list,"cloud":cloud_list}
    weather_df = pd.DataFrame(weather_dict)
    weather_df["date"] = pd.to_datetime(weather_df["date"])
    weather_df["daylength"] = (weather_df["sunsettime"]-weather_df["sunrisetime"])/60 
    return weather_df 


```



## Apply 1：Current Weather 

```python
sns.set_theme(style = "darkgrid")

weather_df = request_weather_now()
weather_df_data = weather_df.loc[[0,1,3,5,6,7,8,9,10,11,12]]
weather_temp = weather_df_data.loc[[0,1]]
weather_hum = weather_df_data.loc[[7,11]]
weather_rain = weather_df_data.loc[[8]]
future_rainfall_text = request_rainfall_future()["summary"]


print("Now,The WEATHER is :",weather_df.iloc[2,1])
print("The RAINFALL in last one hour is :",weather_df.iloc[8,1],"mm")
print("The WIND DIRECTION is :",weather_df.iloc[4,1]," , and the WINDSCALE is :",weather_df.iloc[5,1])
print("Is there any RAINFALL in following 2HOURS? ", future_rainfall_text)
print("----- The following figures show the TEMP, FEELSLIKE TEMP, HUMID, and CLOUD COVER :------")

f,ax1 = plt.subplots(figsize = (7,2.4))
maxpos = max(30,weather_temp.iloc[0,1],weather_temp.iloc[1,1])
minpos = 0
if weather_temp.iloc[0,1]<0 or weather_temp.iloc[1,1]<0 :
	minpos = min(-10,weather_temp.iloc[0,1],weather_temp.iloc[0,1])
	maxpos = 15
color_series = sns.color_palette("Spectral_r", 45)
color1 = max(min(weather_temp.iloc[0,1]+10,44),0)
color2 = max(min(weather_temp.iloc[1,1]+10,44),0)
pat = [color_series[int(color1)],color_series[int(color2)]]
sns.barplot(x = "value",y = "index",data = weather_temp,ax =ax1,palette=pat)
ax1.set_xlim([minpos,maxpos])
ax1.set_ylabel("")
ax1.set_xlabel("")
plt.show()
plt.close()

f,ax2 = plt.subplots(figsize = (7,2.4))
maxpos = 100
minpos = 0
color_series1 = sns.color_palette("YlGnBu", 120)
color_series2 = sns.color_palette("Greys", 170)
color1 = weather_hum.iloc[0,1]+0
color2 = weather_hum.iloc[1,1]+20
pat = [color_series1[int(color1)],color_series2[int(color2)]]
sns.barplot(x = "value",y = "index",data = weather_hum,ax =ax2,palette=pat)
ax2.set_xlim([minpos,maxpos])
ax2.set_ylabel("")
ax2.set_xlabel("")
plt.show()
plt.close()
```


## Apply 2 : Future Weather Forecast 

```python
weather_df = request_weather_future()
sns.set_theme(style = "darkgrid")  
f,ax1 = plt.subplots(figsize = (7,4))
sns.lineplot(x = "date", y = "maxtemp", data = weather_df ,ax = ax1,linewidth = 2,color = "firebrick",marker = "^")
# sns.scatterplot(x = "date", y = "maxtemp", data = weather_df ,ax = ax1,)
sns.lineplot(x = "date", y = "mintemp", data = weather_df ,ax = ax1, linewidth = 2,color = "royalblue",marker = "v")
# sns.scatterplot(x = "date", y = "mintemp", data = weather_df ,ax = ax1,)
# plt.legend(["MAX","MIN"])
plt.xticks(rotation = 15)
ax1.set_ylabel("temp")
ax1.set_xlabel("")
plt.show() 
plt.close()


f,ax2 = plt.subplots(figsize = (7,4))
# ax3 = ax2.twinx()
sns.lineplot(x = "date", y = "humidity", data = weather_df ,ax = ax2,linewidth = 2,color = "darkgreen",marker = "o")
# sns.lineplot(x = "date",y = "rainfall",data = weather_df,ax = ax3)
plt.xticks(rotation = 15)
ax2.set_xlabel("")
# ax3.set_xlabel("")
# ax3.set_ylim([0,max(10,max(weather_df["rainfall"]))])
plt.show() 
plt.close()

f,ax4 = plt.subplots(figsize = (7,4))
sns.lineplot(x = "date", y = "rainfall", data = weather_df ,ax = ax4,marker = 'D',color = "deepskyblue",linewidth = 2)
plt.xticks(rotation = 15)
ax4.set_xlabel("")
ax4.set_ylim([-1,max(10,max(weather_df["rainfall"]))])
plt.show() 
plt.close()

f,ax5 = plt.subplots(figsize = (7,4))
sns.lineplot(x = "date", y = "daylength", data = weather_df ,ax = ax5,marker = 'D',color = "darkorange",linewidth = 2)
plt.xticks(rotation = 15)
ax5.set_xlabel("")
plt.show() 
plt.close()

print("Other information is listed in the following table:")
print(weather_df[["date","dayweather","nightweather","sunrise","sunset"]].head(7))
print(weather_df[["date","moonrise",'moonset',"moonphase","cloud"]].head(7))


```
