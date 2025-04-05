# Webtor, self-hosted

This is the self-hosted version of [webtor.io](https://webtor.io), implemented as an all-in-one Docker image.

## Features

- **Direct Download Link (DDL):** Select any file inside a torrent and download it directly.
- **Instant Video and Audio Streaming:** Choose a video or audio file inside a torrent and start streaming immediately without needing to download it first.  
  **Supported Formats:**
   - **Video:** `avi`, `mkv`, `mp4`, `webm`, `m4v`, `ts`, `vob`
   - **Audio:** `mp3`, `wav`, `ogg`, `flac`, `m4a`
- **Download Entire Torrent as a ZIP Archive:** Download your torrent as a ZIP archive on-the-fly while preserving the original directory structure, without requiring a torrent client.
- **Developer friendly** - with the [SDK](https://github.com/webtor-io/embed-sdk-js) you can provide your users with the ability to watch torrent-videos online on your website.
- **Multi-architecture support:** Runs on both `amd64` and `arm64/v8` platforms.

## Quick Setup

1. [Install Docker](https://docs.docker.com/get-docker/).
2. Start your Webtor instance with the following command:
   ```bash
   docker run -d -p 8080:8080 -v data:/data --name webtor --restart=always ghcr.io/webtor-io/self-hosted:latest
   ```
3. Access the UI at <http://localhost:8080>.
4. You're all set!

## Setting a Custom Domain

If you plan to access your instance from a different host or domain, set the `DOMAIN` environment variable like this:

```bash
docker run -e DOMAIN=https://example.com -d -p 8080:8080 -v data:/data --name webtor --restart=always ghcr.io/webtor-io/self-hosted:latest
```

## Configuring the Autocleaner

Webtor automatically cleans old data when there is insufficient space on the device. You can configure this behavior using the following variables:

```bash
CLEANER_FREE=35%
CLEANER_KEEP_FREE=25%
```

- `CLEANER_FREE` specifies how much space to clean when triggered.
- `CLEANER_KEEP_FREE` sets the threshold at which cleaning starts.

Both variables can be defined as percentages or as byte values (e.g., `10G` or `100M`).
