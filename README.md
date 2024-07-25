This notebook is designed to calculate the distances of each business trip from a single location institution to any destination on the planet. It uses the shortest [geodesic distance](https://en.wikipedia.org/wiki/Geodesics_on_an_ellipsoid), which takes the earth's ellipsoid into account.

In order to use this notebook, **read the introduction, there's important information you might miss** without reading ;)

First of all, you need the geolocation and the name of your institution, as well as an excel file with the trips of interest. These data needs to be inserted into the **[Data Input](#datainput)** section of this notebook.

* In order to get the **geolocation** you can open [google maps](https://www.google.com/maps/) and right-click on the location you are interested in. A new window will open. Click on the two numbers in the first line to copy them to your clipboard. Paste them into the brackets of the `geo_loc` variable, e.g. `geo_loc = (42, 42)`.
* Assign the the **name of your institution** to the `institution_name` variable, e.g. `institution_name = 'Name of Your Institution'`.
* The **excel file with the trips of interest** may contain any number of rows and columns. The file name is specified in the `business_trip_file` variable, e.g. `business_trip_file = 'Your Filename'`. In order to work properly and calculate the distances, the column with the locations needs to be located. This is done via the `location_column` variable. Set it to the proper name, e.g. `location_column = 'Destinations you are Interested in'`.

In order to reduce calculation time, the tool will search for individual destinations and only calculate each distance once and fill all occurances of each destination with that value. Therefore, **your data needs to be prepared properly**, meaning typos and specific adresses should be removed as good as possible. **If there are still errors in the file, the calculation will stop** and, after fixing the error in the excel file, has to be started again. The tool also prints a sorted list with all unique destinations to easen your debugging work. **Approximately 2 destinations are calculated per second**. So, depending on the number of destinations you want know distances to, it takes some patience to wait for the tool calculating, eventhough only unique destinations are used. While calculating, take a rest and drink a cup of tea (you have 1 minute per 100 unique destinations). To estimate calculation times: At our University and approximately 10000 business trips, there are round about 1000 unique destinations, which results in 10 minutes calculation time. 

After processing the data, the tool will save a **new excel file named almost like the original** file with an added `_with_distances`.

You can also decide if the distances should be `'oneway'` or `'roundtrip'` by setting the `calculation_type` accordingly. Setting it to `'oneway'` just takes the shortest possible distance on the planet, setting it to `'roundtrip'` doubles this distance. The default is `'oneway'`.

There is also a short **[summary](#summary)** at the end of this notebook, which gives you a quick overview of your data.
