﻿# Working with calls in Microsoft Graph

> **Important:** APIs under the /beta version in Microsoft Graph are in preview and are subject to change. Use of these APIs in production applications is not supported.

The Calling APIs enables you to create calls and receive calls from users in Skype and Microsoft Teams. Here are list of calling scenarios supported by these APIs.

- Ad-Hoc two party calling
- Ad-Hoc multi party calling
- Meet Now
- Calling into Private meetings
- Calling into Microsoft Teams meetings
- IVR Scenarios

Before you get started with trying out the Calling API, it is worth understanding your media processing requirements.

## MediaPaaS

Media processing is managed through Microsoft Media Platform (MediaPaaS). MediaPaaS helps Bots engage in Skype/Teams audio/video calls and conferences.  It allows real-time bots to participate in both 1:1 and group/multiparty calls​.
- Direct (**application media**) media bot calls: developers can build real-time bots using the SmartAgents API and have access to direct media I/O​. Also known as the [Bots Media Library](https://docs.microsoft.com/en-us/bot-framework/dotnet/bot-builder-dotnet-real-time-media-concepts), it helps you build rich real-time media calling bots.  Developers host the smart agents library and media processor.
- Remote media (**service media**) bot calls: developers can manage the workflow but offload media hosting to MediaPaaS/IVR​.

## SDK
Calling APIs may be used directly by the **service media** bot.  In these cases, the Bot is usually _Stateless_ and does not process media locally.

[Graph Calling SDK](https://graphcallingsdk-docs.azurewebsites.net/index.html) is provided to simplify the creation of bots. The SDK provides functionality to manage the states of the resources in memory and to pull in bot developers' media stack. The Media Extension allows the bot developers to host the media locally and gain access to the low level audio-video sockets.

# Registering a Calling Bot

> **Important:** APIs for Calling in Microsoft Graph are in preview and are subject to change. Use of these APIs in production applications is not supported.

In this topic, learn how to register a new Calling Bot.

## Register your bot in the Azure Bot Service

Complete the following steps:
1. Register a bot through [Azure Bot Channel Registration](https://docs.microsoft.com/en-us/azure/bot-service/bot-service-quickstart-registration).
1. Once you complete the registration, take a note of the registered config values (Bot Name, Application Id and Application Secret).  You will need these values later in the code samples.
1. Enable the Skype channel and configure the Calling tab settings to enable calling.  Fill in the Webhook (for calling) where you will receive incoming notifications. E.g. `https://{your domain}/api/calls`. Refer to [Connect a bot to channels](https://docs.microsoft.com/en-us/azure/bot-service/bot-service-manage-channels) for more information on how to configure channels.
1. Enable the Microsoft Teams channel.

## Permissions

### Add Microsoft Graph Permissions for Calling to your Bot

Microsoft Graph exposes granular permissions that control the access that apps have to resources. As a developer, you decide which permissions for Microsoft Graph your app requests.  The Microsoft Graph Calling APIs support Application permissions, which are used by apps that run without a signed-in user present; for example, apps that run as background services or bots.  Application permissions can only be consented by an administrator.  Calling bots and applications have some capabilties that will need permission consent.  Below is a list of those permissions:

|Permission|Display String|Description|Admin Consent Required|
|---| ------------- |---|--|
|Calls.Initiate.All|Initiate outgoing 1:1 calls from the app (preview)|Allows the app to place outbound calls to a single user and transfer calls to users in your organization’s directory, without a signed-in user.|Yes|
|Calls.InitiateGroupCall.All|Initiate outgoing group calls from the app (preview)|Allows the app to place outbound calls to multiple users and add participants to meetings in your organization, without a signed-in user.|Yes|
|Calls.JoinGroupCall.All|Join Group Calls and Meetings as an app (preview)|Allows the app to join group calls and scheduled meetings in your organization, without a signed-in user.  The app will be joined with the privileges of a directory user to meetings in your tenant.|Yes|
|Calls.JoinGroupCallasGuest.All|Join Group Calls and Meetings as a guest (preview)|Allows the app to anonymously join group calls and scheduled meetings in your organization, without a signed-in user.  The app will be joined as a guest to meetings in your tenant.|Yes|
|Calls.AccessMedia.All ^^see note^^|Access media streams in a call as an app (preview)|Allows the app to get direct access to participant media streams in a call, without a signed-in user.|Yes|

> **Note:** You may not use the Microsoft.Graph.Calls.Media API to record or otherwise persist media content from calls or meetings that your bot accesses.

### Assigning Permissions

You pre-configure the application permissions your app needs when you register your app.  To add Permissions from the Azure Bot Registration Portal, do the following:

* From the **Settings** blade, click **Manage**. This is the link appearing by the **Microsoft App ID**. This link will open a window where you can scroll down to add Microsoft Graph Permissions: under **Microsoft Graph**, choose **Add** next to **Application Permissions** and then select the permissions your app requires in the **Select Permissions** dialog. <br/>
  ![Manage link in Settings blade](./images/registration-settings-manage-link.png)

  You can also add permissions by accessing your app through the [Microsoft App Registration Portal](https://apps.dev.microsoft.com/).

### Getting Administrator Consent

An administrator can either consent to these permissions using the [Azure portal](https://portal.azure.com) when your app is installed in their organization, or you can provide a sign-up experience in your app through which administrators can consent to the permissions you configured. Once administrator consent is recorded by Azure AD, your app can request tokens without having to request consent again.

You can rely on an administrator to grant the permissions your app needs at the [Azure portal](https://portal.azure.com); however, often, a better option is to provide a sign-up experience for administrators by using the Azure AD v2.0 `/adminconsent` endpoint.  Please refer to the [instructions on constructing an Admin Consent URL](https://developer.microsoft.com/en-us/graph/docs/concepts/auth_v2_service#3-get-administrator-consent) for more detail.

> **Note**: Constructing the Tenant Admin Consent URL requires a configured Redirect URI/Reply URL in the [App Registration Portal](https://apps.dev.microsoft.com/). To add reply URLs for your bot, access your bot registration, choose Advanced Options > Edit Application Manifest.  Add your Redirect URI to the field replyURLs.

> **Important**: Any time you make a change to the configured permissions, you must also repeat the Admin Consent process. Changes made in the app registration portal will not be reflected until consent has been reapplied by the tenant's administrator.

# Calls
[Application](./application.md) is used for creating a new call by posting to the calls collection.
[Call](./call.md) provides APIs to manage a call.

# Samples

Samples are hosted in [VSTS](https://sampleapps-microsoftteams.visualstudio.com/_git/CVIBot) and you can get started by reading the [README](https://sampleapps-microsoftteams.visualstudio.com/_git/CVIBot?path=%2FLocalMediaSampleBot%2FREADME.md&version=GBmaster) file.