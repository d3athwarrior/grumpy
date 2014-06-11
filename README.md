ogc-tools
=============

[OGC WMS](http://www.opengeospatial.org/standards/wms) Server in java allowing custom rendering of WMS layers using projection utilities and Graphics2D.

Getting started
-------------------

```
git clone https://github.com/davidmoten/ogc-tools.git
cd ogc-tools
mvn clean install
```


Demonstration
-----------------
```
cd wms-demo
mvn jetty:run
```

Go to [http://localhost:8080](http://localhost:8080/wms-demo) with a browser.

And at the map link you will see this:

<img src="https://raw.githubusercontent.com/davidmoten/ogc-tools/master/src/docs/demo.png"/>

This demonstrates a custom filled shape and some text that is placed around the position of Canberra on the map. Notice that the borders are great circle paths.

How is it done? Easy!

###Create a layer:

See [CustomLayer.java](https://github.com/davidmoten/ogc-tools/blob/master/wms-demo/src/main/java/com/github/davidmoten/geo/wms/demo/CustomLayer.java) for how to render a layer using a ```Projector``` and a ```RendererUtil```.

###Define the service capabilities:

See [wms-capabilities.xml](https://github.com/davidmoten/ogc-tools/blob/master/wms-demo%2Fsrc%2Fmain%2Fresources%2Fwms-capabilities.xml) which should conform to the OGC WMS 1.3 schema.

###Create a servlet to serve the layer and capabilities:

See [WmsServlet.java](https://github.com/davidmoten/ogc-tools/blob/master/wms-demo%2Fsrc%2Fmain%2Fjava%2Fcom%2Fgithub%2Fdavidmoten%2Fgeo%2Fwms%2Fdemo%2FWmsServlet.java) for how an ```HttpServlet``` is created to server WMS requests. You do need to register this servlet against a url of course in [web.xml](https://github.com/davidmoten/ogc-tools/blob/master/wms-demo/src/main/webapp/WEB-INF/web.xml).

From this point you have a working WMS service against the url for the ```WmsServlet```!

To see it all in the browser, ```wms-demo``` project uses [OpenLayers](http://openlayers.org/) javascript libraries and google maps to display the world and the custom layer.


