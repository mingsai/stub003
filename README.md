# helloworld

A new Flutter project that works on Linux Debian 9/Chromebook (HP x360 14, 8GB RAM, 64GB SSD).

## Getting Started

This project is a starting point for a Flutter application. I am testing that a Linux build is possible.

In flutter enable the linux desktop support, then create your own project, and make the mods noted below.

Ensure that you latest version of gcc, clang++, and make installed using apt-get. You may have to link the clang-x++ and clang-x file to corresponding commands clang and clang++.

- Modify the Makefile with the application name. Verify that the main.cc file is in place within the linux folder.

Required modifications to the main.dart include an appropriate test for the correct platform and the required imports as follows:

    import 'package:flutter/foundation.dart' show debugDefaultTargetPlatformOverride;
    import 'dart:io' show Platform;
    import 'package:flutter/material.dart';

    //TargetPlatform debugDefaultTargetPlatformOverride = TargetPlatform.fuchsia;
    
    void main(){
        _setTargetPlatformForDesktop();
        runApp(MyApp());
    }  
    void _setTargetPlatformForDesktop() {
        // No need to handle macOS, as it has now been added to TargetPlatform.
        if (Platform.isLinux || Platform.isWindows) {
            debugDefaultTargetPlatformOverride = TargetPlatform.fuchsia;
        }
    }