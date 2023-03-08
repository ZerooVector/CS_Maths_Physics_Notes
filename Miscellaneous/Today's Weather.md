
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
    response = requests.get("https://devapi.qweather.com/v7/minutely/5m?key=95c1d04eb0434a298e0a5cc7fb7c8471&location=116.41,39.92&lang=en")
    results = response.json()
    weather_text = {}
    weather_text["summary"] = results.get("summary")
    return weather_text
```

## Apply

```python
weather_df = request_weather_now()
weather_df_data = weather_df.loc[[0,1,3,5,6,7,8,9,10,11,12]]
weather_temp = weather_df_data.loc[[0,1]]
weather_hum = weather_df_data.loc[[7,11]]
weather_rain = weather_df_data.loc[[8]]
future_rain_d

print("Now,The WEATHER is :",weather_df.iloc[2,1])
print("The RAINFALL in last one hour is :",weather_df.iloc[8,1],"mm")
print("The WIND DIRECTION is :",weather_df.iloc[4,1]," , and the WINDSCALE is :",weather_df.iloc[5,1])
print("Is there RAINFALL in next 2HOUR? ",)
print("----- The following figures show the TEMP, FEELSLIKE TEMP, HUMID, and CLOUD COVER :------")

f,ax1 = plt.subplots(figsize = (6.5,1.9))
maxpos = max(30,weather_temp.iloc[0,1],weather_temp.iloc[1,1])
minpos = 0
if weather_temp.iloc[0,1]<0 or weather_temp.iloc[1,1]<0 :
    minpos = min(-10,weather_temp.iloc[0,1],weather_temp.iloc[0,1])
    maxpos = 10
color_series = sns.color_palette("Spectral_r", 40)
color1 = max(min(weather_temp.iloc[0,1]+10,39),0)
color2 = max(min(weather_temp.iloc[1,1]+10,39),0)
pat = [color_series[int(color1)],color_series[int(color2)]]
sns.barplot(x = "value",y = "index",data = weather_temp,ax =ax1,palette=pat)
ax1.set_xlim([minpos,maxpos])
ax1.set_ylabel("")
ax1.set_xlabel("")
plt.show()
plt.close()

f,ax2 = plt.subplots(figsize = (6.5,2))
maxpos = 100
minpos = 0
color_series1 = sns.color_palette("Blues", 100)
color_series2 = sns.color_palette("Greys", 150)
color1 = weather_hum.iloc[0,1]
color2 = weather_hum.iloc[1,1]
pat = [color_series1[int(color1)],color_series2[int(color2)]]
sns.barplot(x = "value",y = "index",data = weather_hum,ax =ax2,palette=pat)
ax2.set_xlim([minpos,maxpos])
ax2.set_ylabel("")
ax2.set_xlabel("")
plt.show()
plt.close()
```
