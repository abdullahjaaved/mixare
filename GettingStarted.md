**The follwing tutorial applies for mixare v0.8 and above**

# Importing and compiling the project #

Once you forked or cloned the project from github, you can start importing mixare in your workspace.
Since version 0.8 mixare contains 2 parts. The core part and the library (mixarelib) part.

In order to successfully import the mixare project into your workspace, you need to import the library of mixare. The library can be found in _plugins/mixarelib_


---


You first have to import both the mixare and the mixarelib into your workspace.

After you added both projects, you have to convert mixarelib into a android library project, you can do that by richtclicking on the mixarelib -> go to properties -> select android -> scroll down -> and then check the "is Libary" checkbox.

Then rightclick on the mixare project -> go to properties -> select android -> scroll down -> and then add the mixarelib as the project library.

## Lint issues (translation errors) ##

Since a recent updated of the android tools, Lint translation errors are considered "fatal". It means that you will not be able to create the apk of mixare if the localization files are missing some strings.

A solution is to change the error level to something different than "fatal" for the property "MissingTranslation". To do this proceed as follows: right click on project -> choose properties -> choose "android lint preferences" -> under "correctness: Messages" choose "MissingTranslation" -> change severity to something else than fatal.

Than, if **your** language is among the one missing strings, please consider sending a patch with the updated file :-)


Good luck