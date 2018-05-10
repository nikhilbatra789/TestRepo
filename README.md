# Welcome to StackEdit!

Hi! I'm your first Markdown file in **StackEdit**. If you want to learn about StackEdit, you can read me. If you want to play with Markdown, you can edit me. If you have finished with me, you can just create new files by opening the **file explorer** on the left corner of the navigation bar.


# iOS Integration

Please follow the following steps to integrate iOS Beacon Manager. All of these files can be found in iOS Folder.

1. Add following core files to your target 
	* BeaconManager.h
	* BeaconManager.m
2. Add the following code to your app delegate header (.h) file, inside the interface
        ```obj-c
-(void)startBeaconMonitoring;
-(void)initializeCoreLocation;
@property (strong, nonatomic) RCTBridge *kr_bridge;
        ```
3. Add the following snippets inside your app delegate implementation (.m) file in the respective sections mentioned below
	* Add the following import line
						```obj-c
				#import <CoreLocation/CoreLocation.h>
			```
	* Add private interface in AppDelegate.m (Just Below import Statements)
				```obj-c
		@interface AppDelegate() <CLLocationManagerDelegate>
		@property (strong, nonatomic) CLLocationManager *locationManager;
		@end
				```
	* Add the following code snippet in  **application:didFinishLaunchingWithOptions:** method of app delegate just before returning true
```obj-c
if ([[NSUserDefaults standardUserDefaults] objectForKey:kSavedBeaconMap] == nil) {
[[NSUserDefaults standardUserDefaults] setObject:[NSDictionary new] forKey:kSavedBeaconMap];
}
self.locationManager = [CLLocationManager new];
if([launchOptions objectForKey:@"UIApplicationLaunchOptionsLocationKey"]) {
[self initializeCoreLocation];
}
```
