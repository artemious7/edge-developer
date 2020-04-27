---
description: Host web content in your Win32 app with the Microsoft Edge WebView2 control
title: Microsoft Edge WebView2 for Win32 apps
author: MSEdgeTeam
ms.author: msedgedevrel
ms.date: 04/27/2020
ms.topic: reference
ms.prod: microsoft-edge
ms.technology: webview
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html
---

# class Microsoft::Web::WebView2::Core::CoreWebView2NewWindowRequestedEventArgs 

Event args for the NewWindowRequested event.

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[uri](#uri) | The target uri of the NewWindowRequest.
[NewWindow](#newwindow) | Gets the new window.
[Handled](#handled) | Whether the NewWindowRequestedEvent is handled by host.
[IsUserInitiated](#isuserinitiated) | IsUserInitiated is true when the new window request was initiated through a user gesture such as clicking an anchor tag with target.
[GetDeferral](#getdeferral) | Obtain a CoreWebView2Deferral object and put the event into a deferred state.

The event is fired when content inside webview requested to a open a new window (through window.open() and so on.)

## Members

### Properties

#### uri 

The target uri of the NewWindowRequest.

> {property} string [uri](#uri)

The target webview should not be navigated. If the NewWindow is set, its top level window will return as the opened WindowProxy.

#### NewWindow 

Gets the new window.

> {property} CoreWebView2 [NewWindow](#newwindow)

#### Handled 

Whether the NewWindowRequestedEvent is handled by host.

> {property} bool [Handled](#handled)

If this is false and no NewWindow is set, the WebView will open a popup window and it will be returned as opened WindowProxy. If set to true and no NewWindow is set for a window.open call, the opened WindowProxy will be for an dummy window object and no window will load. Default is false.

#### IsUserInitiated 

IsUserInitiated is true when the new window request was initiated through a user gesture such as clicking an anchor tag with target.

> {property} bool [IsUserInitiated](#isuserinitiated)

### Methods

#### GetDeferral 

Obtain a CoreWebView2Deferral object and put the event into a deferred state.

> public inline CoreWebView2Deferral [GetDeferral](#getdeferral)()

You can use the CoreWebView2Deferral object to complete the window open request at a later time. While this event is deferred the opener window will be returned a WindowProxy to an unnavigated window, which will navigate when the deferral is complete.
