# swoptape: Overview

swoptape is a self-hosted music library manager. Like swopcart, it is built for
personal use — your files, your hardware, your data.

## Philosophy

swoptape is file-first. The primary organisational unit is **collections** —
file-based navigation that reflects how your music is actually stored on disk.
Tag-based views (albums, artists) are available, but only when tag quality is
high enough to be trustworthy. This avoids the broken artist and album views
that plague music servers with inconsistently tagged libraries.

## Components

### swoptape

The web server. Manages the music library, handles scanning and metadata, serves
files for streaming and download, and provides the API that clients talk to.
Same architecture as swopcart — single Go binary, designed for low-power ARM64
hardware.

### Subsonic API

swoptape implements the [Subsonic API](https://www.subsonic.org/pages/api.jsp)
to provide immediate compatibility with a wide ecosystem of existing clients
(Symfonium, DSub, Ultrasonic, etc.) before a native client is built.

### Client *(future)*

A mobile-first native app (iOS, Android) talking directly to swoptape.
Subsonic client compatibility covers this use case in the interim.

## Goals

- Browse a personal music library by file structure (collections) or by
  tag-based views when tag quality is sufficient
- Stream and download music to any device on the network
- Immediate client support via the Subsonic API
- Run acceptably on modest self-hosted hardware

## Non-goals

- Being a general-purpose media server
- Forcing a tag-based view on a messy library
