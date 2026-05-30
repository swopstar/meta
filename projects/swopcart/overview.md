# swopcart: Overview

swopcart is a self-hosted game library manager for personal game collections —
physical rips, ROM dumps, and other owned games. The name is a nod to swapping
cartridges, and to Stop 'n' Swop from Banjo-Kazooie.

The core experience is Steam-like: browse your collection, download to a device,
play, and pick up where you left off on another device. The difference is that
the library is yours — your hardware, your files, your data.

## Components

### swopcart

The web server. Manages the game library, handles scanning and metadata,
serves files, and provides the API that everything else talks to. Written in Go,
ships as a single binary, designed to run on low-power ARM64 hardware (a typical
entry-level NAS with 1 GB RAM).

### Client service and CLI

A background service that runs on the client device, paired with a command-line
utility for interacting with it. Handles communication with the server, game
downloads, and save file synchronisation. The service is the engine that other
client interfaces are built on top of.

### Client UI

A separate user interface built on the client service, targeting two form factors:

- **Desktop** — for PC use
- **10-foot** — for Steam Deck and TV/living room play

### RetroArch fork *(planned, maybe)*

An alternative client based on a RetroArch fork that launches games directly from
swopcart. For users who prefer to stay inside RetroArch rather than use a separate
UI.

## Goals

- Store and browse a personal game collection (physical rips, ROM dumps)
- Download games to any device on the network
- Sync save files across devices — stop on one, pick up on another
- Run acceptably on modest self-hosted hardware

## Future Goals

- Pull games from storefronts such as [itch.io](https://itch.io)

## Non-goals

- Game streaming (downloads only)
- Being a general-purpose media server
