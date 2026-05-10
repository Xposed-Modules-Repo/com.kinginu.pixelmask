# PixelMask

Make Google Photos believe your phone is a Google Pixel — and unlock
Pixel-only perks like **free unlimited Original-quality backup** on any
rooted Android device.

![PixelMask app screens](https://raw.githubusercontent.com/kinginu/PixelMask/main/docs/banner-app.png)

> Source code, full README, issue tracker, and release notes live at the
> source repository: **https://github.com/kinginu/PixelMask**
>
> This repository (`Xposed-Modules-Repo/com.kinginu.pixelmask`) only exists
> so PixelMask shows up in LSPosed Manager's module catalog. Each release
> here mirrors the corresponding release in the source repo.

---

## What it does

Google Photos checks two things to decide whether you're on a Pixel:

- the device fingerprint (`Build.MANUFACTURER`, `MODEL`, `BRAND`, `FINGERPRINT`)
- a list of `hasSystemFeature("PIXEL_<year>_EXPERIENCE")` flags

PixelMask intercepts both — but only inside the Photos process, nothing else
on your phone is affected — and replies with the answers a Pixel of your
choosing would give. Photos then turns on the perks tied to that Pixel.

## Install

1. Find PixelMask in **LSPosed Manager** → Modules and tap install (or
   download the latest APK from the [Releases](https://github.com/Xposed-Modules-Repo/com.kinginu.pixelmask/releases) page).
2. Enable PixelMask in LSPosed Manager.
3. **Scope it to Google Photos *and* to PixelMask itself.** Both. Without
   scoping the module to itself, the home screen sticks on *Module Not
   Active* even when the hook is working.
4. Open **PixelMask** → switch to the **Settings** tab.
5. Tap **Target Device** and pick the Pixel you want Photos to think you're
   on (see the table below).
6. Tap **Stop Google Photos in Settings** and force-stop Photos.
7. Open Google Photos and let it start fresh.

## Did it actually work?

Photos doesn't pop up a "you're a Pixel now" banner. Open Photos → tap your
Google account icon (top-right) → **Photos settings** → **Backup**. If the
spoof is working, you'll see this line:

> **This Pixel can back up unlimited photos & videos at no charge.**

![Photos backup proof flow](https://raw.githubusercontent.com/kinginu/PixelMask/main/docs/banner-proof.png)

If that line isn't there, common causes are: forgot to force-stop Photos
after changing the target Pixel; forgot to scope the module to itself in
LSPosed; another module (`tricky_store`, `shamiko`, `hidemyapplist`, …) is
hiding LSPosed from Photos.

## Which Pixel should I pick?

| Target | What you get |
|---|---|
| **Pixel** *(default)* | **Lifetime unlimited Original-quality backup.** The original 2016 Pixel is the only model whose perk Google never rolled back. |
| Pixel 2 – Pixel 5 | Unlimited *Storage Saver* (compressed) backup. |
| Pixel 6 / 7 (Pro) | No notable Photos perk — Google ended the storage benefit for these generations. |
| Pixel 8 Pro | Video Boost, Night Sight Video. |
| Pixel 9 Pro XL | Add Me, Reimagine, unlimited Magic Editor. |
| Pixel 10 Pro XL | Latest Pixel-first AI features. |

If you came here for free unlimited storage, **the original Pixel** is what
you want. The defaults are already set to it.

## Requirements

- Rooted Android 8.0 or newer (`arm64-v8a`)
- An Xposed framework: [LSPosed](https://github.com/LSPosed/LSPosed) on
  Magisk, or [zygisk-vector](https://github.com/HuskyDG/zygisk-vector) +
  LSPosed on KernelSU / APatch
- Google Photos installed

## Issues, source, license

Everything else lives at the source repo:

- **Source / issue tracker:** https://github.com/kinginu/PixelMask
- **License:** MIT
- **Disclaimer:** for research and educational use; no warranty
