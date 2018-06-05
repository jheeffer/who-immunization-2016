# who-immunization-2016
2016 immunization report, released in 2017 

## Sample Visualizations

### Subnational Bubbleplot

<img src="https://user-images.githubusercontent.com/156229/40961854-a96456aa-6858-11e8-96a2-3f0ff526ab57.png" width=600 />

### Dropout Rate Treemap

<img src="https://user-images.githubusercontent.com/156229/40961907-cd0825d2-6858-11e8-850d-860e7d6cfc8f.png" width=600 />

### Immunization Punchcard

<img src="https://user-images.githubusercontent.com/156229/40961957-fd9c2cca-6858-11e8-9c8f-1c8dedc38128.jpg" width=400 />

## Running the Examples

Download this repository and put the entire directory onto a webserver to run the examples. This is required to load external data files.

For example, On a MacOS computer, navigate to the directory with Terminal and run this command:

```python -m SimpleHTTPServer 8010```

The examples can now be viewed in a web browser on the same machine at [http://localhost:8010/](http://localhost:8010/)

## Swapping out data files

Sample data files are contained in the `data/` directory. Immunization data is imported as files.

Geographic data is imported as [TopoJSON](https://github.com/topojson/topojson#topojson). To convert shapefiles to TopoJSON format, tools like [mapshaper](http://mapshaper.org/) can be used.

To swap out data files for an example, look for calls to `d3.csv` or `d3.json` in the example and update the filename. For instance, the national WEUNIC data is loaded in one bubbleplot example [here](https://github.com/stamen/who-immunization-2016/blob/master/bubbleplot/subnational_with_wuenic.html#L176):

```d3.csv('../data/wuenic_master_07_06_2017.csv', function(error, wuenic_raw) {```

## Downloading PNG exports

For the punchcard and subnational bubbleplots at the country level, PNG images of each country can be downloaded. Run the following command in a JavaScript console while viewing the web page after the graphs have finished rendering:

```d3.selectAll("canvas")
     .each(function(d,i) {
       var self = this;
       var f = function() {
         self.click()
       }
       setTimeout(f, 120*i);
     })```

Your browser will attempt to download several hundred images over the next 15-45 seconds. A prompt may appear to let the web page download many images. If this happens, it may interrupt the download of some countries. Run the command again after dismissing the prompt to download all the country PNGs.

If you're running the examples with the command at the top of the README, you can test this download script with [this bubbleplot example](http://localhost:8010/bubbleplot/admin2_scaled_12_04_2017.html).
