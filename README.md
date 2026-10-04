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

Builds up to and including **1.2** are signed with an Android **debug** key:

```
CN=Android Debug, O=Android, C=US
SHA-256  e6:ef:a8:84:2d:ae:66:42:e1:95:63:80:21:19:cd:a8:
         78:8e:bc:53:1e:57:95:7c:4b:6c:3e:14:0a:33:08:a3
```

That key will be replaced by a proper release key. When it is, the first build
signed with the new one **cannot install over an older copy** — follow the
"Updating in place" steps above: back up, uninstall, install, restore.
