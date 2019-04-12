```python
import requests

# Just an empty array to have somewhere to append the data that will be
# parsed from the json.
wxdata = []

# Setup the items we need for the requests, parameters and url.
url = 'http://api.weatherlink.com/v1/NoaaExt.json'
params = {'user': 'user_code', 'pass': 'password', 'apiToken': 'API_Token'}

# Use requests to get data and return it in json
r = requests.get(url, params=params)
json_data = r.json()

# Pull out the relavent info that we want and append it to our array
wxdata.append( json_data['temp_c'] )
wxdata.append( json_data['dewpoint_c'] )
wxdata.append( json_data['relative_humidity'] )
wxdata.append( json_data['pressure_mb'] ) 
wxdata.append( json_data['davis_current_observation']['solar_radiation'] )
wxdata.append( json_data['davis_current_observation']['et_day'] )
wxdata.append( json_data['wind_mph'])

# Print to screen the items from the array. This could have just been done
# directly from the json_data variable but for to show some different ideas
# I decided on this methodology.
print("Températrue: ",wxdata[0],"\xb0C","Point de rosée: ",wxdata[1],"\xb0C",
      "Humidité: ",wxdata[2],"%","Baromètre: ",wxdata[3],"mb")
print("Rayonnement Solaire: ",wxdata[4],"W/m\u00b2",
     "Évapotranspiration pour le jour: ",wxdata[5],"mm",
     "Wind Speed: ",wxdata[6])
```
