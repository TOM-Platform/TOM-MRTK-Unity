# Client for TOM-Platform

This is an experimental branch from MRTK source code XRI3 branch of MixedRealityToolkit-Unity.

A Unity implementation of the client to support smart glasses and phones that receive data from the server
- This [Unity3D](https://unity.com/) client serves as the primary front-end interface for devices such as smart glasses and phones. 
- Users directly interact with this interface. 
- It's constructed using [MRTK 3](https://github.com/MixedRealityToolkit/MixedRealityToolkit-Unity/tree/feature/XRI3) -- specifically XRI3 branch for its compatibility with Meta Quest devices and switch between hands, controller interaction modes correctly
- It employs web socket communication to connect with the [TOM-Server-Python](../TOM-Server-Python).


## Requirements

- Unity3D v2022.3.43f1, or newer versions.
      - (Older versions of v2022.3 are not yet tested for compatibility)
- Meta XR Core SDK v71 as documented in [Quest Integration](./README_QuestIntegration.md)
  - https://developers.meta.com/horizon/downloads/package/meta-xr-core-sdk
  - Select `Download from Meta`
  - Copy the file to 
    - ```ExternalDependencies\MetaXRSDK\com.meta.xr.sdk.core-71.0.0.tgz```

## Installation
- Open the project in Unity
- The TOM starter projects are located in `Assets/Scenes/TOM/`
- Follow the platform-specific instructions below


#### For Meta Quest (Quest 3, Quest Pro, Quest 3S)
- Ensure that `Android Build Support` has been already added during Unity3D installation.  
- For development -- both Mac or Windows can be used. 
- **For deployment -- 
  - **Windows** might be preferred, 
  - as **MacOS** build has some quirks in controller display / interaction in the generated APK.
- For configuration of IP to server, pls edit details in `UnityProjects/MRTKDevTemplate/Assets/Scripts/TOM/Config/ConfigData.cs`
  - Note: `ConfigData.cs` is ignored in `UnityProjects/.gitignore`

- Set your build setting to the Android Platform: 
  - Go to `File > Build Settings`.
  - Select **Android** and click **Switch Platform**.
- Building the APK
  - Click on Build in `File > Build Settings`.
  - Select an output target (eg. create Builds folder in UnityProject/MRTKDevTemplate/Builds/TOMTemplate.apk) *Builds/Build folder name are ignored in .gitignore.
- Building and running on Meta Quest
  - Connect a USB-C / link cable to the Meta Quest 
  - Authorize the connection from Meta Quest headset if you have not done so. 
  - Refresh the devices list, and the Quest device should appear and select it. 
  - Click on `Build and Run` to build, deploy and run the APK on the device.

- (Optional) Advanced Options for Debugging / Wifi
  - Android Studio can be used to connect the Meta Quest, to view logcat logs about the application.
  - Wifi (via ADB)
    - When the device is connected via cable,
    - Follow the guide at [Using ADB with Meta Quest](https://developers.meta.com/horizon/documentation/native/android/ts-adb/#connect-adb-via-wi-fi) to setup wifi mode


---

# Mixed Reality Toolkit for Unity

![Mixed Reality Toolkit](./Images/MRTK_Unity_header.png)

![MRTK3 Banner](./Images/MRTK3_banner.png)

**MRTK3** is the third generation of the Mixed Reality Toolkit for Unity. It's an open source project designed to accelerate cross-platform mixed reality development in Unity. MRTK3 is built on top of [Unity's XR Interaction Toolkit (XRI)](https://docs.unity3d.com/Packages/com.unity.xr.interaction.toolkit@2.1/manual/index.html) and OpenXR. This new generation of MRTK is intended to be faster, cleaner, and more modular, with an easier cross-platform development workflow enabled by OpenXR and the Unity Input System.

## Key improvements

### Architecture

* Built on Unity XR Interaction Toolkit and the Unity Input System.
* Dedicated to OpenXR, with flexibility for other XRSDK backends
* Open-ended and extensible interaction paradigms across devices, platforms, and applications

### Performance

* Rewrote and redesigned most features and systems, from UX to input to subsystems.
* Zero per-frame memory allocation.
* Tuned for maximum performance on HoloLens 2 and other resource-constrained mobile platforms.

### UI

* New interaction models (gaze-pinch indirect manipulation).
* Updated Mixed Reality Design Language.
* Unity Canvas + 3D UX: production-grade dynamic auto-layout.
* Unified 2D & 3D input for gamepad, mouse, and accessibility support.
* Data binding for branding, theming, dynamic data, and complex lists.

## Requirements

MRTK3 requires Unity 2021.3.21 or higher. In addition, you need the [Mixed Reality Feature Tool for Unity](https://aka.ms/mrfeaturetool) to find, download, and add the packages to your project.

## Getting started

[Follow the documentation for setting up MRTK3 packages as dependencies in your project here.](https://learn.microsoft.com/windows/mixed-reality/mrtk-unity/mrtk3-overview/getting-started/setting-up/setup-new-project) Alternatively, you can clone this repo directly to experiment with our template project. However, we *strongly* recommend adding MRTK3 packages as dependencies through the Feature Tool, as it makes updating, managing, and consuming MRTK3 packages far easier and less error-prone.

## Supported devices

| Platform | Supported Devices |
|---|---|
| OpenXR devices | Microsoft HoloLens 2 <br> Magic Leap 2 <br> Meta Quest 1/2 <br> Windows Mixed Reality (experimental) <br> SteamVR (experimental) <br> Oculus Rift on OpenXR (experimental) <br> Varjo XR-3 (experimental) <br> **If your OpenXR device already works with MRTK3, let us know!**
| Windows | Traditional flat-screen desktop (experimental)
| And more coming soon! |

## Versioning

In previous versions of MRTK (HoloToolkit and MRTK v2), all packages were released as a complete set, marked with the same version number (ex: 2.8.0). Starting with MRTK3 GA, each package will be individually versioned, following the [Semantic Versioning 2.0.0 specification](https://semver.org/spec/v2.0.0.html). (As a result, the '3' in MRTK3 is not a version number!)


Individual versioning will enable faster servicing while providing improved developer understanding of the magnitude of changes and reducing the number of packages needing to be updated to acquire the desired fix(es).

For example, if a non-breaking new feature is added to the UX core package, which contains the logic for user interface behavior the minor version number will increase (from 3.0.x to 3.1.0). Since the change is non-breaking, the UX components package, which depends upon UX core, is not required to be updated. 

As a result of this change, there is not a unified MRTK3 product version.

To help identify specific packages and their versions, MRTK3 provides an about dialog that lists the relevant packages included in the project. To access this dialog, select `Mixed Reality` > `MRTK3` > `About MRTK` from the Unity Editor menu.

![About MRTK Panel](Images/AboutMRTK.png)

## Early preview packages

Some parts of MRTK3 are at earlier stages of the development process than others. Early preview packages can be identified in the Mixed Reality Feature Tool and Unity Package Manager by the `Early Preview` designation in their names.

As of June 2022, the following components are considered to be in early preview.

| Name | Package Name |
| --- | --- |
| Accessibility | org.mixedrealitytoolkit.accessibility |
| Data Binding and Theming | org.mixedrealitytoolkit.data |

The MRTK team is fully committed to releasing this functionality. It is important to note that the packages may not contain the complete feature set that is planned to be released or they may undergo major, breaking architectural changes before release.

We very much encourage you to provide any and all feedback to help shape the final form of these early preview features.

## Contributing

This project welcomes contributions, suggestions, and feedback. All contributions, suggestions, and feedback you submitted are accepted under the [Project's license](./LICENSE.md). You represent that if you do not own copyright in the code that you have the authority to submit it under the [Project's license](./LICENSE.md). All feedback, suggestions, or contributions are not confidential.

For more information on how to contribute Mixed Reality Toolkit for Unity Project, please read [CONTRIBUTING.md](./CONTRIBUTING.md).

## MRTK3 XRI2 to XRI3 migration guide

MRTK3 has been upgraded to use [Unity's XR Interaction Toolkit 3+](https://docs.unity3d.com/Packages/com.unity.xr.interaction.toolkit@3.0/manual/whats-new-3.0.html).  As part of the upgrade several changes were made to properly consume XRI 3 package and adhere to the new patterns.  In a nutshell, the main changes are summarized as follows:

* New controller prefabs and a new rig have been created following the new XRI3 pattern.
  * The old controllers and rig have been marked as osbolete and renamed as "Obsolete MRTK XR Rig", "Obsolete MRTK LeftHand Controller", "Obsolete MRTK RightHand Controller", "Obsolete MRTK Hand Controller", "Obsolete MRTK Interaction Manager", and "Obsolete MRTK Gaze Controller".
  * The new controllers and rig retake the original names of the obsolete controllers.
* New controllers structure have been modified so that all of them have the same structure.
* The deprecated XRI2 XRController component has been removed from the controllers and its input actions have been moved to their interactors.
    * The new controllers now have a Tracked Pose Driver components that holds references to the device's position, rotation, and tracking state input actions.
* Interactors now have a Tracked Pose Driver field that holds a reference to the Tracked Pose Driver component of the parent controller.
* Interactors now have a Mode Managed Root that holds a reference to the parent controller GameObject.
* Added new unity-tests for the new XRI3 functionality + components.
* Updated several unity-tests.
* Updated several scripts so that they work with both obsolete XRI2 and new XRI3 prefabs.
* Updated all scenes to use the new XRI3 rig + controllers.
    * Made a copy of the old HandInteractionExamples scene and renamed as ObsoleteHandInteractionExample, this scene still consumes the old rig + controllers.

A more detailed explanation of the changes can be found in [XRI2TOXRI3MIGRATIONGUIDE.md](./XRI2TOXRI3MIGRATIONGUIDE.md).  The guide can also help others as a path for migrating their own solutions or MRTK3 forks from XRI2 to XRI3.

## Governance

For information on how the Mixed Reality Toolkit for Unity Project is governed, please read [GOVERNANCE.md](./GOVERNANCE.md).

All projects under the Mixed Reality Toolkit organization are governed by the Steering Committee. The Steering Committee is responsible for all technical oversight, project approval and oversight, policy oversight, and trademark management for the Organization. To learn more about the Steering Committee, visit this link: https://github.com/MixedRealityToolkit/MixedRealityToolkit-MVG/blob/main/org-docs/CHARTER.md
