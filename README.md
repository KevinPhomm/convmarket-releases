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

All builds from **1.2** onward are signed with the Conv'Market release key:

```
CN=ConvMarket, O=ConvMarket
RSA 4096
SHA-256  56:16:93:0b:dc:dc:24:93:57:30:b2:30:32:ff:e4:fa:
         e0:1e:d7:39:eb:86:9c:5e:d1:38:b4:ae:65:f9:68:92
```

If `apksigner` reports any other certificate, the file is not a build from here.

No earlier build was ever published, so nothing on a phone was signed with a
different key and no uninstall should ever be needed for an in-place update.
