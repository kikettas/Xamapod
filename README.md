# Xamapod
A tool to generate all the binding files needed in a **Xamarin** binding library
from a **Cocoapods** library. The generated binding files are both the **fat libraries** and
**definitions files** (_ApiDefinitions.cs_ and _Structs.cs/StructAndEnums.cs_) used later by the Binding library.

## 🔗 Works with

- **Swift** libraries ✅
- **ObjectiveC** libraries ✅
- Pods with dependencies ✅
- Pods from external sources ✅


## 📋 Requirements

- Xcode Command Line tools (can be downloaded in Xcode or from [here](https://developer.apple.com/downloads/index.action))
- [Cocoapods](https://guides.cocoapods.org/using/getting-started.html)
- [ObjectiveSharpie](https://dl.xamarin.com/objective-sharpie/ObjectiveSharpie.pkg)

## 🛠 Installation

Simply clone this repository.

## 🚀 Building a binding library from a pod

To start using the tool, go to the repo folder and run this command:

```sh
sh build -p YOUR_POD_NAME
```

Optionally, you can specify both **`-s`** (**subspecs**, separated by commas) and `-l` (**links to external sources**, separated by commas) option.

> Since **Swift** libraries are not officialy supported by Xamarin, the process of
bulding these binding files for Swift Pods is slightly different. First, you have
to mark all the _classes/structs/enums_ that you want to expose
to the binding library with the **`@objc`** attribute. After doing so, you can start using the tool.

### ObjectiveC pod

Once it finishes, you will get this output:

```sh
▸ Installing Pods... ✅
▸ Building libraries... ✅
▸ Creating fat libraries... ✅
▸ Creating binding files... ✅

 SUCCESSFULLY COMPLETED 🚀
```

### Swift pod

The output is similar but during the build, besides creating the binding files, these are normalized (thanks to [SwiftClassify](https://github.com/Flash3001/SwiftClassify))
by using the correct names. Finally all the Swift libraries required by the binding library are listed.


```sh
▸ Installing Pods... ✅
▸ Building libraries... ✅
▸ Creating fat libraries... ✅
▸ Creating binding files... ✅
▸ Normalizing binding files... ✅

▸ Add these Swift libraries to your Xamarin App with NuGet:

AVFoundation
 Core
 CoreAudio
 CoreFoundation
 CoreGraphics
 CoreImage
 CoreLocation
 CoreMedia
 Darwin
 Dispatch
 Foundation
 Metal
 ObjectiveC
 Photos
 QuartzCore
 UIKit
 os
 simd

SUCCESSFULLY COMPLETED 🚀
```

When the building process finishes, all the generated binding files are available in the **Generated** folder.
