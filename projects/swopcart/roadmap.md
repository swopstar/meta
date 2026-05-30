# swopcart: Roadmap

## Done

### Server
- Platform configuration (embedded `platforms.toml`, auto-seeded on first run)
- Library management — create, update, delete with multi-path support
- ROM scanner — directory-based and flat-file, sidecar metadata, external ID markers
- Streaming hash calculation (MD5, SHA1, SHA256) via single file pass
- Library reimport (hard-delete + rescan)
- Game browser frontend — search, filters, download
- Background job system (extracted to gokit)
- JWT auth — access and refresh tokens
- User management

## Upcoming

### Server
- ROM identification via hash lookups (IGDB or similar)
- Save file sync — `savedata` and `storage` services, conflict resolution
  - **flag** mode: sync the latest save as-is, for large or project-style saves (OpenTTD, Civilisation, Cities Skylines, newer Ace Attorney titles)
  - **checkpoint** mode: store a new save file per play session, for progression-style saves (Super Metroid, older Ace Attorney titles, Celeste, Two Point Hospital)
- General API vs Web UI API split
- User-specific library access control

### Client
- Client service (background daemon)
- Client CLI

### Client UI
- Desktop form factor
- 10-foot form factor (Steam Deck, TV)

## Future

- Pull games from storefronts (e.g. itch.io)
- RetroArch fork as an alternative client
- Settings → About this instance (source link for AGPL compliance)
