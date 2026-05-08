<div align="center">

<img src="assets/icon.png" width="80" height="80" style="border-radius: 16px" />

# Trackate

**Smart expense tracking and bill splitting — completely free.**

[![Play Store](https://img.shields.io/badge/Download_on-Play_Store-414141?style=for-the-badge&logo=googleplay&logoColor=white)](https://play.google.com/store/apps/details?id=com.svnate.trackate)
[![Website](https://img.shields.io/badge/Website-trackate.svnate.com-0078D4?style=for-the-badge&logo=google-chrome&logoColor=white)](https://trackate.svnate.com)

![Downloads](https://img.shields.io/badge/1%2C000%2B_downloads-grey?style=flat-square)
![Rating](https://img.shields.io/badge/5.0★_rating-FFD700?style=flat-square)
![Platform](https://img.shields.io/badge/Platform-Android-3DDC84?style=flat-square&logo=android&logoColor=white)
![Flutter](https://img.shields.io/badge/Flutter-02569B?style=flat-square&logo=flutter&logoColor=white)
![Firebase](https://img.shields.io/badge/Firebase-FFCA28?style=flat-square&logo=firebase&logoColor=black)

</div>

---

## What is Trackate?

Most expense apps demand constant manual entry — it gets ignored within a week. Trackate fixes this with **automatic expense detection**, reading payment notifications in real time so users never have to log manually.

Built for students and young users who want Splitwise-level bill splitting without the paywall. Every feature is free.

---

## Demo

<!-- Convert your .mp4 to GIF at ezgif.com and drop it in assets/ -->
<div align="center">

[![Trackate Demo](https://img.youtube.com/vi/azwJVYIfk9g/maxresdefault.jpg)](https://youtu.be/azwJVYIfk9g)

*Click to watch demo*

</div>
---

## Screenshots

<div align="center">
  <img src="assets/screen1.jpg" width="200" />
  <img src="assets/screen2.jpg" width="200" />
  <img src="assets/screen3.jpg" width="200" />
  <img src="assets/screen4.jpg" width="200" />
  <img src="assets/screen5.jpg" width="200" />
  <img src="assets/screen6.jpg" width="200" />
  <img src="assets/screen7.jpg" width="200" />
</div>

---

## The problem it solves

| Problem | How Trackate solves it |
|---|---|
| Manual entry is tedious and gets abandoned | Auto-detects expenses from payment notifications |
| Splitwise locks features behind paywall | Full bill splitting, completely free |
| Hard to track shared group expenses | Real-time multi-party debt balancing |
| No visibility into spending patterns | Per-category budgets and live insights |
| App unusable without internet | Offline state via SharedPreferences, syncs on reconnect |

---

## Key features

- **Automatic expense detection** — reads Android payment notifications, no manual entry needed
- **Real-time spending insights** — live dashboard with per-category breakdowns and budget tracking
- **Bill splitting** — split expenses across multiple people, track who owes what, settle balances
- **Group expense management** — shared groups with real-time sync across all members
- **Offline support** — local state via SharedPreferences, syncs to Firebase on reconnect
- **Push notifications** — Firebase Cloud Messaging for payment reminders and group activity
- **Cross-platform ready** — Flutter codebase targeting Android now, iOS in v2

---

## Architecture

**Pattern:** MVVM with Provider for state management
**Key challenge:** Keeping personal expenses, category budgets, and multi-party debt balances consistent across four interconnected Firestore streams — with atomic batch writes ensuring no partial state when any one piece changes.

---

## Tech stack

| Layer | Technology |
|---|---|
| Framework | Flutter (Dart) |
| Architecture | MVVM + Provider |
| Auth | Firebase Authentication |
| Database | Cloud Firestore |
| Notifications | Firebase Cloud Messaging |
| Auto-detection | Android Notification Listener Service |
| Native bridge | Flutter Method Channels |
| Local storage | SharedPreferences |

---

## Engineering decisions worth noting

**Why Flutter?**
Single codebase targeting Android and IOS — without sacrificing UI quality. Flutter's widget system made it straightforward to build the custom dashboard and budget visualisations without reaching for third-party UI libraries.

**Why Notification Listener over manual entry?**
The biggest reason expense apps fail is friction. If users have to open the app and type every time they spend, they stop after a week. Reading from Android notifications removes the friction entirely — the expense is logged before the user even puts their phone down. This required bridging into native Android via Flutter Method Channels, which was the most technically involved part of the build.

**Why atomic Firestore batch writes?**
With four interconnected data streams — personal expenses, category budgets, group balances, and the debt ledger — a failed partial write would leave the database in an inconsistent state. A user could show as owing money they'd already settled, or a budget could show overspent before the expense was confirmed. Batch writes treat all four updates as a single transaction: either all succeed or none do.

---

## Roadmap

- [x] Automatic expense detection via Notification Listener Service
- [x] Bill splitting and group expenses
- [x] Real-time budget and spending insights
- [x] Firebase sync with offline support
- [x] Push notifications via FCM

---

## About the developer

Built and maintained solo by **Sandesh Shinde** 

[![LinkedIn](https://img.shields.io/badge/LinkedIn-Sandesh_Shinde-0077B5?style=flat-square&logo=linkedin&logoColor=white)](https://www.linkedin.com/in/sandesh-shinde-b491aa246)
[![Email](https://img.shields.io/badge/Email-sandeshshinde2026%40gmail.com-D14836?style=flat-square&logo=gmail&logoColor=white)](mailto:sandeshshinde2026@gmail.com)

> This is a showcase repository. Source code is private as this is a live commercial app.
