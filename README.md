baresip README
==============


![Baresip Logo](https://raw.githubusercontent.com/baresip/baresip/master/share/logo.png)


Baresip is a portable and modular SIP User-Agent with audio and video support.
Copyright (c) 2010 - 2021 Alfred E. Heggestad and Contributors
Distributed under BSD license


![Build](https://github.com/baresip/baresip/workflows/Build/badge.svg)
![ccheck](https://github.com/baresip/baresip/workflows/ccheck/badge.svg)
![OpenSSL and LibreSSL](https://github.com/baresip/baresip/workflows/OpenSSL%20no-deprecated%20and%20LibreSSL/badge.svg)
![Valgrind](https://github.com/baresip/baresip/workflows/valgrind%20leak%20check/badge.svg)


## Features:

* Call features:
  - Unlimited number of SIP accounts
  - Unlimited number of calls
  - Unattended call transfer
  - Auto answer
  - Call hold and resume
  - Microphone mute
  - Call waiting
  - Call recording
  - Peer to peer calls
  - Video calls
  - Instant Messaging
  - Custom ring tones
  - Repeat last call (redial)
  - Message Waiting Indication (MWI)
  - Address book with presence

* Signaling:
  - SIP protocol support
  - SIP outbound protocol for NAT-traversal
  - SIP Re-invite
  - SIP Routes
  - SIP early media support
  - DNS NAPTR/SRV support
  - Multiple accounts support
  - DTMF support (RTP, SIP INFO)
  - Multicast sending & receiving

* Security:
  - Signalling encryption (TLS)
  - Audio and video encryption (Secure RTP)
  - DTLS-SRTP key exchange protocol
  - ZRTP key exchange protocol
  - SDES key exchange protocol

* Audio:
  - Low latency audio pipeline
  - High definition audio codecs
  - Audio device configuration
  - Audio filter plugins
  - Internal audio resampler for fixed sampling rates
  - Linear 16 bit wave format support for ringtones
  - Packet loss concealment (PLC)
  - Configurable ringtone playback device
  - Automatic gain control (AGC) and Noise reducation
  - Acoustic echo control (AEC)
  - Configurable audio sample format (Signed 16-bit, 24-bit, Float etc)
  - EBU ACIP (Audio Contribution over IP) Profile

* Audio-codecs:
  - AAC
  - aptX
  - AMR narrowband, AMR wideband
  - Codec2
  - G.711
  - G.722
  - G.726
  - GSM
  - iLBC
  - L16
  - MPA
  - Opus

* Audio-drivers:
  - Advanced Linux Sound Architecture (ALSA) audio-driver
  - PulseAudio POSIX OSes audio-driver
  - Android OpenSLES audio-driver
  - Gstreamer playbin input audio-driver
  - JACK Audio Connection Kit audio-driver
  - MacOSX/iOS coreaudio/audiounit audio-driver
  - Open Sound System (OSS) audio-driver
  - Portaudio audio-driver
  - Windows winwave audio-driver

* Video:
  - Support for H.265, H.264, H.263, VP8, VP9, MPEG-4 Video
  - Configurable resolution/framerate/bitrate
  - Configurable video input/output
  - Support for asymmetric video
  - Configurable video pixel format
  - Hardware acceleration for video encoder/decoder

* Video-codecs:
  - H.265
  - H.264
  - H.263
  - VP8
  - VP9
  - MPEG-4

* Video-drivers:
  - iOS avcapture video-source
  - FFmpeg/libav libavformat/avdevice input
  - Cairo video-source test module
  - Direct Show video-source
  - MacOSX AVCapture video-source
  - RST media player
  - Linux V4L/V4L2 video-source
  - X11 grabber video-source
  - DirectFB video-output
  - SDL2 video-output
  - X11 video-output

* NAT-traversal:
  - STUN support
  - TURN server support
  - ICE support
  - NATPMP support
  - PCP (Port Control Protocol) support

* Networking:
  - multihoming, IPv4/IPv6
  - automatic network roaming

* Management:
  - Embedded web-server with HTTP interface
  - Command-line console over UDP/TCP
  - Command line interface (CLI)
  - Simple configuration files
  - MQTT (Message Queue Telemetry Transport) module

* Profiles:
  - EBU ACIP (Audio Contribution over IP) Profile


## Building

baresip is using GNU makefiles, and the following packages must be
installed before building:

* [libre](https://github.com/baresip/re)
* [librem](https://github.com/baresip/rem)
* [openssl](https://www.openssl.org/)


### Build with debug enabled

```
$ make
$ sudo make install
```

### Build with release

```
$ make RELEASE=1
$ sudo make RELEASE=1 install
```

### Build with clang compiler

```
$ make CC=clang
$ sudo make CC=clang install
```

Modules will be built if external dependencies are installed.
After building you can start baresip like this:

```
$ baresip
```

The config files in $HOME/.baresip are automatically generated
the first time you run baresip.


### Examples

Configuration examples are available from the
[examples](https://github.com/baresip/baresip/tree/master/docs/examples)
directory.


## License

The baresip project is using the 3-clause BSD license.


## Contributing

Patches can be sent via Github
[Pull-Requests](https://github.com/baresip/baresip/pulls) or to the Baresip
[mailing-list](https://groups.google.com/g/baresip).


## Design goals:

* Minimalistic and modular VoIP client
* SIP, SDP, RTP/RTCP, STUN/TURN/ICE
* IPv4 and IPv6 support
* RFC-compliancy
* Robust, fast, low footprint
* Portable C89 and C99 source code


## Modular Plugin Architecture:
```
aac           Advanced Audio Coding (AAC) audio codec
account       Account loader
alsa          ALSA audio driver
amr           Adaptive Multi-Rate (AMR) audio codec
aptx          Audio Processing Technology codec (aptX)
aubridge      Audio bridge module
audiounit     AudioUnit audio driver for MacOSX/iOS
aufile        Audio module for using a WAV-file as audio input
auloop        Audio-loop test module
ausine        Audio sine wave input module
avcapture     Video source using iOS AVFoundation video capture
avcodec       Video codec using FFmpeg/libav libavcodec
avformat      Video source using FFmpeg/libav libavformat
b2bua         Back-to-Back User-Agent (B2BUA) module
cairo         Cairo video source
codec2        Codec2 low bit rate speech codec
cons          UDP/TCP console UI driver
contact       Contacts module
coreaudio     Apple macOS Coreaudio driver
ctrl_tcp      TCP control interface using JSON payload
debug_cmd     Debug commands
directfb      DirectFB video display module
dshow         Windows DirectShow video source
dtls_srtp     DTLS-SRTP end-to-end encryption
ebuacip       EBU ACIP (Audio Contribution over IP) Profile
echo          Echo server module
evdev         Linux input driver
fakevideo     Fake video input/output driver
g711          G.711 audio codec
g722          G.722 audio codec
g7221         G.722.1 audio codec
g726          G.726 audio codec
gsm           GSM audio codec
gst           Gstreamer audio source
gst_video     Gstreamer video codec
gtk           GTK+ 2.0 UI
gzrtp         ZRTP module using GNU ZRTP C++ library
httpd         HTTP webserver UI-module
i2s           I2S (Inter-IC Sound) audio driver
ice           ICE protocol for NAT Traversal
ilbc          iLBC audio codec
jack          JACK Audio Connection Kit audio-driver
l16           L16 audio codec
menu          Interactive menu
mpa           MPA Speech and Audio Codec
multicast     Multicast RTP send and receive
mqtt          MQTT (Message Queue Telemetry Transport) module
mwi           Message Waiting Indication
natpmp        NAT Port Mapping Protocol (NAT-PMP) module
omx           OpenMAX IL video display module
opensles      OpenSLES audio driver
opus          OPUS Interactive audio codec
oss           Open Sound System (OSS) audio driver
pcp           Port Control Protocol (PCP) module
plc           Packet Loss Concealment (PLC) using spandsp
portaudio     Portaudio driver
pulse         Pulseaudio driver
presence      Presence module
rtcpsummary   RTCP summary module
rst           Radio streamer using mpg123
sdl           Simple DirectMedia Layer 2.0 (SDL) video output driver
selfview      Video selfview module
snapshot      Save video-stream as PNG images
sndfile       Audio dumper using libsndfile
sndio         Audio driver for OpenBSD
speex_pp      Audio pre-processor using libspeexdsp
srtp          Secure RTP encryption (SDES) using libre SRTP-stack
stdio         Standard input/output UI driver
stun          Session Traversal Utilities for NAT (STUN) module
swscale       Video scaling using libswscale
syslog        Syslog module
turn          Obtaining Relay Addresses from STUN (TURN) module
uuid          UUID generator and loader
v4l2          Video4Linux2 video source
v4l2_codec    Video4Linux2 video codec module (H264 hardware encoding)
vidbridge     Video bridge module
vidinfo       Video info overlay module
vidloop       Video-loop test module
vp8           VP8 video codec
vp9           VP9 video codec
vumeter       Display audio levels in console
webrtc_aec    Acoustic Echo Cancellation (AEC) using WebRTC SDK
wincons       Console input driver for Windows
winwave       Audio driver for Windows
x11           X11 video output driver
x11grab       X11 grabber video source
zrtp          ZRTP media encryption module
```


## IETF RFC/I-Ds:

* RFC 2190  RTP Payload Format for H.263 Video Streams (Historic)
* RFC 2250  RTP Payload Format for the mpa Speech and Audio Codec
* RFC 2429  RTP Payload Format for 1998 ver of ITU-T Rec. H.263 Video (H.263+)
* RFC 3016  RTP Payload Format for MPEG-4 Audio/Visual Streams
* RFC 3428  SIP Extension for Instant Messaging
* RFC 3711  The Secure Real-time Transport Protocol (SRTP)
* RFC 3640  RTP Payload Format for Transport of MPEG-4 Elementary Streams
* RFC 3856  A Presence Event Package for SIP
* RFC 3863  Presence Information Data Format (PIDF)
* RFC 3951  Internet Low Bit Rate Codec (iLBC)
* RFC 3952  RTP Payload Format for iLBC Speech
* RFC 4145  TCP-Based Media Transport in SDP
* RFC 4240  Basic Network Media Services with SIP (partly)
* RFC 4347  Datagram Transport Layer Security
* RFC 4568  SDP Security Descriptions for Media Streams
* RFC 4572  Connection-Oriented Media Transport over TLS Protocol in SDP
* RFC 4574  The SDP Label Attribute
* RFC 4585  Extended RTP Profile for RTCP-Based Feedback (RTP/AVPF)
* RFC 4587  RTP Payload Format for H.261 Video Streams
* RFC 4629  RTP Payload Format for ITU-T Rec. H.263 Video
* RFC 4796  The SDP Content Attribute
* RFC 4867  RTP Payload Format for the AMR and AMR-WB Audio Codecs
* RFC 4961  Symmetric RTP / RTP Control Protocol (RTCP)
* RFC 5285  A General Mechanism for RTP Header Extensions
* RFC 5373  Requesting Answering Modes for SIP
* RFC 5506  Support for Reduced-Size RTCP
* RFC 5576  Source-Specific Media Attributes in SDP
* RFC 5577  RTP Payload Format for ITU-T Recommendation G.722.1
* RFC 5626  Managing Client-Initiated Connections in SIP
* RFC 5627  Obtaining and Using GRUUs in SIP
* RFC 5761  Multiplexing RTP Data and Control Packets on a Single Port
* RFC 5763  Framework for Establishing a SRTP Security Context Using DTLS
* RFC 5764  DTLS Extension to Establish Keys for SRTP
* RFC 6157  IPv6 Transition in SIP
* RFC 6184  RTP Payload Format for H.264 Video
* RFC 6263  App. Mechanism for Keeping Alive NAT Associated with RTP / RTCP
* RFC 6416  RTP Payload Format for MPEG-4 Audio/Visual Streams
* RFC 6464  A RTP Header Extension for Client-to-Mixer Audio Level Indication
* RFC 6716  Definition of the Opus Audio Codec
* RFC 6886  NAT Port Mapping Protocol (NAT-PMP)
* RFC 7064  URI Scheme for STUN Protocol
* RFC 7065  TURN Uniform Resource Identifiers
* RFC 7310  RTP Payload Format for Standard apt-X and Enhanced apt-X Codecs
* RFC 7587  RTP Payload Format for the Opus Speech and Audio Codec
* RFC 7741  RTP Payload Format for VP8 Video
* RFC 7798  RTP Payload Format for High Efficiency Video Coding (HEVC)

* draft-ietf-payload-vp9-07


## Architecture:
(note: out of date, needs updating)

```
                   .------.
                   |Video |
                 _ |Stream|\
                 /|'------' \ 1
                /            \
               /             _\|
 .--. N  .----. M  .------. 1  .-------. 1  .-----.
 |UA|--->|Call|--->|Audio |--->|Generic|--->|Media|
 '--'    '----'    |Stream|    |Stream |    | NAT |
            |1     '------'    '-------'    '-----'
            |         C|       1|   |
           \|/      .-----.  .----. |
        .-------.   |Codec|  |Jbuf| |1
        | SIP   |   '-----'  '----' |
        |Session|     1|       /|\  |
        '-------'    .---.      |  \|/
                     |DSP|    .--------.
                     '---'    |RTP/RTCP|
                              '--------'
                              |  SRTP  |
                              '--------'
```

   A User-Agent (UA) has 0-N SIP Calls
   A SIP Call has 0-M Media Streams


## Supported platforms:

* Android (5.0 or later)
* Apple Mac OS X and iOS
* FreeBSD
* Linux
* NetBSD
* OpenBSD
* Solaris
* Windows (mingw and VS2015)


### Supported versions of C Standard library

* Android bionic
* BSD libc
* GNU C Library (glibc)
* Windows C Run-Time Libraries (CRT)
* uClibc


### Supported compilers:

* gcc 4.x or later
* ms vc2003 compiler
* clang 3.x or later


### Supported versions of OpenSSL

* OpenSSL version 1.0.1
* OpenSSL version 1.0.2
* OpenSSL version 1.1.0
* LibreSSL version 2.x
* LibreSSL version 3.x


## Related projects

* [libre - baresip fork](https://github.com/baresip/re)
* [librem - baresip fork](https://github.com/baresip/rem)
* [retest - baresip fork](https://github.com/baresip/retest)
* [libre](https://github.com/creytiv/re)
* [librem](https://github.com/creytiv/rem)
* [retest](https://github.com/creytiv/retest)


## References

* Github: https://github.com/baresip/baresip
* Mailing-list: https://groups.google.com/g/baresip
