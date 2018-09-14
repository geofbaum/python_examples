```python
import requests
#http = urllib3.PoolManager()
url = 'http://api.weatherlink.com/v1/NoaaExt.json'
params = {'user': 'user_code', 'pass': 'password', 'apiToken': 'API_Token'}
##def getWxData():
wxdata = []
#r = http.request('GET', 'http://api.weatherlink.com/v1/NoaaExt.json?user=001D0A00E0A1&pass=christophe&apiToken=4A8512DD05734F6B8C3DECC6CD7428A5')
r = requests.get(url, params=params)
#print(r.headers)
#print(r.json())
json_data = r.json()
#print(json_data)
    
wxdata.append( json_data['temp_c'] )
wxdata.append( json_data['dewpoint_c'] )
wxdata.append( json_data['relative_humidity'] )
wxdata.append( json_data['pressure_mb'] ) 
wxdata.append( json_data['davis_current_observation']['solar_radiation'] )
wxdata.append( json_data['davis_current_observation']['et_day'] )
wxdata.append( json_data['wind_mph'])
    #return wxdata

#weather = getWxData()
print("Températrue: ",wxdata[0],"\xb0C","Point de rosée: ",wxdata[1],"\xb0C","Humidité: ",wxdata[2],"%","Baromètre: ",wxdata[3],"mb")
print("Rayonnement Solaire: ",wxdata[4],"W/m\u00b2","Évapotranspiration pour le jour: ",wxdata[5],"mm","Wind Speed: ",wxdata[6])
print(int(wxdata[2]))
```
