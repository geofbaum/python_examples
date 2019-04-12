```python
#
# Humidity Gauge
# with Plotly
#

import pylab as plt
import numpy as np
import plotly.plotly as py
import plotly.graph_objs as go

base_chart = {
    "values": [40, 10, 10, 10, 10, 10, 10],
    "labels": ["-", "0", "20", "40", "60", "80", "100"],
    "domain": {"x": [0, .48]},
    "marker": {
        "colors": [
            'rgb(255, 255, 255)',
            'rgb(255, 255, 255)',
            'rgb(255, 255, 255)',
            'rgb(255, 255, 255)',
            'rgb(255, 255, 255)',
            'rgb(255, 255, 255)',
            'rgb(255, 255, 255)'
        ],
        "line": {
            "width": 1
        }
    },
    "name": "Gauge",
    "hole": .4,
    "type": "pie",
    "direction": "clockwise",
    "rotation": 108,
    "showlegend": False,
    "hoverinfo": "none",
    "textinfo": "label",
    "textposition": "outside"
}

meter_chart = {
    "values": [50, 10, 10, 10, 10, 10],
    "labels": ["Humidity", "Dry", "Low", "Average", "High", "Very High"],
    "marker": {
        'colors': [
            'rgb(255, 255, 255)',
            'rgb(232,226,202)',
            'rgb(226,210,172)',
            'rgb(223,189,139)',
            'rgb(223,162,103)',
            'rgb(226,126,64)'
        ]
    },
    "domain": {"x": [0, 0.48]},
    "name": "Gauge",
    "hole": .3,
    "type": "pie",
    "direction": "clockwise",
    "rotation": 90,
    "showlegend": False,
    "textinfo": "label",
    "textposition": "inside",
    "hoverinfo": "none"
}

# Array for  possible Humidity Values 0-100
array_humidty = np.linspace(0, 100, 101)
# Useing that array, find index of humidity value from weather data array
index_humidity = np.where(array_humidity == int(wxdata[2]))
print(index_humidity)
# Similar to array above but for radian values to be used with cosine below
array_rad = np.linspace(-1, 1, 101)

humd = int(wxdata[2])
humd_rad = int(array_rad[index_humidity])
print(humd, humd_rad)
m1 = -0.0022075*np.cos((2.8239*pocky)+0.00000318558)+0.2377502
m2 = (0.0005*humd) + 0.475
l11 = (0.0009*humd) + 0.1975
l12 = 0.06624*np.cos((2.8239*humd_rad)+0.00000281801)+0.56749
l21 = 0.0022073*np.cos((2.82424*humd_rad)-0.00000341834)+0.24225008869
l22 = (-0.0005*humd) + 0.525
path = 'M '+str(m1)+' '+str(m2)+' L '+str(l11)+' '+str(l12)+' L '+str(l21)+' '+str(l22)+' Z'
#print(path)

layout = {
    'xaxis': {
        'showticklabels': False,
        'showgrid': False,
        'zeroline': False,
    },
    'yaxis': {
        'showticklabels': False,
        'showgrid': False,
        'zeroline': False,
    },
    'shapes': [
        {
            'type': 'path',
            'path': path,
            #'path': 'M 0.2375 0.5125 L 0.26125 0.575 L 0.2425 0.4875 Z', 
            # change to equation above to automatically calculate based on % humidity
            'fillcolor': 'rgba(44, 160, 101, 0.5)',
            'line': {
                'width': 0.5
            },
            'xref': 'paper',
            'yref': 'paper'
        }
    ],
    'annotations': [
        {
            'xref': 'paper',
            'yref': 'paper',
            'x': 0.23,
            'y': 0.45,
            'text': wxdata[2],
            'showarrow': False
        }
    ]
}

# we don't want the boundary now
base_chart['marker']['line']['width'] = 0

fig = {"data": [base_chart, meter_chart],
       "layout": layout}
py.iplot(fig, filename='gauge-meter-chart')
```
