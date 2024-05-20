# Bypassing SSL Pinning in a Flutter Android Application

## Introduction

SSL pinning is a security mechanism used to enhance the security of mobile applications by ensuring that only specific SSL certificates are accepted during the SSL handshake process.

But, in certain scenarios, like during security testing or debugging, it may be necessary to bypass SSL pinning to intercept and analyze application traffic. This report provides a step-by-step guide on how to bypass SSL pinning in a Flutter Android application using the Reflutter framework and Burp Suite. This framework helps with Flutter apps reverse engineering using the patched version of the Flutter library which is already compiled and ready for app repacking. This library has snapshot deserialization process modified to allow you perform dynamic analysis in a convenient way.

### Supported engines

- Android: arm64, arm32;
- iOS: arm64;
- Release: Stable, Beta

### Install

```
# Linux, Windows, MacOS
pip3 install reflutter
```

### Usage

```console
impact@f:~$ reflutter main.apk

Please enter your Burp Suite IP: <input_ip>

SnapshotHash: 8ee4ef7a67df9845fba331734198a953
The resulting apk file: ./release.RE.apk
Please sign the apk file

Configure Burp Suite proxy server to listen on *:8083
Proxy Tab -> Options -> Proxy Listeners -> Edit -> Binding Tab

Then enable invisible proxying in Request Handling Tab
Support Invisible Proxying -> true

impact@f:~$ reflutter main.ipa
```

### Traffic interception

You need to specify the IP of your Burp Suite Proxy Server located in the same network where the device with the flutter application is. Next, you should configure the Proxy in `BurpSuite -> Listener Proxy -> Options tab`

- Add port: `8083`
- Bind to address: `All interfaces`
- Request handling: Support invisible proxying = `True`
<p align="center"><img src="https://user-images.githubusercontent.com/87244850/135753172-20489ef9-0759-432f-b2fa-220607e896b8.png" width="84%"/></p>
