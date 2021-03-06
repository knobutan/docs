---

copyright:
  years: 2016
lastupdated: "2016-11-22"

---
{:new_window: target="_blank"}

# End-to-end tutorial of the Basic Code Starter
{: #tutorial}

The following end-to-end tutorial walks through the steps to create a project from the Basic Code Starter, including the tools that you must have installed, and subsequently, the steps to run the starter in Xcode and Android Studio.


### Installing developer tools
{: #dev_tools}

Ensure that you have installed the [prerequisite developer tools](get_code.html#prereq-dev-tools){: new_window}.


### Creating a project from the Basic Code Starter
{: #create_project}

1. Create a Mobile dashboard project in {{site.data.keyword.Bluemix}}.

   1. From the **Getting Started** page in the Mobile dashboard, click **Create Project**.

      You can alternatively click **Create Project** from the **Projects** page.

   2. Click **Code Starters**.

   3. Select **Basic** and click **Create Project**.

   4. Enter your project name. For this tutorial, use `BasicProject`.
   
   5. Click **Create**.

2. Optional: Add the Push Notifications capability.

   1. Click **Add** for **Push Notifications** in the **Project Overview** page.

      You can alternatively click **Create** from the **Push Notifications** page.

   2. Enter your service name and click **Create**.

   3. For iOS, [configure Apple Push Notification Service](/docs/services/mobilepush/t_push_provider_ios.html){: new_window}.

   4. For Android, [configure Firebase Cloud Messaging](/docs/services/mobilepush/t_push_provider_android.html){: new_window}.
   
3. Optional: Add the Analytics capability.

   1. Click **Add** for **Analytics** in the **Project Overview** page.

      You can alternatively click **Create** from the **Analytics** page.

   2. Enter your service name and click **Create**.
   
   3. Toggle off **Demo Mode** to see your analytics data after you run your app.
   
   4. See [Getting started with {{site.data.keyword.mobileanalytics_short}}](/docs/services/mobileanalytics/index.html){: new_window} for more information about configuring Analytics.
  
4. Optional: Add the Authentication capability.

   1. Click **Add** for **Authentication** on the **Project Overview** page.

      You can alternatively select **Create** on the **Authentication** page.

   2. Enter your service name and click **Create**.
   
   3. Toggle on **Authentication**.
   
   4. Select your identity provider and enter the required information to configure it. You can enable only one identity provider.

   5. See [Getting started with {{site.data.keyword.amashort}}](/docs/services/mobileaccess/index.html){: new_window} for more information about configuring Authentication.

5. Generate your project code.

   1. Click **Get Code** on the **Project Overview** page to select your platform and language.
   
      You can alternatively click on the **Code** page.
      
   2. For Objective-C, click **iOS Obj-C**.

   3. For Swift, click **iOS Swift**.
   
   4. For Cordova, click **Cordova**.

   5. For Android, click **Android**.
   
   6. When the project code is finished generating, click **Download Code** to download your project archive.


### Running your Objective-C project in Xcode
{: #run_obj-c}

1. Extract the `BasicProject-ObjC.zip` file.

2. Open the `README.md` file in a Markdown viewer to review the steps to configure your project.

   1. Open your Terminal and navigate to your project folder.
   
      1. Run `pod setup` if you need to set up your CocoaPods repository.
      
      2. Run `pod update` if you need to update you update your existing pods.
      
      3. Run `pod install` to install the pods that are required for your project.
      
   2. Open your `BasicProject.xcworkspace` Xcode workspace.
      
3. Run your app.


### Running your Swift project in Xcode
{: #run_swift}

1. Extract the `BasicProject-Swift.zip` file.

2. Open the `README.md` file in a Markdown viewer to review the steps to configure your project.

   1. Open your Terminal and navigate to your project folder.
   
      1. Run `pod setup` if you need to set up your CocoaPods repository.
      
      2. Run `pod update` if you need to update you update your existing pods.
      
      3. Run `pod install` to install the pods that are required for your project.
      
   3. Open your `BasicProject.xcworkspace` Xcode workspace.
      
3. Run your app.


### Running your Cordova project in Xcode
{: #run_cordova_xcode}

1. Extract the `BasicProject-Cordova.zip` file.

2. Open the `README.md` file in a Markdown viewer to configure your project.

   1. Open your `platforms/ios` project in Xcode.
      
3. Run your app.


### Running your Cordova project in Android Studio
{: #run_cordova_studio}

1. Extract the `BasicProject-Cordova.zip` file.

2. Open the `README.md` file in a Markdown viewer to configure your project.

   1. Open your `platforms/android` project in Android Studio.
      
3. Run your app.


### Running your Android project in Android Studio
{: #run_android}

1. Extract the `BasicProject-Android.zip` file.

2. Open the `README.md` file in a Markdown viewer to configure your project.

   1. Open your `BasicProject-Android` project in Android Studio.
      
3. Run your app.


## What to do next
{: #what_next}

View other tutorials.


### UI Starter tutorials
{: #tutorials_UI}

* [Tutorial - Store Catalog](tutorial_store_catalog.html)


### Code Starter tutorials
{: #tutorials_Code}

* [Tutorial - {{site.data.keyword.visualrecognitionshort}}](tutorial_visual_recognition.html)
* [Tutorial - Watson Language](tutorial_watson_language.html)
* [Tutorial - Weather](tutorial_weather.html)
