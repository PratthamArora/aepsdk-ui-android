---
title: Adobe Experience Platform SDK push templates
description: Learn about the push templates provided and supported by the Adobe Campaign Classic Mobile SDK extension.
keywords:
- Adobe Campaign Classic
- Push
- Push Template
- Push Templates
---

# Push templates setup - Android

This document outlines the steps required to configure your app to use default push templates provided by Adobe.

<InlineAlert variant="info" slots="text"/>

Default push template functionality is available for use with the **Adobe Campaign Classic** extension. <br /><br />This is supported by **Android SDK version 3.1.0+**.

## Setup

### Prerequisite

Add the Campaign Classic extension dependency to your app's gradle file:

```groovy
dependencies {
  implementation("com.adobe.marketing.mobile:campaignclassic:3.1.+")
}
```

### Implementation

In your application, call `AEPMessagingService.handleRemoteMessage` from `onMessageReceived` in the class implementing `FirebaseMessagingService`.

Below is an example of where to call the API:

```java
public class MyFirebaseMessagingService extends FirebaseMessagingService {
    @Override
    public void onMessageReceived(RemoteMessage remoteMessage) {
        if (AEPMessagingService.handleRemoteMessage(this, remoteMessage)) {
            // Campaign extension has handled the notification
        } else {
            // Handle notification from other sources
        }
    }
}
```
