---
tags: mobile, kotlin, android
author: truong-dwarvesv
date: 2022-09-26
---

Navigation refers to the interactions that allow users to navigate across, into, and back out from the different pieces of content within your app.

# Navigation overview

The Navigation component consists of three key parts that are described below:

- Navigation graph: An XML resource that contains all navigation-related information in one centralized location. This includes all of the individual content areas within your app, called destinations, as well as the possible paths that a user can take through your app.

- `NavHost`: An empty container that displays destinations from your navigation graph. The Navigation component contains a default `NavHost` implementation, `NavHostFragment`, that displays fragment destinations.

- `NavController`: An object that manages app navigation within a `NavHost`. The `NavController` orchestrates the swapping of destination content in the `NavHost` as users move throughout your app.

# Benefits of using Navigation component

The Navigation component provides a number of other benefits, including the following:

- Handling fragment transactions.
- Handling Up and Back actions correctly by default.
- Providing standardized resources for animations and transitions.
- Implementing and handling deep linking.
- Including Navigation UI patterns, such as navigation drawers and bottom navigation, with minimal additional work.
- [Safe Args](https://developer.android.com/guide/navigation/navigation-pass-data#Safe-args) - a Gradle plugin that provides type safety when navigating and passing data between destinations.
- `ViewModel` support - you can scope a `ViewModel` to a navigation graph to share UI-related data between the graph's destinations.

# How to use

## 1. Setup dependencies
```gradle
dependencies {
    def nav_version = “2.3.2”

    // Java language implementation
    implementation “androidx.navigation:navigation-fragment:$nav_version”
    implementation “androidx.navigation:navigation-ui:$nav_version”

    // Kotlin
    implementation “androidx.navigation:navigation-fragment-ktx:$nav_version”
    implementation “androidx.navigation:navigation-ui-ktx:$nav_version”

    // Feature module Support
    implementation “androidx.navigation:navigation-dynamic-features-fragment:$nav_version”

    // Testing Navigation
    androidTestImplementation “androidx.navigation:navigation-testing:$nav_version”

}
```
## 2. Add a NavHost to an activity

``` XML
<androidx.coordinatorlayout.widget.CoordinatorLayout 
    xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    xmlns:tools="http://schemas.android.com/tools"
    android:id="@+id/container"
    android:layout_width="match_parent"
    android:layout_height="match_parent">

    <fragment
        android:id="@+id/nav_host"
        android:name="androidx.navigation.fragment.NavHostFragment"
        app:navGraph="@navigation/home_nav"
        android:layout_width="match_parent"
        android:layout_height="match_parent"
        app:defaultNavHost="true" />

</androidx.coordinatorlayout.widget.CoordinatorLayout>
```

- This is a layout for an activity. It contains global navigation, including a bottom nav and a toolbar
- `android:name="androidx.navigation.fragment.NavHostFragment" `and `app:defaultNavHost="true"` connect the system back button to the `NavHostFragment`
- `app:navGraph="@navigation/home_nav"` associates the `NavHostFragment` with a navigation graph. This navigation graph specifies all the destinations the user can navigate to, in this `NavHostFragment`

## 3. Create **nav_graph** into res file
- Folder structure: res>navigation>app_navigation.xml

``` XML
<?xml version="1.0" encoding="utf-8"?>
<navigation xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    xmlns:tools="http://schemas.android.com/tools"
    android:id="@+id/home_nav"
    app:startDestination="@+id/homeFragment">

    <fragment
        android:id="@+id/homeFragment"
        android:name="com.df.android.main.view.HomeFragment"
        android:label="HomeFragment"
        tools:layout="@layout/fragment_home">

        <action
            android:id="@+id/action_homeFragment_to_detailFragment"
            app:destination="@+id/detailFragment"
            app:popUpTo="@id/homeFragment"
            app:popUpToInclusive="true"
            app:launchSingleTop="true"
            app:enterAnim="@anim/nav_default_enter_anim"
            app:exitAnim="@anim/nav_default_exit_anim"
            app:popEnterAnim="@anim/nav_default_enter_anim"
            app:popExitAnim="@anim/nav_default_exit_anim"
            />

    </fragment>


    <fragment
        android:id="@+id/detailFragment"
        android:name="com.df.android.main.view.DetailFragment"
        android:label="DetailFragment"
        tools:layout="@layout/fragment_detail" />

</navigation>
```

Here parameters used in `fragment` tag

- **android:id**: unique id for the fragment, just like we are assigning id to any other widgets in XML layout
- **android:name**: It is the fully qualified name of your fragment class
- **android:label**: A string to identify the fragment
- **tools:layout**: An id of layout resource file from res/layout

Let’s discuss the parameters used inside `<action/>`
- **android:id**: unique id for the action, just like we are assigned id to the fragments
- **app:destination**: The unique id of the destination fragment, means this action will move the current view to the destination fragment
- **app:popUpTo**: This is for backward navigation if the app has navigated from a fragment A to fragment B, then fragment B to fragment C. If you want to go fragment A to fragment C you can use this parameter value as the id fragment A. The back stack management and the lifecycle will mange by the Navigation Component.
- **app:popUpToInclusive**: Indicate that the destination specified in app:popUpTo should also be removed from the back stack.
- **app:launchSingleTop**: Whether this navigation action should launch as single-top (i.e., there will be at most one copy of a given destination on the top of the back stack).
- **app:enterAnim**, **app:exitAnim**, **app:popEnterAnim**, **app:popExitAnim**: we can define the animations for the fragment transaction as specified, you must have to create the xml animation file inside res/anim folder.

## 4. Navigation to Destination

### NavigationController

- `NavController` is powerful because when you call methods like `navigate()` method or `popBackStack()` method, it translates these commands into the appropriate framework operations based on the type of destination you are navigating to or from. For example, when you call `navigate()` method with an activity destination, the NavController calls `startActivity()` on your behalf.

- `Fragment.findNavController()`
- `View.findNavController()`
- `Activity.findNavController(viewId: Int)`

### Navigate to a Destination

Navigating is done using a `NavController`, an object that manages app navigation within a NavHost. Each NavHost has its own corresponding `NavController`. You can retrieve a `NavController` by using one of the following methods:

**Kotlin**:
- `Fragment.findNavController()`
- `View.findNavController()`
- `Activity.findNavController(viewId: Int)`

**Java**:
- `NavHostFragment.findNavController(Fragment)`
- `Navigation.findNavController(Activity, @IdRes int viewId)`
- `Navigation.findNavController(View)`

### Ensure type-safety by using Safe Args

The recommended way to navigate between destinations is to use the Safe Args Gradle plugin. It generates simple object & builder classes that allow us to do type-safe navigation and argument passing between destinations.

To learn more about [Safe Args](https://developer.android.com/guide/navigation/navigation-pass-data#Safe-args)


``` Groovy
buildscript {
    repositories {
        google()
    }
    dependencies {
        def nav_version = "2.5.2"
        classpath "androidx.navigation:navigation-safe-args-gradle-plugin:$nav_version"
    }
}
```

To generate Java language code suitable for Java or mixed Java and Kotlin modules, add this line to your app or module's `build.gradle` file:

``` Groovy
// Java
plugins {
  id 'androidx.navigation.safeargs'
}
// Kotlin
plugins {
  id 'androidx.navigation.safeargs.kotlin'
}
```

We can navigate by creating a direction object and pass it over navigation()

``` Kotlin
var amount = "200.0"
var currency = Currency.USDT

val directions: NavDirections = LoginFragmentDirections.actionLoginFragmentToForgotPasswordFragment(amount, currency)

Navigation.findNavController(view).navigate(directions)
```


 ### Custom Backstack Handling

``` XML
<action
    android:id="@+id/action_loginFragment_to_forgotPasswordFragment"
    app:destination="@id/forgotPasswordFragment"
    app:popUpTo="@+id/signinMainFragment"
    app:popUpToInclusive="true"/>
```

- `app:popUpTo`: This is for backward navigation if the app has navigated from a fragment A to fragment B, then fragment B to fragment C. If you want to go fragment A to fragment C you can use this parameter value as the id fragment A. The back stack management and the lifecycle will mange by the Navigation Component.

- `app:popUpToInclusive`: you can pass true/false value based on requirement whether or not want to include fragment for which id is given in `app:popUpTo` attribute.

 ### Animation

``` XML
<fragment
    android:id="@+id/loginFragment"
    android:name="com.android.samples.LoginFragment"
    android:label="fragment_login"
    tools:layout="@layout/fragment_login" >
    <action
        android:id="@+id/action_loginFragment_to_forgotPasswordFragment"
        app:destination="@id/forgotPasswordFragment"
        app:popUpTo="@+id/signinMainFragment"
        app:popUpToInclusive="true"
        app:enterAnim="@anim/slide_in_right"
        app:exitAnim="@anim/slide_out_left"
        app:popEnterAnim="@anim/slide_in_left"
        app:popExitAnim="@anim/slide_out_right"/>
    <action
        android:id="@+id/action_loginFragment_to_tnCFragment"
        app:destination="@id/tnCFragment" />
</fragment>
```

We can define animations by using the below attribute -

- app:enterAnim=”@anim/slide_in_right”
- app:exitAnim=”@anim/slide_out_left”
- app:popEnterAnim=”@anim/slide_in_left”
- app:popExitAnim=”@anim/slide_out_right”

### Nested Graphs

A series of destinations that can be grouped into a nested graph within a parent navigation graph called the root graph. Nested graphs are useful to organize and reuse sections of your app’s UI, such as a self-contained login/profile flow.

We can add nested graph by using `<include>` tag like

``` XML
<include app:graph="@navigation/profile_nav_graph" />
```

The nested graph encapsulates its destinations. Each nested graph must have a destination identified as the start destination. Destinations outside of the nested graph, such as those on the root graph, access the nested graph only through its start destination.

### Updated UI components with NavigationUI

The Navigation component includes a NavigationUI class. This class contains static methods that manage navigation with the top app bar, the navigation drawer, and the bottom navigation. 

### Deeplink

In Android, a deep link is a link that takes you directly to a specific destination within an app.

The Navigation component lets you create two both types of deep links: explicit and implicit.

An implicit deep link refers to a specific destination/screen in an app. When the deep link is invoked, in other words- when a user clicks a link — then our device can open your app to the corresponding destination.

Deep links can be matched by URI, intent actions, or MIME types. You can specify multiple match types for a single deep-link, but note that URI argument matching is prioritized first, followed by action, and then MIME type.

Here’s an example deep link that contains a URI, an action, and a MIME type:

``` XML
<fragment android:id="@+id/a"
          android:name="com.android.samples.DashboardFragment"
          tools:layout="@layout/a">
        <deeplink app:url="www.example.com"
                app:action="android.intent.action.MY_ACTION"
                app:mimeType="type/subtype"/>
</fragment>
```

To enable implicit deep linking, you must also make additions to your app’s manifest.xml file. Add a single `<nav-graph>` element to an activity that points to an existing navigation graph, as shown in the following example:

``` XML
<?xml version="1.0" encoding="utf-8"?>
<manifest xmlns:android="http://schemas.android.com/apk/res/android"
    package="com.android.samples">
    <application ... >
        <activity name=".MainActivity" ...>
            ...
            <nav-graph android:value="@navigation/nav_graph" />
            ...
        </activity>
    </application>
</manifest>
```

When building your project, the Navigation component replaces the `<nav-graph>` element with generated `<intent-filter>` elements to match all of the deep links in the navigation graph.

When an implicit deep link clicked on, the state of the back stack depends on whether the implicit Intent was launched with the Intent.`FLAG_ACTIVITY_NEW_TASK` flag:

- If the flag is set, the task back stack is cleared and replaced with the deep link destination.
- If the flag is not set, you remain on the task stack of the previous app where the implicit deep link was triggered. In this case, the Back button takes you back to the previous app, while the Up button starts your app’s task on the hierarchical parent destination within your navigation graph


### Handling deep links

It is recommended to always use the default `launchMode` (standard) while using navigation component. When we are usingstandard launch mode, navigation automatically handles deep links by calling `handleDeepLink()` method to process explicit or implicit deep links within the Intent. However, this does not happen automatically if we are using an alternate `launchMode` such as `singleTop`. In this case, it is necessary to manually call `handleDeepLink()` in `onNewIntent()`, as shown in the following example:

``` Kotlin
override fun onNewIntent(intent: Intent?) {
    super.onNewIntent(intent)
    navController.handleDeepLink(intent)
}
```

# References

- [Navigation documentation](https://developer.android.com/guide/navigation)
- [Safe Args](https://developer.android.com/guide/navigation/navigation-pass-data#Safe-args)
