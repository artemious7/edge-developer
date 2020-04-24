---
description: Host web content in your Win32 app with the Microsoft Edge WebView2 control
title: Microsoft Edge WebView2 for Win32 apps
author: MSEdgeTeam
ms.author: msedgedevrel
ms.date: 04/22/2020
ms.topic: reference
ms.prod: microsoft-edge
ms.technology: webview
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html
---

# class Microsoft::Web::WebView2::Core::CoreWebView2Deferral 

This class is used to complete deferrals on event args that support getting deferrals via their GetDeferral method.

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[CoreWebView2Deferral](#corewebview2deferral) | Initializes a new instance of the CoreWebView2Deferral class.
[Complete](#complete) | Completes the associated deferred event.

## Members

#### CoreWebView2Deferral 

Initializes a new instance of the CoreWebView2Deferral class.

> public inline  [CoreWebView2Deferral](#corewebview2deferral)(Microsoft.Web.WebView2.Core.Raw.ICoreWebView2Deferral rawCoreWebView2Deferral)

#### Complete 

Completes the associated deferred event.

> public inline void [Complete](#complete)()

Complete should only be called once for each deferral taken.
