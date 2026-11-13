# FocusLock

FocusLock is an Android-first focus timer and app-pausing MVP starter built with Kotlin and Jetpack Compose.

## Download the source

Download **[FocusLock_Android_Project.tar.xz](./FocusLock_Android_Project.tar.xz)** and extract it with 7-Zip (Windows) or your system archive utility. It contains the Android project, Node.js analytics API, Supabase schema, admin page, and setup/privacy guides.

After extraction, open the `FocusLock` folder (the one containing `settings.gradle.kts`) in Android Studio.

## Included in this MVP

- Daily focus schedule enabled by default after first-time setup: 6 hours, with a configurable start time.
- Optional, visible gradual timer plan: +1 hour per day up to 10 hours. It is off by default and never silently changes the user's timer.
- Selectable short-video/social app package list, including YouTube, Instagram, TikTok, Snapchat, Facebook, Threads, ShareChat, Moj and Josh.
- WhatsApp stays excluded from blocking in this version.
- Focus pause screen with an emergency exit and an optional +1-hour extension warning.
- One-time permission/protection onboarding.
- Optional anonymous install analytics, disabled by default.
- Supabase schema, rate-limited Node API, and an admin counts page.

## Important limitations

- This is an **MVP source starter, not a compiled or device-tested APK**. Build and test it in Android Studio on a real Android device before distribution.
- App pausing requires the user to explicitly enable FocusLock's Accessibility Service. The permission can be disabled by the user.
- Android does not provide a universal API to discover every app containing Reels/Shorts-style content. The app blocks known package names only.
- WhatsApp is not blocked; this MVP cannot reliably block chats while allowing only its call screen.
- Daily start uses an inexact Android alarm and may be delayed by the operating system.
- This is not a system firewall or an impossible-to-bypass lock. Do not advertise it as one.
- No app can guarantee that data will never leak. Analytics is opt-in and minimal, but the backend still needs secure HTTPS hosting, credential protection, retention rules, and security testing before public release.

## Build

1. Install Android Studio, Android SDK Platform 36, and JDK 17.
2. Extract the source archive.
3. Open the extracted `FocusLock` directory in Android Studio.
4. Allow Gradle sync to finish, then run the app on an emulator or Android phone.
5. On first launch, review the permission explanation and enable the Accessibility Service in Android Settings.
6. Test the pause screen and emergency exit with a non-essential app before using long sessions.

## Optional anonymous install-count backend

1. Create a Supabase project and run `backend/schema.sql` in its SQL editor.
2. Copy `backend/.env.example` to `.env` and fill in the Supabase URL, service-role key, and a long random admin token. Keep `.env` private.
3. From the `backend` folder, run `npm install` and `npm start`.
4. Deploy the API behind HTTPS. Configure the Android app's `TELEMETRY_BASE_URL` in `app/build.gradle.kts` to point to your API, then rebuild.
5. Analytics is off until the user opts in. It sends a random installation ID and app version, not names, contact details, selected apps, or screen content.

See `PRIVACY.md` inside the archive for the data-handling notes.
