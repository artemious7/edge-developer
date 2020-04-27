---
description: Host web content in your Win32 app with the Microsoft Edge WebView2 control
title: Microsoft Edge WebView2 for Win32 apps
author: MSEdgeTeam
ms.author: msedgedevrel
ms.date: 12/09/2019
ms.topic: reference
ms.prod: microsoft-edge
ms.technology: webview
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge
---

# interface IWebView2NavigationCompletedEventArgs 

> [!NOTE]
> This interface may be altered or unavailable for releases after SDK version 0.8.355. Please refer to [WebView2 API Reference](../../../webview2-api-reference.md) for the latest API reference.

```
interface IWebView2NavigationCompletedEventArgs
  : public IUnknown
```

Event args for the NavigationCompleted event.

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[get_IsSuccess](#get_issuccess) | True when the navigation is successful.
[get_WebErrorStatus](#get_weberrorstatus) | The error code if the navigation failed.

## Members

#### get_IsSuccess 

True when the navigation is successful.

> public HRESULT [get_IsSuccess](#get_issuccess)(BOOL * isSuccess)

This is false for a navigation that ended up in an error page (failures due to no network, DNS lookup failure, HTTP server responds with 4xx), but could also be false for additional things such as window.stop() called on navigated page.

#### get_WebErrorStatus 

The error code if the navigation failed.

> public HRESULT [get_WebErrorStatus](#get_weberrorstatus)(WEBVIEW2_WEB_ERROR_STATUS * WEBVIEW2_WEB_ERROR_STATUS)
