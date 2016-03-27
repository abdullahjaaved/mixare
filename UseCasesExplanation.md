This page explains the different use-cases as shown on the website: http://www.mixare.org/usage/

## Use case 1, 2 and 3: ##
Mixare is able to parse data in a specific format documented here (
http://code.google.com/p/mixare/wiki/DisplayYourOwnData ) both from
online sources or from the filesystem using the standard android
mechanism like:

Example for online resources:
```
Intent i = new Intent(); 
i.setAction(Intent.ACTION_VIEW); 
i.setDataAndType(Uri.parse("http://your_server/JSONEndpoint"), 
"application/mixare-json"); 
startActivity(i); 
```

Example for locally-stored file:
```
Intent i = new Intent(); 
i.setAction(Intent.ACTION_VIEW); 
i.setDataAndType(Uri.parse("content://com.android.htmlfileprovider/sdcard/Y OUR-JSON-FILENAME"), 
"application/mixare-json"); 
startActivity(i); 
```

The above examples cover **use-case 3** of mixare, if you put the above code
in your application it will launch mixare and it will just work. You do
not have to worry about GPS initialization and further details, as
mixare will take care of that and display the points.
Use case **number 2** is just the same, you just have to ensure that you
webpage contains a link with the appropriate mime-type
(application/mixare-json) and mixare will be launched.

Right now _this is the only supported way to get data in mixare_ (unless
you go for option 4). There is no way (right now) to push a list of
places in the app for you application but using the methods explained
above.

We thought that this was the most meaningful approach as it allows even
non-programmers to use mixare as an augmented reality engine. This
approach also allow the development of **closed source** launchers that
interacts with mixare through this URI pass. This is what we did with
our own apps , since it allowed us to keep our data private.
If you think that other approaches would be better, please answer here
or propose you idea in another thread! We would be delighted to hear
your ideas or proposals.

## About use-case number 4: ##

!IMPORTANT: Please remember that since mixare itself is GPLv3, any
application that is developed on mixare using approach 4 **has** to be
released as GPLv3!

Use-case 4 is meant to build a completely autonomous application based
on top of mixare. We received some feedbacks asking how to embed the
application in other existing ones. As stated above, right now this is
not possible unless you rewrite some of the code of mixare itself. Some
directions about how to do this follow:

**How to change the JSON parsing (to support additional data formats:**

 See the file https://github.com/mixare/mixare/blob/master/src/org/mixare/data/Json.java

**How to had-code some test data places in mixare for testing purposes:**

 See the same file above, basically you have to set the properties of
each Marker's PhysicalPlace (mGeoLoc) object using setLatitude,
setLongitude and setAltitude.

We hope this pointers will help you getting more from mixare.