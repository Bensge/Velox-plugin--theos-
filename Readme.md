#Velox plugin template

This is a plugin tempate for a Velox plugin. Use it with theos (-> nic.pl)


###How do the plugins work?

The plugins are placed into /Library/Velox/Plugins/. When Velox loads (at respring), it loads all plugins and checks if they are valid. 

###How do i specify for which app my plugin is?

There's a key in the plugins Info.plist called 'VeloxAppIDs'. The value is an array of bundle identifiers. Add the bundle identifier of the app you pugin is meant for to that array. Because it's an array, you can also make your folder work with multiple apps.

###Can my folder have a dynamic height?

Yes! There's a method called -(float)realHeight which you can implement in your plugin view. This method gets called right after -initWithFrame, return the height of your folder there. For example, for a plugin showing a tableView, tableView.contentSize.height would be the right thing to return in -realHeight. Please mind that you can notchaneg the folders height while it's visible, only when the plugin gets initalized.

###Are there some example folders?

Yes, there are! Take a look at [this stopwatch folder](https://github.com/maxkatzmann/Velox-Stopwatch) by Max katzmann or [that 'Carrox' folder](https://github.com/hbang/Carrox) by thekirbylover 

###What is the Velox.h file for?

This is the header of the velox manager. You can use the methods to set custom options for your folder plugin like the folder arrow background image, or dim the notch shadow.
Example usage:
		[[objc_getClass("Velox") sharedManager] setAdjustsNotchShadow:YES];
Don't forget to #import "Velox.h" and #import <objc/runtime.h>