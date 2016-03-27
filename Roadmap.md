# Open Tasks #

## Datasources ##
  * Downloading
    * Automatically updating datasources in intervals provided by datasource
  * ARML support
  * GeoJSON support
  * act as WFS Client (WFS = Web Feature Service)
    * http://www.opengeospatial.org/standards/wfs
    * as XML
    * as GeoJSON
  * Local/custom datasources
    * Showing “local” datasources in datasources menu depending on actual user position
    * Showing market links to separate apps with local content.
    * For custom/launcher apps show specific datasource as first entry in datasource menu
    * Custom datasource dialog should always be shown when clicking on it (not only for long clicks)
  * Meta or link tag on websites pointing to datasource

## Marker ##
  * Clustering
    * Show text only for foremost marker
    * POIs being behind only show circles
    * Zoom? functionality
      * Show hidden marker after clicking foremost one
        * Row by row or
        * Radially, like Google Earth does or
        * Zoom into the screen with Pinch-to-zoom
    * Stack social media messages like HTC SMS widget
  * Detailed text boxes
    * Shown on the lower part of the screen after clicking on a POI
    * Contents
      * Image of datasource
      * Title
      * Long description
      * Clicking on it activates WebView to the provided link
    * Sliding right/left on text box switches to the next POI right/left of the current one
    * Currently selected POI should be highlighted (the corresponding circle and the point in the radar)
    * Add support for lines and polygons
      * use OpenGL ES

## UI ##
  * Side arrows
    * Show a small arrow with amount of POIs being outside of the screen on the left and right side of the screen
  * Portrait mode
  * When holding device horizontally automatically switch to MapView
  * Aearoplane mode like Layar has
  * Clicking Back twice should exit Mixare
  * ListView
    * On the top of the list show all visible markers and below all other downloaded but invisible markers

## Sensors ##
  * Compass
    * Smooth compass measurements
    * Show notification when compass measurements are not reliable
  * Integration with high precision DTM (Digital Terrain Model) and visibility analysis
    * using WPS (http://www.opengeospatial.org/standards/wps)

## Searching/Filtering ##
  * Distinguish between searching and filtering
    * Filtering: Filters downloaded marker data for a keyword
    * Searching: Querying datasources with a keyword or some kind of category
  * Not matching markers should be transparent
  * Filtering should be done on complete marker list (not only visible ones)
  * Searching can be done in datasource menu like selecting a tag/feature category for openstreetmap or wikipedia


# Completed Tasks #
## Datasources ##
  * Downloading
    * Downloading and showing multiple datasources simultaneously

## Marker ##
  * Different marker categories
    * Social media markers
      * Social media messages floating in the sky in speech bubbles
        * Distance has influence on size and angle of the speech bubble
    * POI markers
      * Geographic features like wikipedia entries
    * Navigation markers
      * Small arrows pointing to objects like cities or train stations
  * Two marker lists
    * all downloaded markers
    * visible markers
  * Distance
    * Show distance as number
    * Make distant POIs increasingly transparent --> distance is encoded through circle diameter
  * Remember from which datasource the marker originates

## UI ##
  * MapView
    * Only show 10? icons with logo, all other markers with small red dot to increase performance --> Not necessary, mapview had a bug and it is fixed now

## Sensors ##
  * GPS Height
    * POIs without height information should be shown on the same height as the user or with elevation angle zero