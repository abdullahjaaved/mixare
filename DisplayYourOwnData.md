#This page documents the data format that mixare understands and how to communicate it to the application.

# Introduction #

Mixare as a standalone application is bound to geonames.org, more specifically to the data taken from wikipedia. When you start the application a call is made to http://ws.geonames.org/findNearbyWikipediaJSON (please see [here](http://www.geonames.org/export/JSON-webservices.html) for details).

# How to launch mixare with your data source #

In order to show your own data through Mixare you may invoke it like this:
```
Intent i = new Intent();
i.setAction(Intent.ACTION_VIEW);
i.setDataAndType(Uri.parse("http://your_server/JSONEndpoint"), "application/mixare-json");
startActivity(i); 
```

Mixare will be invoked by the android system for every call you make to the myme type **application/mixare-json**

It means you can even launch mixare from the browser ;)

# How to use your own datasource from within mixare #

Recent versions of mixare (> v0.7) support adding and editing datasource at runtime. Just go to the datasources list (press menu -> select datasource) and add your own (press menu -> select "add new datasource").

Choose whether the POIs should be displayed as circles or as arrows, and if the format is Mixare(JSON) or OpenStreetMap (XAPI). Then go back, and the datasource will be saved.


# How your data should be encoded #

At the moment mixare supports two types of JSON encoding, the first being the one of geonames.org discussed earlier.

The second format is documented below:
## Please note that the code below is a working example. ##
```
{
    "status": "OK",
    "num_results": 3,
    "results": [
        {
            "id": "2827",
            "lat": "46.43893",
            "lng": "11.21706",
            "elevation": "1737",
            "title": "Penegal",
            "distance": "9.756",
            "has_detail_page": "1",
            "webpage": "http%3A%2F%2Fwww.suedtirolerland.it%2Fapi%2Fmap%2FgetMarkerTplM%2F%3Fmarker_id%3D2827%26project_id%3D15%26lang_id%3D9"
        },
        {
            "id": "2821",
            "lat": "46.49396",
            "lng": "11.2088",
            "elevation": "1865",
            "title": "Gantkofel",
            "distance": "9.771",
            "has_detail_page": "0",
            "webpage": ""
        },
        {
            "id": "2829",
            "lat": "46.3591",
            "lng": "11.1921",
            "elevation": "2116",
            "title": "Roen",
            "distance": "17.545",
            "has_detail_page": "1",
            "webpage": "http%3A%2F%2Fwww.suedtirolerland.it%2Fapi%2Fmap%2FgetMarkerTplM%2F%3Fmarker_id%3D2829%26project_id%3D15%26lang_id%3D9"
        }
    ]
}
```

  * There **must** be an array whos name is "results" at the first level of the JSON object.
  * Each element of the array **must** contain at least _lat_ (latitude), _lng_ (longitude), _elevation_ (could be "0"), _title_ (the string that will be shown below the Marker).
  * Each element of the array **could** contain _webpage_ (a link to the what is shown when the user clicks on the marker) and if it does it **must** contain _has\_detail\_page_ with a value of 1). NB: A value of 0 for _has\_detail\_page_ means that mixare will not consider clicks on that marker.
  * Each element of the array **could** contain _distance_.
  * It is **strongly recommended** to add a **unique** ID to each marker. This ID (among with the title) is used to distinguish among different markers. _(in mixare version < 0.8.2 there was a bug where markers with the same title were collapsed into one even if the ID was specified)_

## Further details ##

Further details are available here: UseCasesExplanation