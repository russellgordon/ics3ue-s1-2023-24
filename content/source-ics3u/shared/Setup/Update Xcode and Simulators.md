---
draft: false
draftSectionTwo: false
enableToc: true
excludeBacklinks: true
created: 2024-01-09T00:00:00.000-0400
---
In some situations, when previewing applications or using the Simulator, Xcode 15.0 would use more computing resources than expected, leading to high CPU usage and excessive battery drain on laptop computers.

Xcode 15.2 and the updated iOS 17.2 simulator runtime reportedly fix this issue; anecdotally Mr. Gordon has observed this to be true.

## Update Xcode using Xcodes

Launch the [[Xcodes]] app on your computer.

Recall that Xcodes is an application that helps you manage the installation  of *Xcode*, which is the programming environment we use.

Install Xcode 15.2 – depending on how much disk space you have on your computer, you may keep old versions of Xcode around if you wish:

![[Screenshot 2024-01-08 at 7.26.02 PM.png]]

> [!IMPORTANT]
> Be sure that Xcode 15.2 is the "active" version of Xcode on your computer. You should see the green checkmark noted above in the screenshot.

Open Xcode 15.2 – check that you launched the correct version:

![[Screenshot 2024-01-08 at 7.31.19 PM.png|451]]

## Remove old simulators

Follow the menu sequence **Xcode > Settings...** and then select the **Platforms** tab:

![[Screenshot 2024-01-08 at 7.33.11 PM.png|501]]

As needed, remove old simulators and ensure that you have the iOS 17.2 simulator installed.

## Remove derived data

When building projects, Xcode creates caches that make later project builds faster.

To ensure that projects you work with will not encounter the high CPU usage bug, we will clear the caches created by earlier versions of Xcode.

Follow the menu sequence **Xcode > Settings...** and then select the **Platforms** tab:

![[Screenshot 2024-01-08 at 7.52.38 PM.png]]

Click the small arrow next the the filesystem path for the **Derived Data** folder.

This will open the **Finder** to that folder – you can then delete it by moving it to the trash:

![[Screenshot 2024-01-08 at 7.54.22 PM.png]]

Xcode will create the folder again the next time a project is built.