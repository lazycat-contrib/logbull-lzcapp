# logbull-lzcapp

This repository packages Log Bull as a LazyCat LPK v2 application.

## Runtime

- Package ID: `community.lazycat.app.logbull`
- Version: `0.6.2`
- Upstream image source: `docker.io/logbull/logbull:v0.6.2`
- Manifest runtime image: `registry.lazycat.cloud/czyt/logbull/logbull:76fdab7f67ec74e7`
- HTTP entrypoint: `/` -> `http://logbull:4005/`
- Persistent data: `/lzcapp/var/data` -> `/logbull-data`

The runtime image stays on LazyCat Registry delivery. This migration does not switch the application to built-in mirrors.

## Build

The project now uses split LPK v2 metadata with `package.yml`, `manifest.yml`, and `lzc-build.yml`, and sets `min_os_version: 1.5.0`.

## Automation

`.github/lazycat-action.yml` keeps image delivery in `lazycat` mode, tracks the upstream `docker.io/logbull/logbull` stable `0.x` tags, and publishes only to the MiaoMiao private store.

`.github/workflows/lazycat.yml` supports:

- `push` on `main`
- `workflow_dispatch`
- reusable `workflow_call`

It also enables `versioned-release-asset: true`, so release assets are named like `community.lazycat.app.logbull-v0.6.2.lpk`.

Required GitHub Secrets:

- `LZC_API_TOKEN`
- `APPSTORE_URL`
- `APPSTORE_TOKEN`
- `APP_ID` (optional)
- `PRIVATE_STORE_GROUP_CODES` (optional)
