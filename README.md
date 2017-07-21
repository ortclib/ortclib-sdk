INSTRUCTIONS
=======

From your terminal, please clone the "ortclib-sdk" git repository (before cloning, please read IMPORTANT NOTES section below):
git clone --recursive https://github.com/ortclib/ortclib-sdk.git

This repository will yield the ORTC Lib SDK and dependency libraries.

Directory structure:

- ortc-lib-sdk\bin          	contains scripts for preparing an environment for Windows
- ortc-lib-sdk\common          contains samples applications that can use Ortc and WebRtc libraries. Currently it is only the case for PeerCC sample 
- ortc-lib-sdk\ortc    		contains code of Ortc and dependency libraries
- ortc-lib-sdk\webrtc    		contains code of WebRtc and dependency libraries
- ortc-lib-sdk\docs			contains documentation

IMPORTANT NOTES:
1)  Ensure that Git is properly configured to handle line endings. Git setting for core.autocrlf needs to be set to true; you can check current setting for core.autocrlf using command: 'git config -l', or 'git config core.autocrlf', and you can change setting to true using 'git config --global core.autocrlf true'. 
    Usefull links: 
	https://help.github.com/articles/dealing-with-line-endings/
	https://git-scm.com/book/en/v2/Customizing-Git-Git-Configuration#__code_core_autocrlf_code (section core.autocrlf)  
2) Visual Studio 2015 is required
3) Latest supported Win 10 SDK is 10.0.14393.x

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

3) Now you can build winrt libraries for Ortc or WebRtc and deploy sample apps ChatterBox (WebRtc only) and PeerCC.

====
