# What Is macOS?

---

Many have and use an Apple product in their lives every day. From your Macbook to your iPhone or iPad, there are many different revisions to the Apple OS line, but most of them are, in fact, based on macOS (originally Mac OS X). So let's answer the question, "What is macOS?"

Let's start this module by breaking down the history of macOS, its use, architecture, and core components. `macOS` is the official term for the operating system used on Apple computers. It is a widely used OS and is `second` in market use only to Windows operating systems. It can be found in the realms of daily home use, business management, graphical design, and arts.

---

## History Roundup

Let's take a look at the origins of macOS for a minute.

#### Timeline

## 2000-2002

This is known as the original start to OS X leading up to macOS as we know it. In the fall of 2000, Apple released a public beta code named `Kodiak` for users to test and provide feedback. After taking in those responses and making fixes, Apple released Mac OS X (10.0), named `Cheetah`, in the spring of 2001. This is the first time the world will see the new User interface Aqua. ![](https://academy.hackthebox.com/storage/modules/157/macosx_cheetah.png)  
A few months later, Apple released OS X (10.1) named `Puma`. This iteration drastically improved system performance and began officially replacing Mac OS 9, OS X's predecessor, on all new computers shipped out.![](https://academy.hackthebox.com/storage/modules/157/macosx_puma.png)  
In the Fall of 2002, the next iteration of OS X was released. OS X (10.2), named `Jaguar`, focused on user interaction improvements and introduced new applications like iChat to the world.![](https://academy.hackthebox.com/storage/modules/157/macosx_jaguar.png)

## 2003

OS X (10.3) named `Panther` was released in the fall of 2003. Most interesting about this release was the fact that Apple's new web browser `Safari` replaced Internet Explorer on their hosts. Support for integration with `Active Directory` was also added during this release. ![](https://academy.hackthebox.com/storage/modules/157/macosx_panther.png)

## 2005

OS X (10.4) named `Tiger` released, bringing with it new features and new looks with Widgets and dashboards. Up to this point, only PowerPC processors were supported for Apple products. With this release, Apple hit a milestone by officially releasing support for the `Intel` based chipset in their hosts. ![](https://academy.hackthebox.com/storage/modules/157/macosx_tiger.png)

## 2007-2009

2007 was a big year for Apple. In the spring, they unveiled their new gadget that changed the world, the `iPhone` and with it iOS, which was completely based on Mac OS X. That same year in the fall, OS X (10.5) `Leopard` was released and introduced Apple's built-in backup system, Time Machine, along with support for 64-bit applications. At this point, dual-booting was first introduced to the Mac line with the introduction of Boot Camp, providing support for the Windows OS on Mac hardware. ![](https://academy.hackthebox.com/storage/modules/157/macosx_leopard.png)  
Following Leopard in 2009, OS X (10.6) `Snow Leopard` released, which was an incremental update over Leopard. The only real changes were the addition of the AppStore and the discontinuation of support for the PowerPC processors. From this point on, Apple moved to Intel based processors exclusively. ![](https://academy.hackthebox.com/storage/modules/157/macosx_snow_leopard.png)

## 2011-2012

OS X (10.7) `Lion` brought many successful features from iOS to their Mac OS X, like Gestures and saved window states. Lion also saw the introduction of `iCloud` to Mac OS X, bringing interconnected cloud storage to the Apple realm of products. ![](https://academy.hackthebox.com/storage/modules/157/macosx_lion.jpg)  
2012 brought us `Mountain Lion` (10.8), with the main focus on bringing many of the features that were currently iOS-only into Mac OS X. ![](https://academy.hackthebox.com/storage/modules/157/macosx_mountain_lion.jpg)

## 2013

From this point forward, Apple decided to stick to a yearly release cycle of Mac OS X. After over a decade of releases named after big wild cats, Apple also decided to ditch the animal theme and move to a naming convention based off locations and landmarks within `California.`. With a fresh new naming standard, OS X (10.9) `Mavericks`, kicks off the new release schedule and Apple put out a statement that all future releases would be `free for upgrade` (including this one). There were some functionality tweaks but nothing substantial under the hood. ![](https://academy.hackthebox.com/storage/modules/157/macosx_mavericks.jpg)

## 2014-2015

With the release of OS X (10.10) `Yosemite`, the Handoff functionality brought exciting change to the Apple product lines allowing users to seamlessly move any task users are working on from one Apple device to another. The UI is moving more toward the iOS look and feel. ![](https://academy.hackthebox.com/storage/modules/157/macosx_yosemite.jpg)  
OS X (10.11) `El Capitan` brought more performance changes and the ability to tile your screen with split views. ![](https://academy.hackthebox.com/storage/modules/157/macosx_el_capitan.jpg)

## 2016-2017

OS X is dead! Long live `macOS`. With the release of macOS (10.12) named `Sierra`, Apple officially moved away from the "OS X" moniker to "macOS". Along with this change, Apple brought integration for Siri, Apply Pay, and other tweaks under the hood to macOS. ![](https://academy.hackthebox.com/storage/modules/157/macosx_sierra.jpg)  
macOS (10.13) `High Sierra` brought along the switch to the `Apple File System (APFS)` and several other support functionalities under the hood. ![](https://academy.hackthebox.com/storage/modules/157/macosx_high_sierra.jpg)

## 2018

macOS (10.14) `Mojave` brought significant visual enhancements with this update. `Darkmode` was introduced to the platform, working natively with all macOS apps and many third-party ones. The ability to have your host dynamically shift from dark mode to light mode with the time of day was also a big change. Mojave also ported over several more iOS apps to macOS, like News, Stocks, and Home, to name a few. ![](https://academy.hackthebox.com/storage/modules/157/macosx_mojave.jpg)

## 2019

macOS (10.15) `Catalina` split iTunes into three separate apps (Apple TV, Podcasts, and Music). This update also focused on bringing more iOS features to macOS and also allowed the use of an iPad as a secondary display with the `Sidecar` feature. ![](https://academy.hackthebox.com/storage/modules/157/macosx_catalina.png)

## 2020

macOS 11 releases, named `Big Sur`, finally moved away from OS version 10 (or X) and brought big changes to the UI and functionality of the OS as a whole. Much care was taken to improve communications channels in this revision as well. The major new feature of macOS 11 was supporting the all-new `Apple Silicon` processor while still supporting Intel processors for at least a few more years. Much of the focus of this revision also went to bug fixes. ![](https://academy.hackthebox.com/storage/modules/157/macosx_big_sur.jpg)

## 2021

macOS 12 `Monterey`. Integration improvements, dubbed `Universal Control`, were introduced that made controlling multiple Apple devices at once much more seamless. AirPlay saw some big changes, and you can now use a Mac as a speaker when casting to other devices. `Spatial Audio` was introduced to Facetime, along with other features like SharePlay which, allow you to share audio, video, and even your screen with other users over FaceTime. ![](https://academy.hackthebox.com/storage/modules/157/macosx_monterey.jpg)

## 2022

macOS 13 `Ventura` is the most recent release of macOS as of the time of writing this module. It introduced a new window management feature called `Stage Manager`, along with other features like `Continuity Camera`, new Apps and app updates, a facelift to the settings app, along with other features. ![](https://academy.hackthebox.com/storage/modules/157/macosx_ventura.jpg)

---

Now that we know a bit about the history of macOS let's dive into the architecture of the OS itself and some of its core components.

---

## OS & Architecture Info

`Kernel`: [XNU](https://github.com/apple/darwin-xnu)

- The Mach kernel is the basis (along with portions from BSD) of the macOS and iOS `XNU` Kernel architecture, which handles our memory, processors, drivers, and other low-level processes.

`OS Base`: [Darwin](https://github.com/apple/darwin-xnu), a FreeBSD Derivative open-sourced by Apple.

- Darwin is the base of the macOS operating system. Apple has released Darwin for open-source use. Darwin, combined with several other components such as `Aqua`, `Finder`, and other `custom components`, make up the macOS as we know it.

As mentioned above, macOS recently shifted to mainly support Apple Silicon while still supporting Intel processors for the time being.

These points above make up the basis of macOS as an operating system. There is much more to it, but we are just trying to get an initial understanding of what macOS is for now. Next, let us address several core components within macOS.

---

## Core Components

`GUI`: [Aqua](https://en.wikipedia.org/wiki/Aqua_(user_interface)#References) is the basis for the Graphical interface and visual theme for macOS. As technology has advanced, so has Aqua, providing more and more support for other displays, rendering technologies, and much more. It is known for its flowy style, animations, and transparency with windows and taskbars.

`File Manager`: [Finder](https://support.apple.com/en-us/HT201732) is the component of macOS that provides the Desktop experience and File management functions within the OS. Aqua is also responsible for the launching of other applications.

`Application Sandbox`: By default, macOS and any apps within it utilize the concept of sandboxing, which restricts the application's access outside of the resources necessary for it to run. This security feature would limit the risk of a vulnerability to the application itself and prevent harm to the macOS system or other files/applications within it.

[Cocoa](https://developer.apple.com/library/archive/documentation/macOSX/Conceptual/OSX_Technology_Overview/CocoaApplicationLayer/CocoaApplicationLayer.html): Cocoa is the application management layer and API used with macOS. It is responsible for the behavior of many built-in applications within macOS. Cocoa is also a development framework made for bringing applications into the Apple ecosystem. Things like notifications, Siri, and more, function because of Cocoa.