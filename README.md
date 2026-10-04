# Conv'Market releases

Builds of Conv'Market, an offline Android app for counting stock and recording
sales at conventions and markets. The app's source is not here — this repo holds
only the version manifest and the installable builds.

`version.json` is what the app reads, at most once a day, to find out whether a
newer build exists. It is a plain public file; the request carries no app data.

## Installing

1. Download the `.apk` from the newest entry under **Releases**.
2. Open it on the phone. Android will ask you to allow installing apps from your
   browser — that permission is what lets a sideloaded app install at all.
3. Needs Android 8.0 (API 26) or newer.

## Updating in place

An update only installs over an existing copy if both are signed with the same
key. If Android refuses with *"App not installed"* or
*"update incompatible"*, the signing key has changed: back up first from
**Settings → Backup → Back up now**, uninstall, install the new build, then
restore. Uninstalling without a backup loses all stock, sales and photos.

## Verifying a download

```
apksigner verify --print-certs convmarket-<version>.apk
```

The expected SHA-256 of the signing certificate will be published here once a
release signing key is in use.
