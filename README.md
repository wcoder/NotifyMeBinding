# NotifyMe ![version](https://img.shields.io/badge/original-v1.0.1-brightgreen.svg?style=flat)

<!--[![NuGet Badge](https://buildstats.info/nuget/AndroidAboutPage)](https://www.nuget.org/packages/AndroidAboutPage/)-->

Port of [NotifyMe](https://github.com/jakebonk/NotifyMe) for Xamarin.Android.

---

A Android Library for simple notifications. Very easily set a delay or time when you want the notification to popup. Notification will popup through system reboots.

![Demo](https://thumbs.gfycat.com/DishonestPlushBlacklab-size_restricted.gif)

## Setup

TODO

<!--Grab the latest version from NuGet

> Install-Package AndroidAboutPage-->

## Dependencies

* Xamarin.Android.Support.v4

## Modify AndroidManifest.xml

Permission:

```xml
<uses-permission android:name="android.permission.RECEIVE_BOOT_COMPLETED" />
```

`<application>`:

```xml
    <receiver android:name="com.allyants.notifyme.NotificationPublisher" />
    <receiver android:name="com.allyants.notifyme.BootNotifyMe">
        <intent-filter>
            <action android:name="android.intent.action.BOOT_COMPLETED" />

            <category android:name="android.intent.category.HOME" />
        </intent-filter>
    </receiver>
```

## Example

Create a NotifyMe Builder Object

```cs

var notifyMe = new NotifyMe.Builder(ApplicationContext);

```

Then set the fields you want.

```cs
notifyMe.Title(String title);
notifyMe.Content(String content);
notifyMe.Color(Int red,Int green,Int blue,Int alpha);//Color of notification header
notifyMe.led_color(Int red,Int green,Int blue,Int alpha);//Color of LED when notification pops up
notifyMe.Time(Calendar time);//The time to popup notification
notifyMe.Delay(Int delay);//Delay in ms
notifyMe.large_icon(Int resource);//Icon resource by ID
notifyMe.Rrule("FREQ=MINUTELY;INTERVAL=5;COUNT=2")//RRULE for frequency of notification
notifyMe.AddAction(Intent intent,String text); //The action will call the intent when pressed
```

After all the fields that you want are set just call build()!

```cs
notifyMe.Build();
```

&nbsp;

---

&copy; 2020