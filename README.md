# HMS Site Kit Codelab

## [](#table-of-contents)Table of Contents

-   [Introduction](#introduction)
-   [Installation](#installation)
-   [Configuration](#configuration)
-   [Supported Environments](#supported-environments)
-   [License](#license)

## [](#introduction)Introduction


HUAWEI Site Kit provides convenient and secure access to various place-related services for users. You can obtain information about places by sending requests to services. HUAWEI Site SDK offers following core capabilities that will enable you to leverage your application so that your user can reach and explore any place around the world.

### [](#what-you-will-create)What You Will Create

In this codelab, you will use the demo project that has been created for you to experience Site Kit APIs. Through the demo project, you will:
  
 - Experience the sample usage of Keyword Search
 - Experience the sample usage of Nearby Place Search
 - Experience the sample usage of Place Detail Search
 - Experience the sample usage of Place Search Suggestion
 - Experience the sample usage of Widget


### [](#what-you-will-learn)What You Will Learn

In this codelab, you will learn how to:

 - Integrating and using abilities of HUAWEI Site SDK
 - Implementing MVP design pattern for reusable and adaptable using of kit capabilities


## [](#installation)Installation

### [](#required-knowledge)Get the Sample Code


Clone the GitHub repository from the command line:
```
$ git clone https://codehub-dg-g.huawei.com/hms---turkey-dtse-branch/team-c9/hmssitekitdemo.git
```
If git is not available on the computer you are using then access to given URL through a WEB Browser and download the project.

**Note:** If you want to run the app, you have to create a project in the AppGallery Connect corresponding to the package name and SHA26. See “[Preparing for the Integration](#_4._Preparing_for)” step for details .

### [](#required-knowledge)Import the Code

Select HmsSitekitDemo directory (File > Open > .../HmsSitekitDemo) from Android Studio and import the project.

**Note:** agconnect-services.json file should be added to project folder as described in “Preparing for the Integration”. Please use your own **API Key** to call kit capabilities.

## [](#supported-environments)Supported Environments

### [](#hardware-requirements)Hardware Requirements


- One PC that runs the Windows OS with installed Android Studio
- A mobile phone running Android 4.4 or later, which is used for debugging the developed app


### [](#software-requirements)Software Requirements

- Java JDK 1.8 or later
- Android API Level 19 or higher
- EMUI 3.0 or later
- HMS Core (APK) 4.0.3.300 or later


## [](#configuration)Configuration

### [](#creating-quick-app)Preparing for the Integration


**Step 1:** Create an app in AppGallery Connect.
**Step 2:** Create an Android Studio project. (You can skip this step if you have already imported and using the sample code).
**Step 3:** Generate a signing certificate.
**Step 4:** Generate a signing certificate fingerprint.
**Step 5:** Configure the signing certificate fingerprint.
**Step 6:** Add the app package name and save the configuration file.
**Step 7:** Configure the Maven repository address and AppGallery Connect gradle plug-in.
**Step 8:** Configure the signature file in Android Studio.

For details, see the [HUAWEI HMS Core Integration Preparation](https://developer.huawei.com/consumer/en/codelab/HMSPreparation/index.html).

**Note:** You need to register as a developer to complete the operations above.


### [](#integrating-hms-push-kit-in-the-quick-app)Integrating the Huawei Site SDK


**Step 1:** Verify whether site sdk dependency has been added. If not, add it as following to the **dependencies** section in the app level **build.gradle** file:


```
dependencies {
... 
	implementation 'com.huawei.hms:site:5.0.1.300'
... 
}
```


**Step 2:** Configure the **minSdkVersion** in the app level **build.gradle** file.


```
android {
  ...  
  defaultConfig {
	  ...  
	  minSdkVersion 19
	  ...  
	} 
	... 
  }
```


**Step 3:** Check if AGC plugin is applied. If not enable the AGC plug-in in the app level **build.gradle** file.


```
apply plugin: 'com.huawei.agconnect'
```

## [](#license)License

```
 Site Kit Codelab is licensed under the [Apache License, version 2.0](http://www.apache.org/licenses/LICENSE-2.0).
```
