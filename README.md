# helloworld

A new Flutter project that works on Linux Debian 9/Chromebook (HP x360 14, 8GB RAM, 64GB SSD).

## Getting Started

This project is a starting point for a Flutter application. I am testing that a Linux build is possible.

A few resources to get you started if this is your first Flutter project:

-To be successful, modify the Makefile with the application name. Verify that the main.cc file is in place within the linux folder.

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