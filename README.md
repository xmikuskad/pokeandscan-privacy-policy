# PokeAndScan privacy policy website

This folder is the standalone-site staging copy for `xmikuskad/pokeandscan-privacy-policy`, requested in issue 22. The site has two language URLs: `/en/` and `/sk/`.

## Publish and update

The public site uses `en/index.html` and `sk/index.html`; GitHub Pages serves them at:

- https://xmikuskad.github.io/pokeandscan-privacy-policy/en/
- https://xmikuskad.github.io/pokeandscan-privacy-policy/sk/

GitHub Pages is enabled from the default branch root. Shared first-party CSS and the contact link script live in `assets/`. Verify both HTTPS pages on mobile and desktop. Keep the pages static; they need no build step or third-party scripts. Update the date and both language versions whenever actual data practices change. Keep this README as maintainer guidance and do not copy it into the public page.

The Android Settings action opens the Slovak or English URL according to the saved app language. Change the base only if GitHub Pages reports a different canonical URL.

## Implementation notes for maintainers

- The current Android source implements user-started live capture, MP4 processing for the supported reference profile, review, and CSV/JSON export. Verify the exact release build and supported profiles before describing a feature as unavailable or planned.
- During live capture, Android may provide non-game or system-screen frames. The app classifies these in memory, discards the images, and may retain only a warning type and source timestamp; keep that distinction clear in both policy languages.
- Shared CSV/JSON exports are staged in private app cache; old share-cache files are pruned when a later share is prepared, after seven days, and Android may clear the cache sooner. Preserve this retention detail and clarify that deleting a scan does not delete an already-created export.
- `AndroidManifest.xml` sets `android:allowBackup="false"`; the legacy and Android 12+ rules explicitly exclude app data. Some Android manufacturers may not honor device-to-device transfer exclusions, so avoid an absolute guarantee for every device.
- The privacy contact is assembled by first-party JavaScript from separate address components, with a `[at]`/`[dot]` fallback when JavaScript is unavailable. This only reduces simple harvesting; it does not prevent all bots or scraping.
- The owner requested publication of these pages in the public repository. Review the wording and both URLs whenever actual data practices change.
