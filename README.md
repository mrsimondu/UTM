#  UTM

> It is possible to invent a single machine which can be used to compute any computable sequence.

-- <cite>Alan Turing, 1936</cite>

UTM is a full featured virtual machine host for iOS. In short, it allows you to run Windows, Android, and more on your iPhone and iPad.

## Features

* 30+ processors supported including x86_64, ARM64, and RISC-V thanks to qemu as a backend
* Fast native graphics through para-virtualization thanks to SPICE
* JIT based acceleration using qemu TCG
* Frontend designed from scratch for iOS11+ using the latest and greatest APIs
* Create, manage, run VMs directly from your device
* No jailbreak required!

## Building

1. Install Xcode command line and the following build prerequisites
    `brew install bison pkg-config gettext glib libgpg-error`
   Make sure to add `bison` to your `$PATH` environment!
2. `git submodule update --init --recursive` if you haven't already
3. Run `./scripts/build_dependencies.sh` and wait for everything to build
4. Open `UTM.xcodeproj` and select your signing certificate
5. Build and deploy from Xcode

### Building for Simulator

Run `./scripts/build_dependencies.sh -a x86_64` to build the libraries for iOS Simulator.

### Running on iOS 13.3.1+

Since iOS 13.3.1, it [appears Apple has stopped allowing free developer profiles to sign dylibs](https://github.com/flutter/flutter/issues/49504#issuecomment-581090664). As a workaround, you can either spend $99/year on an Apple developer program or < $10/year on some third party iOS signing certificate (you can search for it online, do not ask for help with this).

## Why isn't this in the AppStore?

Apple does not permit any apps that has interpreted or generated code therefore it is unlikely that UTM will ever be allowed. However, there are various ways people on the internet have come up to side load apps without requiring a jailbreak. We do not condone or support any of these methods.

## License

UTM is distributed under the permissive Apache 2.0 license. However, it uses several (L)GPL components. Most are dynamically linked but the gstreamer plugins are statically linked and parts of the code are taken from qemu. Please be aware of this if you intend on redistributing this application.