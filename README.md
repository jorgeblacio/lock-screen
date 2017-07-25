# Lock Screen

Simple and beautiful Lock Screen library to set an check pin code. Integrated with fingerprint authentication.

Easily secure your app with Lock Screen library as easy as starting an intent. 

![Screenshots](https://github.com/amirarcane/lock-screen/demo/blob/master/set.mp4)

![Screenshots](https://github.com/amirarcane/lock-screen/demo/blob/master/check.mp4) 

Lock Screen gets a 4 digit pincode from user at first running time. Then every time that you start Lock Screen intent, it 
 checks if thw 

Watching this repository will allow GitHub to email you whenever I publish a release.

---
# Gradle Dependency

Add this line to your `build.gradle` project

```java
compile 'com.amirarcane.lock-screen:lockscreen:1.0.0'
```
---
# Usage

Just add these lines to your class, that's it.

```java
RecentImages recentImages = new RecentImages();
ImageAdapter adapter = recentImages.getAdapter(MainActivity.this);
```
`recentImages.getAdapter()` method returns an adapter that you can easily set it as your gridView adapter. By default it returns device pictures based on `Date_Taken` and `Descending` order, for changing them see [Customization](https://github.com/amirarcane/recent-images/#customization)

Use `recentImages.cleanupCache()` to clean the cache.
It removes all the callbacks from the drawables stored in the memory cache.
This method must be called from the onDestroy() method of any activity using the cached drawables.
Failure to do so will result in the entire activity being leaked.

You can use regular gridView but if you want to use it exactly like above picture you need horizontal gridView.
I used jess-anders/two-way-gridView in this library. All you have to do is set below code in your xml instead of regular gridView:

```xml

<com.jess.ui.TwoWayGridView
    android:id="@+id/gridView"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:background="#E8E8E8"
    app:columnWidth="70dp"
    app:rowHeight="70dp"
    app:numColumns="auto_fit"
    app:numRows="auto_fit"
    app:verticalSpacing="16dp"
    app:horizontalSpacing="16dp"
    app:gravity="center"/>

```
---
# Customization

RecentImages class contains some methods for customization:

`getAdapter(Context context)` default method to get adapter

`getAdapter(Context context, String columns, String sort)` parameter columns filters device images base on date, name, id and etc. parameter sort will sort them based on `Desecnding` or `Ascending` order

`setDrawable(int drawable)` to use an image from you drawable folder before loading of images

`setHeight(int height)` to set images height (in dp)

`setWidth(int width)` to set images width (in dp)

`setPadding(int padding)` to set images padding (in dp)

`setSize(int size)` to set quality of thumbnail images (values are 1, 2, 3, 4. 1 means best quality and high resolution and 4 means least quality an low resolution)

Here is an example:

```java
RecentImages recentImages = new RecentImages();
ri.setHeight(70);
ri.setWidth(70);
ImageAdapter adapter = recentImages.getAdapter(MainActivity.this, ri.LATITUDE, ri.ASCENDING);
gridView.setAdapter(adapter);
```

---