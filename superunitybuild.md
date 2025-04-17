## Overview

[SuperUnityBuild](https://github.com/superunitybuild) is a free and open source automation tool for quickly and easily generating builds with Unity, It is simple to use and very extendable. This document describes a basic setup to get you started. At the end of this article you will be able to perform the following actions with a single button press:

Build for Windows, Mac and Linux (building for other platforms is also supported)
Upload to itch.io using Butler (meaning only changed files will be pushed to itch)
Zip each build and move to your backup drive

## Installing SuperUnityBuild

SuperUnityBuild is available from OpenUPM which is, in my opinion, the most convenient way of installing. We will also install the optional BuildActions package as this brings some features we want (like Itch.io uploading). Follow these steps:

1. Open `Edit -> Project Settings -> Package Manager`
2. Enter the following details into the `Scoped Registries` section:
  1. Name package.openupm.com
  2. URLhttps://package.openupm.com
  3. Scope(s) com.github.superunitybuild.buildtool
3. Click the `+` below the scopes box to add another scope
4. Enter `com.github.superunitybuild.buildactions` as the second scope
5. Click `Save` - saving will take a few moments
6. Close the `Project Settings` window
7. Open `Window -> Package Manager`
8. Click `+` in the top left
9. Select `Add Package by Name`
10. Enter `com.github.superunitybuild.buildtool` as the name
11. Click `Add`- the package will be installed
12. Repeat from step 8) but using `com.github.superunitybuild.buildactions` as the package name

## Setting SuperUnityBuild up for Windows Build

1. `Windows -> SuperUnityBuild`
2. Click `Release Types`
3. Click the `Add Release Type` button
4. Expand the `New Release Type` section
5. Set a `Type Name` such as "Release"
6. Click `SceneList` and add/order the scenes you want in the build
7. Click `Build Platforms`
8. Select `PC` in the platforms dropdown
9. Click `Add Platform`
10. Expand the newly added `PC (Windows x86, App)` section
11. [Optional] Deselect `x86` and select `x64`
12. Click the big green `Perform All Enabled Builds` button

You're now building with SuperUnityBuild! After a short time the build will be complete and explorer will open up at the root of your builds folder. 
You can configure the path to the build in `Basic Settings`. You can also configure the version number in `Product Parameters`.

## Setting SuperUnityBuild up for Mac and Linux Builds

Adding new platforms is super easy. As long as you have the required modules installed in your Unity installation simply add the required platforms to your `Build Platforms`:

1. Click `Build Platforms`
2. Select `macOS` or `Linux` in the platforms dropdown
3. Click `Add Platform`
4. Expand the newly added `macOS (Intelx64, App)` or `` section
5. [Optional for macOS] Select `Universal` in the architecture dropdown
6. Click the big green `Perform All Enabled Builds` button

You are now building for all your chosen platforms with a single button press!

If any of your platforms are not built it is most commonly because you have not installed the build modules for that platform.  To resolve this follow these steps:

1. Open the Hub.
2. Select Installs.
3. Find the Editor you want to add the components to.
4. Click the three dots to the right of the version label, then select Add Modules.
5. In the Add Modules dialog, locate the module to add and tick its checkbox.
6. When you have selected all the modules to add, select Done.

## Zip and Backup Releases

It is a good idea to backup all releases. In this section we use the ZipFileOperation build action to zip the contents of the build and place them somewhere like a networked backup storage.

1. Click `Post-Build Actions` to expand that section
2. Select `ZipFileoperations` in the dropdown
3. Click `Add Build Action` button
4. Change `Output Path` to you backup location, e.g. `D:\Releases Backups`
5. Change the `Output File Name` to something like "$PRODUCT_NAME-$PLATFORM-$ARCHITECTURE-$VERSION-$YEAR_$MONTH_$DAY.zip"
6. Click the big green `Perform All Enabled Builds` button
7. A new build will be created and a zip of that build will be placed in your chosen output path.

## Automatically Publishing Releases to Itch.io

Now the most exciting part, using [Butler](https://itch.io/docs/butler/) to publish your release to Itch.io. This section assumes you already have itch.io setup for your game and that Butler is installed.

1. Click `Post-Build Actions` to expand that section
2. Select `UploadItch` in the dropdown
3. Click `Add Build Action` button
4. Set the path to Butler
5. Set you itch user name
6. Set the name of your game on itch (this is the name as it appears in the URL of the game)
7. Tick to use the generated build version number
8. Click `Add Filter`
9. Setup a filter for `Release Type` `Equals` "Release" (or whatever you named it above)
10. Click the big green `Perform All Enabled Builds` button

And now you are publishing to Itch.io. The first time your entire game will be uploaded but in subsequent builds only changed or new content will be uploaded.

## Notes

When building IL2CPP projects you should add a FolderOperation action before the UploadItch action. Set it to Delete and for the Input path put in:

`$BASEPATH/$VERSION/$RELEASE_TYPE/$PLATFORM/$ARCHITECTURE/$SCRIPTING_BACKEND/$PRODUCT_NAME_BackUpThisFolder_ButDontShipItWithYourGame`

This folder is in IL2CPP builds and should never be shipped with your game. You might prefer to move this folder rather than delete it and it contains "generated C++ for debugging".
