# Expo

## What is Expo?
- Expo is a framework and a platform for universal React applications. It is a set of tools and services built around React Native and native platforms that help you develop, build, deploy, and quickly iterate on iOS, Android, and web apps from the same JavaScript/TypeScript codebase.
[Documentation](https://docs.expo.io/versions/v35.0.0/get-started/installation/)

## Pros and Cons
- Pros
    - Easy to use
    - Immediate results
    - Everything is covered by Expo
    - Nice documentation from Getting started to all API Docs
    - Live reload while in development
    - Library linking (react-native link) not necessary
    - Test directly on device both for iOS and Android (through the Expo container app)
    - Develop from Windows/MacOS or whatever (you only need nodejs and an internet connection)
 
- Pros 
    - Build is done by Expo, in their cloud
    - Native modules not supported
    - Expo apps don’t support background code execution (source docs.expo.io)
    - Javascript source is hosted in their cloud
    - The app is going to be at least arond 30MB on iOS and at least around 20MB on Android because Expo is including all libraries in the App for now
 
## How to use native modules in Expo
 - Expo dose not support native moudles. To use them such as In App Purchase, you need to eject react-native source from Expo.
[Documentation](https://docs.expo.io/versions/latest/expokit/eject/)
 

 
