---
tags: AIOT
---

# Day 05

* **API** 使用  
    此[連結](https://sta.ci.taiwan.gov.tw/STA_AirQuality_v2/v1.0/)為**環保署國家空品測站 SensorThings API 服務網址**
    ```python
    #!/usr/bin/env python3
    
    import requests
    import pprint
    
    # URL for the API
    url = "https://sta.ci.taiwan.gov.tw/STA_AirQuality_v2/v1.0/"
    
    # POST the request to the server
    response = requests.get(url)
    # GET the response from the server and grab the json
    result = response.json()
    
    # Using pprint to show the beauty format
    # You can use print also
    pprint.pprint(result)
    ```
* **API** 使用 2  
    ```python
    import requests
    import argparse

    # Add parser
    parser = argparse.ArgumentParser()
    parser.add_argument("--length", type=int)

    # Parse the argument
    args = parser.parse_args()
    len_data = args.length
    if (len_data > 100):
        print("The return data should smaller then 100")
        exit(1)

    # Get the json data
    url = "https://sta.ci.taiwan.gov.tw/STA_AirQuality_EPAIoT/v1.0/Things"
    response = requests.get(url)
    data = response.json()

    # Get the amount of data
    print("The total amount of data is {}.".format(data["@iot.count"]))
    # Next page link
    print("To visit next page , please follow {}".format(data["@iot.nextLink"]))

    # Get the detail of each value
    value = data["value"]
    print("\nThere are {} data in this page".format(len(value)))

    for i in range(len_data):
        print("=============data {}=============".format(value[i]["@iot.id"]))
        print("Description:", value[i]["description"])
         # You can print set up your own data
     ```
* 個別資料
```json
{
   "@iot.count":3,
   "value":[
      {
         "description":"相對溼度",
         "@iot.id":2,
         "name":"Relative humidity",
         "observationType":"http://www.opengis.net/def/observationType/OGC-OM/2.0/OM_Measurement",
         "observedArea":{
            "type":"Point",
            "coordinates":[
               121.41965,
               24.98162
            ]
         },
         "phenomenonTime":"2020-12-11T21:02:00.000Z/2020-12-12T01:56:00.000Z",
         "resultTime":null,
         "@iot.selfLink":"https://sta.ci.taiwan.gov.tw/STA_AirQuality_EPAIoT/v1.0/Datastreams(2)",
         "unitOfMeasurement":{
            "name":"percentage",
            "symbol":"%",
            "definition":"https://en.wikipedia.org/wiki/Percentage"
         },
         "Sensor@iot.navigationLink":"https://sta.ci.taiwan.gov.tw/STA_AirQuality_EPAIoT/v1.0/Datastreams(2)/Sensor",
         "Thing@iot.navigationLink":"https://sta.ci.taiwan.gov.tw/STA_AirQuality_EPAIoT/v1.0/Datastreams(2)/Thing",
         "Observations@iot.navigationLink":"https://sta.ci.taiwan.gov.tw/STA_AirQuality_EPAIoT/v1.0/Datastreams(2)/Observations",
         "ObservedProperty@iot.navigationLink":"https://sta.ci.taiwan.gov.tw/STA_AirQuality_EPAIoT/v1.0/Datastreams(2)/ObservedProperty"
      },
      {
         "description":"細懸浮微粒 PM2.5",
         "@iot.id":1,
         "name":"PM2.5",
         "observationType":"http://www.opengis.net/def/observationType/OGC-OM/2.0/OM_Measurement",
         "observedArea":{
            "type":"Point",
            "coordinates":[
               121.41965,
               24.98162
            ]
         },
         "phenomenonTime":"2020-12-11T21:02:00.000Z/2020-12-12T01:56:00.000Z",
         "resultTime":null,
         "@iot.selfLink":"https://sta.ci.taiwan.gov.tw/STA_AirQuality_EPAIoT/v1.0/Datastreams(1)",
         "unitOfMeasurement":{
            "name":"microgram per cubic meter",
            "symbol":"μg/m3",
            "definition":"https://acronyms.thefreedictionary.com/ug%2Fm3"
         },
         "Sensor@iot.navigationLink":"https://sta.ci.taiwan.gov.tw/STA_AirQuality_EPAIoT/v1.0/Datastreams(1)/Sensor",
         "Thing@iot.navigationLink":"https://sta.ci.taiwan.gov.tw/STA_AirQuality_EPAIoT/v1.0/Datastreams(1)/Thing",
         "Observations@iot.navigationLink":"https://sta.ci.taiwan.gov.tw/STA_AirQuality_EPAIoT/v1.0/Datastreams(1)/Observations",
         "ObservedProperty@iot.navigationLink":"https://sta.ci.taiwan.gov.tw/STA_AirQuality_EPAIoT/v1.0/Datastreams(1)/ObservedProperty"
      },
      {
         "description":"溫度",
         "@iot.id":3,
         "name":"Temperature",
         "observationType":"http://www.opengis.net/def/observationType/OGC-OM/2.0/OM_Measurement",
         "observedArea":{
            "type":"Point",
            "coordinates":[
               121.41965,
               24.98162
            ]
         },
         "phenomenonTime":"2020-12-11T21:02:00.000Z/2020-12-12T01:56:00.000Z",
         "resultTime":null,
         "@iot.selfLink":"https://sta.ci.taiwan.gov.tw/STA_AirQuality_EPAIoT/v1.0/Datastreams(3)",
         "unitOfMeasurement":{
            "name":"degree celsius",
            "symbol":"°C",
            "definition":"https://en.wikipedia.org/wiki/Celsius"
         },
         "Sensor@iot.navigationLink":"https://sta.ci.taiwan.gov.tw/STA_AirQuality_EPAIoT/v1.0/Datastreams(3)/Sensor",
         "Thing@iot.navigationLink":"https://sta.ci.taiwan.gov.tw/STA_AirQuality_EPAIoT/v1.0/Datastreams(3)/Thing",
         "Observations@iot.navigationLink":"https://sta.ci.taiwan.gov.tw/STA_AirQuality_EPAIoT/v1.0/Datastreams(3)/Observations",
         "ObservedProperty@iot.navigationLink":"https://sta.ci.taiwan.gov.tw/STA_AirQuality_EPAIoT/v1.0/Datastreams(3)/ObservedProperty"
      }
   ]
}
```

> 這 **json** 檔案包含各種資料。