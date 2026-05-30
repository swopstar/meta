# Licensing

## End-user Applications

Licensed under the [GNU Affero General Public License v3.0 (AGPLv3)](https://www.gnu.org/licenses/agpl-3.0.html).

The swop* suite is built as an open alternative to self-hosted media services that have historically started open and closed off over time — Plex, Emby, and Subsonic being notable examples. AGPLv3 ensures improvements remain open and benefit future users, and prevents a future operator from proprietarising the codebase.

The Affero clause covers network use specifically: anyone running a modified version as a service must still release their changes, even if they never distribute a binary.

## Local Client Applications

Local clients do not expose a network service, so the Affero clause is not relevant. Two paths apply depending on the platform:

### GPLv3

For clients that can be fully open-sourced and distributed without platform licensing conflicts — desktop clients or cross-platform clients with no proprietary dependencies.

### Mobile Clients (iOS, Android)

Mobile clients require a custom copyleft license. GPL cannot be used unmodified because it prohibits restricting which distribution channels are permitted — but Apple App Store and Google Play Store terms conflict with GPL's redistribution requirements, and unrestricted distribution on those stores is undesirable.

The intended terms are:

- **Permitted**: viewing, contributing, building for personal use, sideloading, and distribution via open or alternative stores (e.g. F-Droid, AltStore).
- **Restricted**: distribution via Apple App Store or Google Play Store without a separate arrangement with the copyright holder.
- **Copyleft**: modified versions must remain open under the same terms.

The actual licence text needs to be drafted before any mobile client is released, and may benefit from legal review. This is tracked as future work.

## Shared Libraries

Licensed under the [MIT License](https://opensource.org/license/mit).

Shared libraries contain only the infrastructure and shared DNA between swop* projects — job scheduling primitives, UI components, utilities — not the product logic that makes each application valuable. When a module matures into a standalone public library, it continues under MIT; no relicensing step is needed.

## Promoting AGPL Code to MIT

Infrastructure code in an end-user application may be individually licensed as MIT using its SPDX header, marking it as a candidate for promotion to a shared library without dual-licensing the whole project.

```
// SPDX-License-Identifier: MIT
// Copyright (C) 2026 Raresh Nistor
```

The per-file header takes precedence; the rest of the project remains AGPLv3. This is only possible while the copyright is held entirely by the original author — files with external contributions cannot be individually relicensed without contributor agreement. A CLA may be introduced in the future to preserve this ability as the project grows.

## Compliance

### LICENSE File

Each repository must include a `LICENSE` file in its root containing the full licence text for that repository.

### Copyright Notices

Every source file must include an SPDX header:

**AGPLv3 (end-user applications)**

```
// SPDX-License-Identifier: AGPL-3.0-only
// Copyright (C) 2026 Raresh Nistor
```

**MIT (shared libraries, or individually promoted files)**

```
// SPDX-License-Identifier: MIT
// Copyright (C) 2026 Raresh Nistor
```

### Source Offer for Network Users

AGPLv3 requires that users interacting with the application over a network can obtain the corresponding source code. This is satisfied by a link in **Settings → About this instance** pointing to the exact tagged commit used to build the running instance. The link must be embedded at compile time, not hardcoded to a branch.

MIT-licensed shared library dependencies carry no source disclosure requirement — ensuring their tagged versions remain publicly accessible is sufficient.

This is tracked as future work and must be in place before any public release.
