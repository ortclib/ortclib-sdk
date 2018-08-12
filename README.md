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

Requirements:

- Visual Studio 2017
- The C++/WinRT Visual Studio extension must be installed - https://marketplace.visualstudio.com/items?itemName=CppWinRTTeam.cppwinrt101804264
- Windows 10 SDK, version 1803 (10.0.17134.0) - https://developer.microsoft.com/en-us/windows/downloads/sdk-archive
  More info here: https://blogs.msdn.microsoft.com/chuckw/2018/05/02/windows-10-april-2018-update-sdk/
- "Debugging Tools for Windows" feature from the Windows 10 SDK must be installed.

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

2) From VS2017, load ortc\windows\solutions\Ortc.sln for Ortc or webrtc\windows\solutions\WebRtc.sln for WebRtc development.

3) Now you can build winuwp libraries for Ortc or WebRtc and deploy sample apps ChatterBox (WebRtc only) and PeerCC.

====
