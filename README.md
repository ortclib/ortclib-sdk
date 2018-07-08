INSTRUCTIONS
=======

From your terminal, please clone the "ortclib-sdk" git repository:
git clone --recursive https://github.com/ortclib/ortclib-sdk.git

This repository will yield the ORTC Lib SDK and dependency libraries.

Directory structure:

- ortc-lib-sdk\bin          	contains scripts for preparing an environment for Windows
- ortc-lib-sdk\common          contains samples applications that can use Ortc and WebRtc libraries. Currently it is only the case for PeerCC sample 
- ortc-lib-sdk\ortc    		contains code of Ortc and dependency libraries
- ortc-lib-sdk\webrtc    		contains code of WebRtc and dependency libraries
- ortc-lib-sdk\docs			contains documentation


How to Build:

WINDOWS BUILD :
----------------------------

1) Run prepare script, from your terminal:
<br />
<pre>
<code>
cd ortclib-sdk
bin\prepare.bat
</code>
</pre>
<br />
This script will prepare environment but it won't build webrtc projects. In this case webrtc project will be built from Visual Studio once you try to build Org.Ortc or Org.WebRtc.

2) From VS2015, load ortc\windows\solutions\Ortc.sln for Ortc or webrtc\windows\solutions\WebRtc.sln for WebRtc development.

3) Now you can build winuwp libraries for Ortc or WebRtc and deploy sample apps ChatterBox (WebRtc only) and PeerCC.

====

# Unity Video Rendering

There are two ways to render WebRTC video streams in Peer Connection Client sample application using Unity engine:
1. In standard Peer Connection Client XAML application video content can be rendered through Swap Chain Panel component - WebRtcUnityXaml.sln
2. Unity standalone application with full screen 3D display - WebRtcUnityD3D.sln

## Unity build requirements

1. Unity version 2017.4.1 (2017.4.1f1) with Windows Store .NET Scripting Backend

*Remark: If Unty is not installed on default location (C:\Program Files\Unity), edit install path values in property files common\windows\samples\PeerCC\Client\UnityCommon.props and common\windows\samples\PeerCC\ClientUnity\UnityCommon.props.*

## Compile and run

* For XAML based application with Unity rendering component open webrtc\windows\solutions\WebRtcUnityXaml.sln and build PeerConnectionClientUnity.WebRtc
* Unity 3D Peer Connection Client application - build PeerConnectionClientUnity project in webrtc\windows\solutions\WebRtcUnityD3D.sln

## Exporting Visual Studio solution from Unity Editor - PeerCC Unity standalone application only

1. Build soulution WebRtcUnityD3D.sln - this step adds WebRTC binaries to Unity project space
2. Open Unity project common\windows\samples\PeerCC\ClientUnity\Unity\PeerCCUnity in Unity Editor
3. Go to 'File' -> 'Build settings...' -> 'Build' and choose an export folder
4. Add the following XML block to PeerCCUnity\Package.appxmanifest:
```
  <Extensions>
    <Extension Category="windows.activatableClass.inProcessServer">
      <InProcessServer>
        <Path>WebRtcScheme.dll</Path>
        <ActivatableClass ActivatableClassId="WebRtcScheme.SchemeHandler" ThreadingModel="both" />
      </InProcessServer>
    </Extension>
  </Extensions>
```
5. Open PeerCCUnity.sln, build and run project PeerCCUnity
