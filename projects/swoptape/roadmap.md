# swoptape: Roadmap

## Done

- Project scaffolding
- Config loading
- Database layer (GORM + PostgreSQL)
- User model with granular permissions (`admin`, `upload`, `tag`) and TOTP
- Session model with IP, user agent, last used, and revoked tracking

## Upcoming

### Server
- Music library scanning (collections — file-based)
- Tag-based views (albums, artists) when tag quality is sufficient
- Streaming and download
- Subsonic API implementation
- Web UI API and General API split
- `storage` service
- Background job system (via gokit)
- Auth — JWT access and refresh tokens (to be shared with swopcart via gokit)

### Frontend
- Web UI (via react-ui)

## Future

- Mobile client (iOS, Android)
