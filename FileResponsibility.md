# File/Class responsibilities of the iPhone version #

  * _MixareAppDelegate_
```
  The main class of the app. It controls the whole programm flow. 
```
  * **gui**
    * _MarkerView_
```
  UiView which shows the info web page of a poi on the screen when tapping on a circle in the cam-view.
```
    * _NotificationViewController_
```
  Manages a small loading notification, which is shown when the info web page of a poi is loading
```
    * _WebViewController_
```
  Manages the web page view of a poi when tapping on a poi cell in the list view
```
    * **radarView**
      * _Radar_
```
  Class which draws the radar with the points on the screen
```
      * _RadarViewPort_
```
  Class which marks the visible area which is visible for the user
```
    * **tabbarControllers**
      * **augmentedView**
        * _AugmentedGeoViewController_
```
  This class is used in the appDelegate to instanciate the augmented view with the used center location.
```
        * _AugmentedViewController_
```
  The main class for the CameraView. It makes all calculation and mappings from virtual world in the "camera World".
  Draws the markers on the screen and updates them. Manages device and heading motion. 
```
      * **sourceView**
        * _SourceTableCell_
```
  This class represents a custom UITableViewCell with a large image on the right side and a label.
```
        * _SourceTableViewController_
```
  Class which manages the source view on the tabbar.
```
      * _ListViewController_
```
  Manages the list view of the pois on the tabbar.
```
      * _MapViewController_
```
  Manages the map view of the pois on the tabbar.
```
      * _MoreViewController_
```
  Manages the infot view of the app on the tabbar - the more section with license and gps info.
```
  * **data**
    * **json**
```
  Open source json framwework (not written by me)
```
    * _DataHandler_
```
  not used at the moment
```
    * _DataSource_
```
  Class which manages sourcesand makes the download requests for each source.
```
    * _JsonHandler_
```
  Class which parses the different json files of the sources and generate a Array of all elements.
```
    * _XMLHandler_
```
  Not used at the moment.
```
  * **reality**
    * _PhysicallyPlace_
```
 Class which represents a real poi.
```
    * _PoiItem_
```
  Class which manages a poi with all of its properties.
```
