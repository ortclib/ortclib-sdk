M62 WebRTC Native and UWP enhancements
=======

This repo contains all the patches and extensions made to WebRTC for the [3D Streaming Toolkit project](https://github.com/CatalystCode/3dtoolkit), enabling building powerful stereoscopic 3D experiences that run on the cloud and stream to devices. Changes include:

#### WebRTC M62 native:

- [NvPipe](https://github.com/anderm/NvPipe/tree/low-latency-optimization) integration in the H264 encoder - zero latency video compression library for interactive remoting applications
- Included ffmpeg for client decoding and openh264 for encoding on machines with no Nvidia GPU 
- Video frame extensions to allow pointers of RGB and texture data to be passed to the encoder
- RTP package header extensions to allow HoloLens frame prediction timestamps to be synched with the encoded frame 
- Override to prioritize H264 codecs

#### WebRTC UWP wrapper:

- Extensions to MediaStreamSource to enable HoloLens frame prediction timestamps 
- Improvements to MF sample timestamps and duration for better decoding performance

INSTRUCTIONS
=======

From your terminal, please clone the git repository:
<br />
<pre>
<code>
git clone --recursive -b 3dtoolkit-M62-release https://github.com/ortclib/ortclib-sdk.git 3dtoolkit-M62-release
</code>
</pre>
<br />
Make sure you use the above command; a simple clone will not download all dependencies. In case you experience any errors while downloading the submodules, you can retry using these commands:
<br />
<pre>
<code>
git submodule init
git submodule update
</code>
</pre>
<br />
IMPORTANT NOTES:

1)  Ensure that Git is properly configured to handle line endings. Git setting for core.autocrlf needs to be set to true; you can check current setting for core.autocrlf using command: 'git config -l', or 'git config core.autocrlf', and you can change setting to true using 'git config --global core.autocrlf true'. 
    Usefull links: 
	https://help.github.com/articles/dealing-with-line-endings/
	https://git-scm.com/book/en/v2/Customizing-Git-Git-Configuration#__code_core_autocrlf_code (section core.autocrlf)  
2) Visual Studio 2017 is required
3) Latest supported Win 10 SDK is 10.0.14393.x

HOW TO BUILD FOR WINDOWS
----------------------------
In order to build the native and UWP libraries required in 3D Streaming Toolkit, you need to run a batch script.

1) Run build3DToolkitLibs script, from your terminal:
<br />
<pre>
<code>
cd 3dtoolkit-M62-release
bin\build3DToolkitLibs.bat
</code>
</pre>
<br />
This script will prepare the solution, download all the required tools, generate the projects, build the native and UWP libraries and copy them to a `dist` folder.

NATIVE CODE CHANGES
----------------------------
The native libraries are generated in two types of projects, one for Win32 and one for UWP. These projects have the same underlying code expect for the H264 encoding/decoding codec:

- `webrtc\xplatform\webrtc\out\win_(platform)_(configuration)` - Win32 specific build with Nvpipe/OpenH264 for encoding and ffmpeg for decoding     
- `webrtc\xplatform\webrtc\out\winuwp_10_(platform)_(configuration)` - UWP specific build with MediaFoundation for encoding/decoding. 

You can open the `all.sln` for any of these libraries and build the libraries for WebRtc. 

UWP CODE CHANGES
----------------------------
The UWP wrapper solution can be found at `\webrtc\windows\solutions\WebRtc.sln`

