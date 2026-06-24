# What We Should Know?
Android mobile app can be written by Kotlin, Java, C++. Android SDK tool will compile your code, combined with any resource into APK(.apk) / Android App Bundle(.aab). 

- APK uses to install android-power devices.
- AAB refers to archive file. 

Some important components of Android files in this doc. 
https://developer.android.com/guide/components/fundamentals

Here is Android community, in case you need help. 
https://developer.android.com/community


We usually use **Android Studio IDE** to develop our android mobile. Because it provides environment of emulator of mobile application.

---
*You can also connect to a physical Android device, turns it into developer debug mode, to connect to Android Studio emulator*


No matter where you release your Android App. The ready-release APK file must being signed with your certificate (zipalign tool).

## Digital Signature
The concept of signature is only to make sure the application customers downloaded is come from one particular entity. (e.g. Making sure your IG app is from META)

The first principle is the author holds the `Private Key`, the also the public holds the `Public Key`. When application published, it will being encrypted by author's private key. However, each person why public key can open it and see what's inside? Therefore, each encryption only responsible with `one-time decrypted`. Hacker can NOT decrypt the files, and sent it to someone, because the public key will NOT match. 

---
*Customers / Google need to make sure this APP is published by your company originally, no anyone else*
---

In the process of signing, `apksigner` by SDK will use the built-bytecode to create a hash, this hash is the current state of source code. The `keytool` by JDK will generate private key, encrypted with your source code, stored in your local `.keystore` file, THIS IS the signature. 

For public key, which is derived from private key by hashing, embedded it in APK itself as self-signed certificate. THIS IS the certificate.

Therefore the signed APK is combined with `signature + certificate` 

The device will decrypt stored signature by using public key inside, if the decrypted value matches the hash, then it works. 

![images](/images/09.png)

## SHA-256
It's a secure Hash algorithm 256-bit. It turns your current stage of each files and resources, into a **64 hexadecimal characters**. 

When you built your apk, you need to built with your signature, which is the keystore you created, it generates the public certificate for **APP identification and API access**.


## Build variants
`Build Variant` is a tool in android studio. It means different version of application you can build. 

It is defined in `/app/build.gradle.kt`, which is a setting feature of how you want to build your app. 

There are 2 types: `Product flavor` & `Build type`.

e.g. 
- The flavor (**dev/staging/prod**) chooses which server the app talks to. 
- The build type (**debug/release**) chooses how the code is packaged

It's basically saying `Do you want salt & pepper OR soy sauce?` But your main dish is still fish balls. 

![images](/images/10.jpg)

## Mobile OS
A piece of software manage small hardware. 

The difference between desktop OS and mobile OS, also due to the difference of its hardware. For example, the desktop has larger battery. 

Two major mobile OS is *Android and IOS*

## Goal of android architecture?
- Architecture must be consistent. No fail.
- Divide the jobs into layers. Easy to fix bug and debug.
- Stay open for architecture choice. Some structure might be better for one situation.
- Simplicity over complicity.

However, IOS might has similar architectural requirement as well. 

## Android Studio Scope Selector?
In android studio, there are multiple scope selector, "Project, Android, Project File, ..etc" 

They all refer to the same folder, but showing a different lens/view to developer for specific jobs. 

If you need to code on kotlin, better using Android View. If you need to check the file structure, better using Project View. 

## What's three parts in macro-layer of Android?
1. `presentation/` — anything the user sees or touches (Activities, Fragments, Dialogs, ViewModels)
2. `domain/` — pure business logic, no Android imports, no network code (use cases, agent orchestration rules)
3. `data/` — how data is fetched and stored (HTTP clients, databases, API definitions, parsers)

it's Google recommend app architecture

- `data/`-- How to get the data?

- `domain/`-- How to deal with those data?

- `presentation/`-- How we present to user?

In most examples, in kotlin + Java section,
UI Layer           →    presentation/
Domain Layer       →    domain/
Data Layer         →    data/

The core of Android App dev, only 3 things
1. shows stuff to user (UI part)
2. Decides what to do with input (Business Rules)
3. Get/saves data (network, database, files)

## What's MVVM?
Google itself recommends *MVVM (Model-View-ViewModel)* as the official android architecture. It's the standard pattern for organizing user view (The '/presentation' layer)

![image](../images/00.png)

- `model`, where is your data?
- `view`, what shows to user?
- `viewmodel`, combined both and show to user

`ViewModel` is like a middleman, transfer data between `model` and `view`. 

The files
1. The View (IndexFragment.kt), pure display which is connectes to the XML layout, display when data in and out. 
2. The ViewModel(IndexViewModel.kt), the bridge between you presenting UI, and backend database
3. The State (AssetUiState.kt),defining the boundaries and rules of screen

## The API Quality


access token(JWT), which is only holding 3 parts:
- Identity
- Role/permissions
- Time Limits

To calculate the latency of user application. There are 3 layer. 
- First is connection between user terminal device and user's connected router. 
- Second is the connections between cloud application and cache handler (spring boot + redis)
- Third is connection between cloud application to external API provider. 

## Http connection
Http request

Http methods

Http content-type

accessToken
It's short-live access password. 
Each login, it will generate new access token. 

middleware regulates whether this request needs token. 

refreshToekn

tokenType

epiresIn

