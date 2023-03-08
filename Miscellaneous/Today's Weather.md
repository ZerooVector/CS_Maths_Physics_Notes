
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
	return weather_text 
```

## Apply

```python
dict = request_weather_now()
# print(dict["temp"])
weather_df = pd.DataFrame(dict,index = ["value"]).T.reset_index()
# f,ax1 = plt.subplots(figsize = (6.5,2))
# plt.show()
weather_df_data = weather_df.loc[[0,1,3,5,6,7,8,9,10,11,12]]

sns.barplot(x = "value",y = "index",data = weather_df_data)
plt.show()
```
