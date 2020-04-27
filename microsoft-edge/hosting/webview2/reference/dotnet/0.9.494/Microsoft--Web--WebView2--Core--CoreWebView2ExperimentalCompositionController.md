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

# class Microsoft::Web::WebView2::Core::CoreWebView2ExperimentalCompositionController 

> [!NOTE]
> This an experimental API that is shipped with our prerelease SDK version 0.9.494.

This class is an extension of the CoreWebView2Controller class to support visual hosting.

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[UIAProvider](#uiaprovider) | Returns the UI Automation Provider for the WebView.
[RootVisualTarget](#rootvisualtarget) | The RootVisualTarget is a visual in the hosting app's visual tree.
[Cursor](#cursor) | The current cursor that WebView thinks it should be.
[CursorChanged](#cursorchanged) | The event fires when WebView thinks the cursor should be changed.
[SendMouseInput](#sendmouseinput) | If eventKind is CoreWebView2MouseEventKind.HorizontalWheel or CoreWebView2MouseEventKind.Wheel, then mouseData specifies the amount of wheel movement.
[CreateCoreWebView2PointerInfoFromPointerId](#createcorewebview2pointerinfofrompointerid) | A helper function to convert a pointerId received from the system into a CoreWebView2ExperimentalPointerInfo.
[SendPointerInput](#sendpointerinput) | SendPointerInput accepts touch or pen pointer input of types defined in CoreWebView2PointerEventKind.

## Members

### Properties

#### UIAProvider 

Returns the UI Automation Provider for the WebView.

> {property} object [UIAProvider](#uiaprovider)

#### RootVisualTarget 

The RootVisualTarget is a visual in the hosting app's visual tree.

> {property} object [RootVisualTarget](#rootvisualtarget)

This visual is where the WebView will connect its visual tree. The app uses this visual to position the WebView within the app. The app still needs to use the Bounds property to size the WebView. The RootVisualTarget property can be an IDCompositionVisual or a Windows::UI::Composition::ContainerVisual. WebView will connect its visual tree to the provided visual before returning from the property setter. The app needs to commit on its device setting the RootVisualTarget property. The RootVisualTarget property supports being set to nullptr to disconnect the WebView from the app's visual tree.

#### Cursor 

The current cursor that WebView thinks it should be.

> {property} IntPtr [Cursor](#cursor)

The cursor should be set in WM_SETCURSOR through Mouse.SetCursor or set on the corresponding parent/ancestor HWND of the WebView through ::SetClassLongPtr. The HCURSOR can be freed so CopyCursor/DestroyCursor is recommended to keep your own copy if you are doing more than immediately setting the cursor.

#### CursorChanged 

The event fires when WebView thinks the cursor should be changed.

> {property} EventHandler< object > [CursorChanged](#cursorchanged)

For example, when the mouse cursor is currently the default cursor but is then moved over text, it may try to change to the IBeam cursor.

### Methods

#### SendMouseInput 

If eventKind is CoreWebView2MouseEventKind.HorizontalWheel or CoreWebView2MouseEventKind.Wheel, then mouseData specifies the amount of wheel movement.

> public inline void [SendMouseInput](#sendmouseinput)(CoreWebView2MouseEventKind eventKind,CoreWebView2MouseEventVirtualKeys virtualKeys,uint mouseData,Point point)

A positive value indicates that the wheel was rotated forward, away from the user; a negative value indicates that the wheel was rotated backward, toward the user. One wheel click is defined as WHEEL_DELTA, which is 120. If eventKind is CoreWebView2MouseEventKind.XButtonDoubleClickCoreWebView2MouseEventKind.XButtonDown, or CoreWebView2MouseEventKind.XButtonUp, then mouseData specifies which X buttons were pressed or released. This value should be 1 if the first X button is pressed/released and 2 if the second X button is pressed/released. If eventKind is CoreWebView2MouseEventKind.Leave, then virtualKeys, mouseData, and point should all be zero. If eventKind is any other value, then mouseData should be zero. Point is expected to be in the client coordinate space of the WebView. To track mouse events that start in the WebView and can potentially move outside of the WebView and host application, calling SetCapture and ReleaseCapture is recommended. To dismiss hover popups, it is also recommended to send WM_MOUSELEAVE messages.

#### CreateCoreWebView2PointerInfoFromPointerId 

A helper function to convert a pointerId received from the system into a CoreWebView2ExperimentalPointerInfo.

> public inline CoreWebView2ExperimentalPointerInfo [CreateCoreWebView2PointerInfoFromPointerId](#createcorewebview2pointerinfofrompointerid)(uint PointerId,IntPtr ParentWindow,Matrix4x4 transform)

parentWindow is the HWND that contains the webview. This can be any HWND in the hwnd tree that contains the webview. The CoreWebView2Matrix4x4 is the transform from that HWND to the webview. The returned CoreWebView2ExperimentalPointerInfo is used in SendPointerInfo. The pointer type must be either pen or touch or the function will fail.

#### SendPointerInput 

SendPointerInput accepts touch or pen pointer input of types defined in CoreWebView2PointerEventKind.

> public inline void [SendPointerInput](#sendpointerinput)(CoreWebView2PointerEventKind eventType,CoreWebView2ExperimentalPointerInfo pointerInfo)

Any pointer input from the system must be converted into a CoreWebView2ExperimentalPointerInfo first.
