# MiracleTek mobile workflow prototype: installable web app

This folder is a complete, self-contained copy of the prototype. It does not use Claude or any other online service. Once the files are on a web address, anyone can open it and install it on an iPhone or Android phone like an app.

It uses sample data only. Nothing is stored or sent anywhere, and it resets each time it is closed.

## What is in the folder

| File or folder | Purpose |
|---|---|
| `index.html` | The app |
| `manifest.json` | Tells phones the name, icon and full-screen behaviour |
| `sw.js` | Saves the app on the phone so it opens offline after the first visit |
| `icons/` | App icons (MiracleTek logo) |
| `fonts/` | Manrope and Barlow Semi Condensed fonts, bundled so nothing loads from the internet (licences included) |

Keep all of these together. The files must sit at the top level of the web address, with `index.html` as the home page.

## 1. Put it on a web address

The address must start with **https://**. Any host that serves static files works. Two easy options:

**GitHub Pages (free)**
1. Create a new repository on GitHub.
2. Upload the contents of this folder to the repository's top level, not the folder itself.
3. Go to **Settings, then Pages**. Under Build and deployment, choose **Deploy from a branch**, pick **main** and **/(root)**, then **Save**.
4. After a minute the address appears at the top of that page, like `https://yourname.github.io/yourrepo/`.

**Azure Storage static website**
1. In the Azure portal, open a Storage account and go to **Data management, then Static website**.
2. Select **Enabled**, set the index document name to `index.html`, and **Save**. Copy the **Primary endpoint** (it starts with https://).
3. Upload the files into the `$web` container, keeping the `icons` and `fonts` folders. This is easiest with Azure Storage Explorer, or with:
   `az storage blob upload-batch --auth-mode login --account-name <storage-account> --source <path-to-this-folder> --destination '$web'`

**Who can open it:** anyone who has the address. The prototype contains no real data. If access must be limited, host it on a site that is behind your company sign-in.

## 2. Test it on a phone

Open the address on a phone and tap **Sign in**. No account is needed. The sign-in screen already has a sample email, and any password works.

## 3. Message to send to people

> Open this link on your phone: **[your address]**
>
> **iPhone:** open it in **Safari**, tap the **Share** button, then **Add to Home Screen**, then **Add**.
> **Android:** open it in **Chrome**, tap the **⋮** menu, then **Install app**.
>
> Tap Sign in to start. There is nothing to log in to and all data is sample data. Open it once while you have a connection and it will also work offline.

The app also has this guide built in: Sign in screen, then **Install on this device**, or the profile icon on My Work.

Safari is needed on iPhone. The browsers inside Outlook, Teams and Mail do not offer Add to Home Screen, so people should open the link in Safari or Chrome first.

## Updating it later

1. Change the files.
2. Open `sw.js` and change `VERSION` (for example from `miracletek-proto-v2` to `miracletek-proto-v3`).
3. Upload the files again over the old ones.

People get the new version the next time they open the app while online.

## Notes

- The Manrope and Barlow fonts are licensed under the SIL Open Font License (see the licence files in `fonts/`).
- The MiracleTek logo is the file you supplied, and the colour theme (red and charcoal) is taken from it.
- This is a prototype for discussion, not a certified or production system.
