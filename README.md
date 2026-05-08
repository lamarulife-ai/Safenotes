# SafeNotes — Privacy Policy

*Your thoughts deserve a private place.*

**Version:** 1.3.1
**Last updated:** April 23, 2026

---

## 🔒 Privacy First — Always

SafeNotes is a **fully offline, on-device** diary. We do **not** collect, transmit, store, or share **any** of your data. Ever.

- No accounts. No sign-up. No email required.
- No analytics. No ads. No trackers. No telemetry.
- No servers. No cloud. No "sync".
- No `INTERNET` permission — the app physically cannot reach the internet, even if it wanted to.

If you forget your PIN, **we cannot help you recover your data** — because we never had it. That's the point.

---

## ✨ What's in the app

- 📓 **Encrypted diary entries** — write, edit, attach photos
- 😊 **Mood tracker** — tag each entry with how you felt (Great / Good / Okay / Bad / Awful)
- 🚀 **Writing streak** — a gentle nudge that counts consecutive days you've written
- 🔔 **Daily reminder** *(optional, opt-in)* — one quiet ping a day at the time you choose
- ❤️ **Favorites** — heart entries on the Home feed to find them again
- 🧱 **Home-screen widget** — date, streak, and a one-tap "+" to start a new entry
- 🖼️ **PIN-locked PDF export** — share a single entry or your whole diary as a password-protected PDF
- 💾 **Encrypted `.nbk` backups** — AES-256-GCM, key derived from your PIN
- 🌗 **Themes & fonts** — light/dark/system, multiple palettes, calligraphy fonts
- 🌍 **10 languages** — English, Hindi, Spanish, Portuguese (BR), Arabic, French, German, Russian, Japanese, Simplified Chinese

---

## 🌐 100% Offline Guarantee

SafeNotes does **not** declare the `INTERNET` permission in its Android manifest. This means:

- Android's kernel-level networking sandbox blocks any socket call from the app
- Even if a third-party library tried to phone home, the OS would reject it
- There is no "trust us" — it's enforced by the operating system itself

You can verify this yourself:
- Open Android **Settings → Apps → SafeNotes → Permissions**
- The list will not show "Wi-Fi & mobile data" — because we never ask for it.

---

## 🔐 Security Details

| What | How |
|------|-----|
| **Diary database** | SQLCipher · AES-256 · key derived from your PIN via PBKDF2-HMAC-SHA256 (120,000 iterations) |
| **Settings & PIN hash** | AndroidX Security `MasterKey` · AES-256-GCM encrypted SharedPreferences |
| **Backups (`.nbk`)** | AES-256-GCM · per-backup random salt · PBKDF2 from your PIN |
| **PDF exports** | Standard 128-bit AES password-protected PDF · password = your current PIN |
| **App entry** | 7-digit PIN required at every cold start |
| **Brute force** | 5 wrong attempts → 10-minute cooldown · survives app kill / reinstall of process |
| **Screenshot block** | `FLAG_SECURE` ON by default · blocks screenshots, screen recording, and Recents thumbnail |
| **Inter-app isolation** | No exported components · no other app can invoke SafeNotes' code |

Photos you attach are downscaled, re-saved as JPEG, and stored in the app's **private internal storage** — inaccessible to other apps. Android's file-system encryption applies; we don't add a second layer at the file level.

---

## 📦 Backup & Restore

You're in full control of your backups.

- Tap **Settings → Data Management → Back up now**
- Choose where to save the `.nbk` file via Android's system file picker — your device, an SD card, Google Drive, Dropbox, anywhere you control
- The file is **encrypted with your PIN** at the moment of backup; only that PIN unlocks it
- We never auto-upload. We never see the file. The picker is the only path data leaves the app.

If you change your PIN later, **old backups still need the old PIN** to restore. The app handles this with a two-stage prompt so you always know which PIN to enter.

---

## 📱 Permissions

SafeNotes requests as few permissions as possible. As of version 1.3.1 the app declares **one** runtime permission, and it is opt-in.

### 🔔 `POST_NOTIFICATIONS` *(optional, opt-in, Android 13+)*

- **When:** Only the moment you flip the *Daily writing reminder* switch ON in *Settings → Data Management*
- **Why:** To post one daily notification at the time you chose
- **Content:** Fixed text — *"Every day has a story / Write yours today."* — never includes any of your entry content
- **Default:** OFF on a fresh install; we never ask until you ask
- **Deny / revoke:** The reminder switch flips back OFF and we never ask again

### 🖼️ Photo selection — *no permission required*

We use the **Android Photo Picker** (system-provided dialog). It runs in a separate system process and only hands the app the specific photos you tap. We do **not** request `READ_MEDIA_IMAGES` or `READ_EXTERNAL_STORAGE`.

### 📂 File saving / restoring — *no permission required*

PDF exports, `.nbk` backups, and downloaded photos use Android's **Storage Access Framework**. The system picker appears, you choose the destination, and the app receives only the URI you picked. We do **not** request `WRITE_EXTERNAL_STORAGE` or `MANAGE_EXTERNAL_STORAGE`.

### ❌ What we never ask for

Contacts · Location · Calendar · Microphone · Camera · Phone · SMS · Accounts · Device ID · Bluetooth · Internet · Background data · Auto-start

---

## 📜 Data We Collect

**None.** Not a single byte.

- ❌ No name, email, phone, or any identifier
- ❌ No analytics, crash reports, telemetry, advertising IDs
- ❌ No third-party SDKs that collect data
- ❌ No "anonymous usage statistics"
- ❌ No diagnostic uploads

The "Name" you enter during onboarding (so the app can greet you with *"Hi Sid 😊"*) is stored **only on your device** and never leaves it.

---

## 🗑 Deleting Your Data

Three independent paths, all 100% under your control:

- **🗒️ Single entry** — open the entry → tap the trash icon
- **🧹 Wipe all entries** — *Settings → Data Management → Delete Data* → type `DELETE` to confirm. Erases every entry and every attached photo. Your PIN, name, theme, language, and reminder settings stay so you can keep using the app — pair with a `.nbk` backup if you want a restore point.
- **🚮 Uninstall the app** — removes the encrypted database, encrypted preferences, all photos, all settings. Nothing remains. There is no cloud copy because there is no cloud.

We do not retain anything on our side. There is nothing to delete on our end — because we never had it.

---

## 🧩 Third-Party Software

SafeNotes is built on open-source libraries:

- **Jetpack Compose / Material 3** (Google) — UI
- **Room** (Google) — database access layer
- **SQLCipher** (Zetetic LLC) — full-database encryption
- **AndroidX Security Crypto** (Google) — encrypted preferences
- **PDFBox** (Apache Software Foundation) — PDF generation with AES password protection
- **Coil** (Coil contributors) — image loading
- **Kotlinx Serialization** (JetBrains) — backup file format
- **AndroidX Emoji2** (Google) — emoji rendering

None of these libraries make network calls in SafeNotes — most physically cannot, because the app does not declare `INTERNET`. None collect telemetry from this app.

The app is distributed via the **Google Play Store** (Google). Google may collect installation/update data per [Google's privacy policy](https://policies.google.com/privacy). That collection is independent of SafeNotes; we have no access to it.

---

## 👶 Children's Privacy

SafeNotes is suitable for users **aged 13 and over**. We do not knowingly collect any information from anyone, regardless of age — because the app does not collect information at all. Parents and guardians may use Google Play and Android parental controls to manage installation.

---

## 🔄 Changes to This Policy

If this policy changes, the updated version will:

- Be published in the project's GitHub repository
- Ship with the next app release
- Have its **Last updated** date refreshed
- Be highlighted in the app's *What's new* on the Play Store, if the change affects what data leaves the device, what permissions are asked, or who has access

---

## 📧 Contact

For privacy questions, requests, or concerns:

- ✉️ **Email:** lamarulife@gmail.com
- 📌 **Subject:** SafeNotes Privacy

We aim to respond within 7 days. Because we hold no data about you, traditional "data access" or "data deletion" requests don't apply — there is nothing to retrieve or remove on our side. We're happy to answer questions about how the app works and verify our on-device-only architecture.

---

## 📍 App Information

- **App name:** SafeNotes
- **Package:** com.nocbook.app
- **Version:** 1.3.1 *(versionCode 9)*
- **Min Android:** 8.0 (API 26)
- **Target Android:** 15 (API 35)

---

## ⚠️ Disclaimer

SafeNotes is provided **as-is**, with no warranty. We've engineered the app for a specific threat model — opportunistic access to your phone, lost or stolen devices, snooping on the network — and we believe it addresses that model well. No software is invulnerable, however, and you remain responsible for safeguarding your PIN and your device.

If you forget your PIN, your data **cannot be recovered** — by you, by us, or by anyone. That's the security guarantee. Please keep at least one `.nbk` backup somewhere safe if your diary matters to you.

---

## 💙 Final Note

SafeNotes exists because some thoughts shouldn't live on someone else's server. We built the app we wanted for ourselves: private by default, offline by design, yours forever.

Thank you for trusting SafeNotes with your story.
