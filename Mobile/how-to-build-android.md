[← Back to README](../README.md)

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
*Customers / Google need to make sure this APP is published by the one who HOLDS private key originally, and it has NOT being modified*
---

In the process of signing, `apksigner` by SDK will use the built-bytecode to create a hash, this hash is the current state of source code. The `keytool` by JDK will generate private key, encrypted with your source code, stored in your local `.keystore` file, THIS IS the signature. 

For public key, which is derived from private key by hashing, embedded it in APK itself as self-signed certificate. THIS IS the certificate.

Therefore the signed APK is combined with `signature + certificate` 

The device will decrypt stored signature by using public key inside, if the decrypted value matches the hash, then it works. 

![images](/images/09.png)

If the hash is not matched, then the installation would simply fail outright with **verification error**.

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

It's basically saying `Do you want salt & pepper OR soy sauce on your FISH BALLS?` But your main dish is still fish balls. 

![images](/images/10.jpg)


## Mobile OS
A piece of software manage small hardware. 

The difference between desktop OS and mobile OS, also due to the difference of its hardware. For example, the desktop has larger battery. 

Two major mobile OS is *Android and IOS*

Even some of Chinese mobile maker, like XIAOMI and HUAWEI, MIUI/HyperOS is also Android underneath. 

## Goal of android architecture?
- Architecture must be consistent. No fail.
- Divide the jobs into layers. Easy to fix bug and debug.
- Stay open for architecture choice. Some structure might be better for one situation.
- Simplicity over complicity.

However, IOS might has similar architectural requirement as well. 

## Architecture by Google
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

## Mobile <-> BackEnd
The SIZE. If you download an mobile app for 200mb, it only means how much code and bundles ships to your mobile (client-side). 

The download package only need to contain all the bundles that client need to use. 

The connection between both entities mostly is RESTful api connection. JSON Web Token, which's the **entire software industry standard** to securely transfer info as a JSON object.
- Header 
- Payload
- Signature

https://www.geeksforgeeks.org/web-tech/json-web-token-jwt/

How JWT works (client - server)

e.g. BackEnd is Spring Boot
1. When user login password is verified, Spring BOot will generate a JWT,and sent it back to user mobile. 
2. Once the APP save it, for every request to protected API route, it will carry JWT as header. 
3. Server side will extract token, and verify its cryptographic signature. 

*BUT the JWT will expire right?*

SO there will be a **Refresh Token Rotation**, when client-side detect the HTTP error code (401 unauthorized) form server-side, then it will generate new auth-token. 




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

## 32 or 64?
It's the configuration of mobile CPU. It means the cpu can only take 32 bit of data in one single operation. 

Because machine code is only constructed by 1 and 0, it need to operate by CPU, but it can only guess what kind of cpu that user use. 

Since Kotlin code will be compiled into bytecode in advance, stored in `classes.dex`, set of instruction user's phone can understand. It's not neither 32 or 64

It's like a English Menu, you can sent it to each restaurant for them to make it. BUT the facility of each restaurant is different. 

---
*You can analysis your APK on Android Studio after you built, if there's no `lib` file, that's totally fine with this problem*


## How to publish an APP?
If you have a signed apk/abb file with a developer account on Google Play Store, that's already enough for publish an APP. 

If for Chinese mobile maker, the job is ALL about business registration. (Like xiaonmi and huawei)


## MObile storage allocation
On server side, redis lives in RAM. It's not the permanent storage like mySQL. 

On client side, the storage setting on mobile is to save the data after the APP is being killed. 

# j
On WeChat server side

local keystore file -- 32-character hash -- 微信公众平台's signature 

your app package name + signature = appID

put the appID inside your application through the format of WeChat Pay SDK 

WeChat only need to know whether it is the real app is calling or fake app is calling, since the appID is public. 

Application makes the call -- WeChat check appID -- WeChat check the bundled merchant id -- put the payment money from user account to merchant account.



The payment request is being sent by the app's server side (spring boot)

request
- merchant id
- appID
- outer trade number (out_trade_no) (each payment carries a unique key)
- amount (8 usd)

All signed with merchant private key, and sent to WeChat pay API through HTTPS

WeChat Pay check, then authorized, returns prepay_id. (The request has approved, now start to pay)

server do the signing again, then back to mobile application

the installed WeChat SDK, which has installed in your application, call the 微信 on user's phone

微信 check the sign again, and od the match on 'signature' and 'fingerprint'

After both check, money move from user's wallet to merchant wallet. 

# things

you need
- merchant id (business license, public account)
- app id (package name + local keystore)

WeChat need to make sure the app user's paying for is from your company

when spring boot send order, you need
- merchant private key

WeChat need to confirm the request is from your spring boot (Your App's server), it is not protecting the connection, the connection is protecting by HTTPS/SSL, the key only sign and confirm the order is from our APP

when user mobile receive prepay_id, then after paid the order, you need
- V3 key

WeChat encrypt the payment result, it does the callback (HTTP POST) to your spring boot, you use v3 key decrypt the hidden content

