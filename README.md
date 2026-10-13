# Stoma Template (standalone web app)

Measure a stoma from a photo with a bank card beside it, and print a true-size cutting template (PDF).

**Trial version for evaluation. Not a medical device. Not clinically validated.**
Do not use it with patients until it has been checked by a clinician and approved under your organisation's own governance.

## What is in this folder

| File | Purpose |
|---|---|
| `index.html` | The whole app (one file, no outside services) |
| `manifest.webmanifest`, `icon-*.png`, `apple-touch-icon.png` | Lets people add it to a phone's home screen with an icon |
| `sw.js` | Lets it work offline after the first visit |

Nothing is sent anywhere. Photos are processed inside the page. A patient name, saved measurements and suppliers are kept only in that browser on that device.

## Put it on the web (free, about 10 minutes)

It must be served over **https** for the home-screen and offline features. Either option below does that automatically.

### Option A: Cloudflare Pages (direct upload)
1. In the Cloudflare dashboard go to *Workers & Pages* > *Create* > *Pages* > *Upload assets*.
2. Name the project (for example `stoma-template`), then drag in **the contents of this folder** (the files, not a zip of the folder).
3. Deploy. You get an address such as `https://stoma-template.pages.dev`. You can attach your own domain later.

### Option B: GitHub Pages
1. Create a new public repository and upload these files to its main branch (*Add file* > *Upload files*).
2. *Settings* > *Pages* > *Deploy from a branch* > `main` / root > Save.
3. After a minute the app is at `https://<your-username>.github.io/<repository>/`.

### Updating later
Upload the new files over the old ones. Installed copies update the next time they are opened online (the version number in `sw.js` changes with each release).

## For a nurse or clinician trying it
1. Open the address on a phone. In Safari tap Share > *Add to Home Screen*; in Chrome use the menu > *Add to Home screen* or *Install app*.
2. Lay a clean bank card flat beside the stoma, not touching it. Hold the phone straight above and parallel to the skin. Keep the whole card and the stoma in view.
3. Choose the photo. The app looks for the card; confirm the yellow outline sits on it (or tap the four corners).
4. Tap round the stoma where it meets the skin.
5. Choose an allowance, save the PDF and print at **100% (actual size)**.
6. Check the bank-card box, the 100 mm ruler and the X and Y dimension lines on the printout. If they do not measure correctly, the printer scaled the page: print again at 100%.

For a trial, leave the patient name blank and use example subjects or yourself, until your organisation has approved it.

## Known limits
- Tested only on simulated photos and by the developer; not compared with clinical measurements.
- Accuracy depends on a flat card, a sharp photo and the phone being parallel to the skin. The app warns when the card looks tilted or small.
- The card finder can pick the wrong rectangle on a busy background; the confirm step is there for that.
- Sending the email: the PDF can only be attached through "Share PDF" (where the phone allows it) or by attaching the downloaded file yourself.
