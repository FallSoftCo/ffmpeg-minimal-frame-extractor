# FFmpeg Minimal Frame Extractor

This repository contains a minimal FFmpeg build specifically optimized for extracting frames from YouTube videos.

## Features

This minimal build includes only:
- HTTP/HTTPS protocol support for YouTube URLs
- Video decoders: H264, HEVC, VP8, VP9
- JPEG encoder for frame output
- Scale filter for thumbnails
- No audio support
- No unnecessary codecs or filters

## Binary Size

The binary is approximately 10MB (compared to 70MB+ for full FFmpeg).

## Usage

```bash
./ffmpeg-frame-extractor-linux-x64 -ss 10 -i "https://youtube.com/..." -frames:v 1 -q:v 2 -vf scale=240:180 output.jpg
```

## Build Configuration

```
--disable-everything
--enable-small
--enable-static
--disable-shared
--enable-lto
--enable-protocol=file,http,https,tcp,tls
--enable-demuxer=mov,mp4,matroska,webm,flv
--enable-decoder=h264,hevc,vp8,vp9
--enable-encoder=mjpeg
--enable-muxer=image2
--enable-filter=scale,format
```