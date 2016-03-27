## Current Market release ##

### v0.9 ###

  * memory optimizations (a lot!)
  * code refactoring (a lot!)
  * updated api level to Google API level 10
  * various fixes in existing languages files
  * added loading plugin through launcher support in the manifest
  * added support for reading offline datasources (fixed file:// url readings)
  * fixed refresh on datasource change
  * Fixed location finding. Accuracy of the location increased.
  * Work Flow Enhancements: setZoomLevel should not refreash downloads, repaint should only repaint, better maintains of view (onRestart),removed duplicate getDownloadManager, secure Loging
  * MixMap enhancements
  * Added Sending results among activities + few enhancements
  * Fixed DataView Click event for not set keypads + click calculate angle check after validation
  * Refactor Radar viewing, and secure radarText function
  * Add Arabic Language support. (supported on 2.3.3 and later)
  * Added UML diagrams
  * DownloadManager using new thread safe structure
  * New DataSourceManager class - DownloadManager explose - created mgr package
  * Added a prompt, if there are plugins installed. This gives the user the choice to use the plugins, or not.
  * Added walking route in mapview and toggle buttons for it.
  * Added support for Intents can be fired if a url supports it. changed: processUrl and loadwebpage in mixview


## Current Development ##

The features in the Development branch will be part of the next major release, features in the Master/Hotfix branch will be released to the market as minor updates as soon as they are tested.

### DEVELOPMENT branch ###
  * no changes since current market release

### MASTER/HOTFIX branch ###
(this reflects the changes in the current master branch on github: see https://github.com/mixare/mixare )
  * no changes since current market release
<a href='Hidden comment: 
'></a>


## Past releases ##

### v0.8.2 ###
  * dutch language support
  * code cleanup MixListView is now used only for POIs list
  * mp3 /mp4 support in webview
  * code cleanup and licensing update

### v0.8.1 ###
  * FIX of various issues

### v0.8 ###
  * NEW Refactored code and plugin structure. Developers can now customize mixare behavior (datasources, etc.)
  * REMOVED Buzz datasource. Buzz does not exist anymore

### v0.7.x ###
  * NEW Added support for custom datasource defined at runtime (the user can add new datasource and edit them)
  * a few bugfix release were made

### v0.6.6 ###
  * FIX [issue 74](https://code.google.com/p/mixare/issues/detail?id=74) - underline POIs with links in AR view (thanks leg!)
  * FIX [issue 74](https://code.google.com/p/mixare/issues/detail?id=74) - underline POIs with links in list view (thanks leg!)
  * FIX [issue 67](https://code.google.com/p/mixare/issues/detail?id=67) - display the message about compass errors only a few times (thanks leg!)

### v0.6.5 ###
  * FIX [issue 71](https://code.google.com/p/mixare/issues/detail?id=71) (thanks leg!)

### v0.6.4 ###
  * FIX [issue 64](https://code.google.com/p/mixare/issues/detail?id=64) (thanks kunlgt82!)
  * target SDK: 9 (gingerbread)
  * FIX [issue 63](https://code.google.com/p/mixare/issues/detail?id=63) (thanks to the community of samdroid)

### v0.6.3 ###
  * FIX [issue 52](https://code.google.com/p/mixare/issues/detail?id=52), local data source

### v0.6.2 ###
  * FIX the tapping the map before the content is downloaded now works

### v0.6.1 ###
  * FIX the click on the markers work are now more reliable

### v0.6 ###
  * NEW multiple data sources may be selected at once
  * NEW floating social media markers
  * NEW graphics for social media markers
  * NEW navigation arrows for Openstreetmap railway stations
  * NEW dynamic diameter for POIs
  * FIX Better performances

### v0.5 ###
  * NEW data source: Openstreetmap railway stations
  * NEW data source: Custom URL
  * NEW feature: search among displayed entries
  * NEW language: Spanish

### v0.4.1 ###
  * bugfix (double press menu on menulist and datasource could forceclose mixare)
  * bugfix twitter returns error when requested radius < 1km

### v0.4 ###
  * Added Google maps as visualization option
  * Added google buzz as data provider (thanks hanbo)
  * Many many bugfixes

### v0.3 ###
  * Added compatibility with Froyo (Android 2.2) and Froyo install to sd card
  * Added twitter as data source (very early integration)
  * Various fixes in the list view
  * Menu enhancements

### v0.2 ###
  * Added menu
  * Added german translation
  * Added italian translation
  * Added persistent preferences (radius)
  * Added "show license at first start"
  * Added list view
  * Added GPS fix notifications
  * Added failed download notifications
  * Fixed download nullpointerexception

### v0.1.1 beta ###
  * compatibility with android 1.5
  * camera on Nexus One fixed

### v0.1 beta (first version) ###
  * the app may fail to start (NullpointerException) if you never had a GPS fix after last reboot.
  * the camera in the Nexus one is not working