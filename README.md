#CYHelper
## **NOTE**
This project is not longer maintained.

## About
CYHelper is an Objective-C library for iOS developer. It try to provides all the useful features of iOS and wrap them to be easy-to-use API.

## What's new?
###1.1.5
* UIDevice category for platform infomation.

See More at [ChangeLog.md](https://github.com/lancy/CYHelper/blob/master/ChangeLog.md)

## Features
* UIDevice category for platform infomation.
* NSArray and NSSet utils: map, filter and reject with block, flattenArray.
* Days with in era from date to date.
* Easy to associcated objects.
* Attach userinfo to UIAlertView, UIActionSheet, UIControl
* Easy to post and observe notification to default notification center.
* Easy to access subarray
* Convert date to string with date format
* JSON Serialization with NSData, NSString, NSDictionary
* MD5 generation with NSData, NSString
* Word Tokenization with string.
* Singleton(sharedInstance Method) macro
* Runtime print call stack
* Check OS version, app version, device model
* Check whether device is jail broken
* Perform block after delay
* Create UIColor With RGBHex
* Easy to access x, y, centerY, centerX, width, height, right, bottom, origin and size of UIView.
* Determind is iPhone or iPad
* Remove all subviews of view
* NSNumber simple calculation.

## Requirements
* iOS 5.0 or later
* support ARC

## Installation
* Use CocoaPods to install CYHelper.
* Or simply drag CYHelper folder to your project, and import "CYHelper.h". Otherwise you can also add individual componet of CYHelper, just import corresponding head files.

## API List
### UIDevice+CYHardware.h (NEW)
    - (NSString *)platform;
    - (CYPlatformType)platformType;
    - (NSString *)platformString;

### UIAlertView + CYHelper.h
    @property (strong, nonatomic) NSDictionary *userInfo;
### UIActionView + CYHelper.h
    @property (strong, nonatomic) NSDictionary *userInfo;
### UIControl + CYHelper.h
    @property (strong, nonatomic) NSDictionary *userInfo;
### NSObject + AssociatedObjects.h
    - (void)associateValue:(id)value withKey:(const void *)key;
    - (void)atomicallyAssociateValue:(id)value withKey:(const void *)key;
    - (void)associateCopyOfValue:(id)value withKey:(const void *)key;
    - (void)atomicallyAssociateCopyOfValue:(id)value withKey:(const void *)key;
    - (void)weaklyAssociateValue:(id)value withKey:(const void *)key;
    - (id)associatedValueForKey:(const void *)key;
    - (void)removeAllAssociatedObjects;
    + (void)associateValue:(id)value withKey:(const void *)key;
    + (void)atomicallyAssociateValue:(id)value withKey:(const void *)key;
    + (void)associateCopyOfValue:(id)value withKey:(const void *)key;
    + (void)atomicallyAssociateCopyOfValue:(id)value withKey:(const void *)key;
    + (void)weaklyAssociateValue:(id)value withKey:(const void *)key;
    + (id)associatedValueForKey:(const void *)key;
    + (void)removeAllAssociatedObjects;


### NSNumber + CYHelper.h
    // DO NOT USE THEM when you have perfomace problem.
    // These method convert NSNumber to NSDecimalNumber to process the calculation.
    // I provide these methods just for convenience.
    // NSDecimal(C-level) is much faster than NSDecimalNumber, can be a better choice.
    - (NSNumber *)addNumber:(NSNumber *)number;
    - (NSNumber *)subNumber:(NSNumber *)number;
    - (NSNumber *)mulNumber:(NSNumber *)number;
    - (NSNumber *)divNumber:(NSNumber *)number;
    - (NSNumber *)modNumber:(NSNumber *)number;

### NSObject + CYNotification.h
    - (void)postNotificationName:(NSString *)notificationName;
    - (void)postNotificationName:(NSString *)notificationName userInfo:(NSDictionary *)userInfo;
    - (void)observeNotificationName:(NSString *)notificationName selector:(SEL)selector;
    - (void)unObserveNotificationName:(NSString *)notificationName;

### NSObject + CYHelper.h
    - (void)performBlock:(void (^)(void))block afterDelay:(NSTimeInterval)delay;
    
### UIColor + CYHelper.h
    + (UIColor *)colorWithRGBHex:(UInt32)hex;
    + (UIColor *)colorWithRGBHex:(UInt32)hex alpha:(CGFloat)alpha;
    
### UIView + CYHelper.h
    @property (nonatomic) CGFloat x;
    @property (nonatomic) CGFloat y;
    @property (nonatomic) CGFloat width;
    @property (nonatomic) CGFloat height;
    @property (nonatomic) CGSize size;
    @property (nonatomic) CGPoint origin;
    @property (nonatomic) CGFloat bottom;
    @property (nonatomic) CGFloat right;
    @property (nonatomic) CGFloat centerX;
    @property (nonatomic) CGFloat centerY;
    - (void)removeAllSubviews;

### NSArray + CYHelper.h
    - (NSArray *)subarrayFromIndex:(NSUInteger)index;
    - (NSArray *)subarrayToIndex:(NSUInteger)index;
    - (NSArray *)map:(id (^)(id value))handlerBlock;
    - (NSArray *)filter:(BOOL (^)(id value))handlerBlock;
    - (NSArray *)reject:(BOOL (^)(id value))handlerBlock;
    - (NSArray *)flattenArray;
### NSSet + CYHelper.h
    - (NSSet *)map:(id (^)(id value))handlerBlock;
    - (NSSet *)filter:(BOOL (^)(id value))handlerBlock;
    - (NSSet *)reject:(BOOL (^)(id value))handlerBlock;
### NSDate + CYHelper.h
    // example: dateFormat:@"yyyy-MM-dd 'at' HH:mm";
    // formattedDateString: 2001-01-02 at 13:00
    - (NSString *)stringWithDateFormat:(NSString *)dateFormat;
    - (NSInteger)daysWithinEraToDate:(NSDate *)toDate;
### NSDictionary + CYHelper.h
    - (NSData *)jsonData;
    - (NSString *)jsonString;
### NSData + CYHelper.h
    - (NSData *)MD5;
    - (NSString *)MD5String;
    - (NSDictionary *)jsonObject;
### NSString + CYHelper.h
    - (NSDictionary *)jsonObject;
    - (NSString *)MD5String;
    - (NSArray *)arrayWithWordTokenize;
    - (NSString *)separatedStringWithSeparator:(NSString *)separator;
    
### CYSystemInfo.h
    #define IOS7_OR_LATER	
    #define IOS6_OR_LATER	
    #define IOS5_OR_LATER	
    #define IOS4_OR_LATER
    #define IOS3_OR_LATER
    #define IS_IPHONE
    #define IS_IPAD
    
    + (NSString *)osVersion;
    + (NSString *)appVersion;
    
    + (NSString *)deviceModel;
    
    + (BOOL)isJailBroken;
    + (NSString *)jailBreaker;
    
### CYSingletonHelper.h
    #define AS_SINGLETON( __class )
    #define DEF_SINGLETON( __class )

### CYRuntimeHelper.h
    + (void)printCallStackWithCount:(NSUInteger)count;
    
## Contact Me
* [Follow my github](https://github.com/lancy)
* [Write an issue](https://github.com/lancy/CYHelper/issues)
* Send Email to me: lancy1014@gmail.com

## Special Thanks to
I refer to the following code. Thank them sparked my inspiration. Thank them for their contributions to the open source community.

* [ReactiveCocoa](https://github.com/ReactiveCocoa/ReactiveCocoa)
* [BlocksKit](https://github.com/pandamonia/BlocksKit) 
* [BeeFramework](https://github.com/gavinkwoe/BeeFramework)
* [REUIKitAdditions](https://github.com/romaonthego/REUIKitAdditions)
* [iOS 6 Advanced Cookbook](https://github.com/erica/iOS-6-Advanced-Cookbook)

## License

CYHelper is available under the WTFPL license.

Copyright © 2012-2014 Lancy.
