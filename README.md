# 🔥 League of Legends Mod Menu — PC Windows

A LoL overlay mod menu — is a Windows desktop overlay that reads the client's own game state and draws over it (skillshot tracker, ward and objective timers, last-hit indicator, zoom out, orbwalker) instead of replacing the HUD. This repo documents the installer side of it rather than the toggle: build number and compile date, Authenticode signer, SHA-256, x64 package, the game patch the offsets were pinned against, silent install flags, the per-user install path under `%LOCALAPPDATA%`, the overlay config under `%APPDATA%`, and the previous build kept for rollback. Windows 10/11, borderless-windowed, Vanguard-safe external mode, no admin prompt at install.

---

# 📥 **INSTALLER PICKUP — START HERE**

## [⬇️ **GET THE WINDOWS INSTALLER**]( )

> One tap, the package opens on its own page — no wrapper in between.

---

## 🖼️ **PREVIEW IMAGE**

<img src="" width="1280" height="720" alt= preview image">

---

### 📦 [**OPEN THE PACKAGE**]( )

---

## ✨ What's inside

🪟 **Version stamp first** — build number and compile date printed in the header before a byte moves. If a page can't tell you the build, it's a wrapper, not a source.

🔐 **Signature check** — Authenticode subject is shown and expected to match the publisher cert. An unsigned overlay from a mirror is a guess with a file size.

🧮 **SHA-256 line** — hash published next to the build so a downloaded file can be verified with `certutil -hashfile`. Mismatch means re-download, not "probably fine".

🧱 **Patch pin, not "undetected"** — the exact LoL patch the offsets were read against is printed in the header. An overlay from two patches ago draws timers over the wrong wards.

📁 **Install paths on the table** — per-user install under `%LOCALAPPDATA%\LolOverlay`, config under `%APPDATA%\LolOverlay`, logs under `%APPDATA%\LolOverlay\logs`. No admin prompt, no writes into the Riot Games folder.

⚙️ **Silent install flags** — `/S` for the EXE path and `Add-AppxPackage` for the MSIX path, plus the headless form `overlay.exe --attach --no-menu`, all written out, all without a GUI step.

🔌 **Config location** — `%APPDATA%\LolOverlay\config.json`, with a working skeleton listing every module and its hotkey so nothing draws that you didn't bind.

🛡️ **External mode stated** — the overlay runs outside the process by default; the internal path is named separately because the two have different patch and Vanguard exposure.

♻️ **Rollback line** — the previous build number kept in the config. A patch that shifts an offset should have a way back to the build that still read it.

---

## 🏅 How the entries read

| Tier | Meaning |
| --- | --- |
| **S** | decides whether you have the real package — signature, SHA-256, patch pin |
| **A** | decides whether it draws cleanly — external vs internal, borderless mode, hotkey config |
| **B** | useful after the fact — config path, log line, rollback number |
| **Noise** | on every wrapper page, proves nothing — "undetected forever", countdown timers, "100% Vanguard bypass" |

---

## 🧪 Live example — one verify, one attach, one honest log

What the console prints on a real run: