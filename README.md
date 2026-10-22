# spinoapp.github.io

Website and downloads for [Spino](https://spinoapp.github.io), a posture reminder for the macOS menu bar.

The site is a single static page (`index.html`) served by GitHub Pages from `main`.
The app's source lives in a separate private repository; this repository only hosts
the site and the signed `Spino.dmg` builds attached to [Releases](../../releases).

## Publishing a new version

In the app repository:

```bash
./scripts/package.sh   # → dist/Spino.dmg
```

Then attach it to a new release here (bump the tag to match `MARKETING_VERSION`):

```bash
gh release create v1.0 ../spino/dist/Spino.dmg \
  --repo spinoapp/spinoapp.github.io --title "Spino 1.0" --notes "…"
```

The download buttons point at `releases/latest/download/Spino.dmg`, so the site
picks up the new build without any change. Keep the asset name `Spino.dmg`.

Only one release is kept: the newest. A new release becomes `latest`
automatically, so delete older ones together with their tags:

```bash
gh release delete v0.9 --cleanup-tag --yes   # an older release
```
