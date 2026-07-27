# Solo Fitness — Privacy Policy

**Effective date:** 27 July 2026  
**Contact:** mikesot7@gmail.com

This Privacy Policy describes how the Solo Fitness mobile application
("Solo Fitness", "we", "us") collects, uses, and shares information from
the people who use it ("you").

By using Solo Fitness you agree to this policy. If you do not agree, do not
use the app.

Related documents:

- [Terms of Service](./terms-of-service.html)
- [Delete your account](./account-delete.html)

---

## 1. Information we collect

Solo Fitness collects data you provide in the app, data created while you use
features (including optional AI features), and limited technical data needed to
run the service. We do not buy personal data from data brokers and we do not
track you across other apps or websites for advertising.

### 1.1 Account information

- **Email address** — from Google Sign-In or Sign in with Apple (production).
  Development builds may also use email/password for testing.
- **Authentication identifiers** — provider account IDs needed to keep you
  signed in (for example a Google account ID or Apple user identifier via
  Supabase Auth).
- **Nickname / display name** — chosen by you during onboarding (and later via
  paid nickname changes).
- **Profile basics** — gender, age, height, and body weight entered during
  onboarding or Settings.
- **Preferences** — language/locale and cosmetic theme choices.

### 1.2 Fitness and health information

- **Workouts** — exercises, sets, repetitions, weights, dates, optional notes,
  duration, training mode, and related progress data you log.
- **Workout templates** — reusable workout structures you save (including
  templates suggested by the AI coach that you choose to keep).
- **Body weight history** — weigh-ins you record.
- **Ranks / XP / streaks** — scores derived from your training activity.
- **Other training logs** — additional activity you log in the app (for
  example swimming sessions), when you use those features.

This is **user-entered** fitness data. Solo Fitness is **not** a medical device
and does **not** read Apple Health / HealthKit or Google Fit by default.

### 1.3 Nutrition information (optional)

- **Meals** — foods, portion sizes, macronutrients, meal slot/day, and optional
  free-form notes.
- **Custom foods** — foods you create.
- **Nutrition goals** — calorie/macro targets and wizard answers used to
  compute them.
- **Meal photo id** — when you log a meal from a photo, a `photoId` may sync
  with the meal entry so the UI can group items. The image thumbnail itself
  stays on your device (see §1.6).

### 1.4 Social and messaging information (optional)

- **Friendships** — friend requests and accepted friendships. Nicknames (and
  optional supporter badge) can be visible to friends.
- **Profile photo (optional)** — if you upload an avatar, the image is stored on
  our servers and shown to friends in chat, lists, and the calendar. You can
  remove it in Settings.
- **Presence / last activity** — when you use social features, a last-seen
  timestamp may be visible to accepted friends (for example to show online
  status).
- **Direct messages and group chat messages** — content you send to other users.
- **Co-workout / live training sessions** — participants, session state, and
  related workout data shared for that session.
- **Referral codes / invites** — if you use referral features.

### 1.5 Purchases and wallet

- **Diamond balance, ledger, unlocks, and feature credits** — in-app currency
  and entitlements stored on our servers.
- **Purchase metadata** — product identifiers, transaction events, and
  entitlement state received from RevenueCat / the app stores so we can credit
  diamonds. We do **not** receive your full card number; payments are handled
  by Google Play or the Apple App Store.

### 1.6 Device permissions and media

You can deny any permission; related features will simply be limited.

| Permission / media | How we use it |
|---|---|
| **Camera** | Barcode scanning for foods; optional meal photos for AI analysis. Barcode frames are processed for detection and are **not** stored as a video library. |
| **Photo library** | Optional: pick a meal photo to analyze, or a profile photo to upload. |
| **Microphone + speech recognition** | Optional: dictate meal notes. Speech is converted to text by the **on-device / OS speech recognizer**. We do **not** upload or store raw audio recordings. |
| **Profile photo upload** | Optional: photo you choose for your profile. Stored on our servers (Supabase Storage) and shown to friends when you use social features. Removed when you delete the photo or your account. |
| **Meal photo thumbnails** | Compressed thumbnails are stored **only on your device** (about 30 days) for the day view. They are **not** synced as image files to our database. |
| **AI meal photo request** | When you run AI meal-photo analysis, a compressed image is sent **for that request** to our backend and then to the AI provider (see §3). |
| **Local notifications** | Optional: rest-timer alerts on your device when a set rest period ends (including lock-screen / Live Activity on iOS where supported). Scheduled locally; we do **not** receive notification content on our servers. |

### 1.7 Product analytics (first-party)

We may store lightweight **product event** records in our database (for example
onboarding completed, workout finished, shop purchase, shop redeem). These are
used to operate and improve the product. They are **not** used for advertising
networks or cross-app tracking.

### 1.8 What we do not collect for advertising

We do **not** collect contacts, precise location, browsing history across other
apps, or advertising IDs for ads. We do not run a third-party ad SDK in Solo
Fitness.

---

## 2. How we use information

We use your information to:

- create and secure your account;
- show your profile, ranks, workouts, nutrition, wallet, and social features;
- sync your data across devices when you are signed in;
- let friends find you by nickname (when they search) and power chat /
  co-workout features you choose to use;
- process diamond purchases and redeem shop items / AI credits;
- run optional AI features you trigger (meal-note formatting, meal-photo
  analysis, AI coach);
- look up foods via public food databases when you search or scan barcodes;
- diagnose reliability issues and understand product usage via first-party
  analytics events;
- respond to support requests you send by email.

We do **not** sell your personal information.  
We do **not** use your data for third-party advertising.  
We do **not** use your content to train **our own** AI models. When you use AI
features, request content is processed by third-party AI providers solely to
generate the feature response (see §3).

---

## 3. How information is stored and shared

### 3.1 Primary storage

Your account and app data are stored on [Supabase](https://supabase.com/)
(PostgreSQL, Auth, Storage for profile photos, Edge Functions, and related
infrastructure) under the developer's project. Connections use HTTPS/TLS. Access
is restricted with Row-Level Security so users generally only read/write their
own rows, plus rows required for friendships, chats, and co-workouts they
participate in.

### 3.2 Third-party services

| Service | Purpose | Data involved |
|---|---|---|
| **Supabase** | Auth, database, file storage (avatars), sync, Edge Functions, product analytics events | Account and app data described in §1 |
| **Google Sign-In / Google** | Authentication on Android; Google Play distribution & billing | Email / Google account identifiers; store purchase metadata |
| **Sign in with Apple / Apple** | Authentication on iOS; App Store distribution & billing | Email (if you choose to share it) / Apple user identifier; store purchase metadata |
| **RevenueCat** | In-app purchase receipt validation and purchase events for diamond packs | App user id, product ids, purchase/entitlement events |
| **OpenRouter** (AI gateway) | Powers optional AI features via our Supabase Edge Functions | Content you submit for that feature (see below) |
| **Open Food Facts** | Barcode lookup and food search | Barcode or search query you entered (no account password) |

**Optional AI features (only when you use them):**

1. **AI meal-note formatting** (`format-meal-note`) — your typed/dictated meal
   text is sent to OpenRouter to clean it into a food list.
2. **AI meal-photo analysis** (`analyze-meal-photo`) — a compressed meal image
   (and locale hints) is sent to OpenRouter vision models to estimate foods and
   macros.
3. **AI coach** (`ai-trainer`) — your chat messages and, when needed for the
   request, relevant profile / workout / nutrition context are sent to
   OpenRouter so the coach can answer.

AI requests go **Solo Fitness app → our Supabase Edge Function → OpenRouter →
upstream model provider**. Providers process the request to return a result.
Their retention and logging are governed by their own policies. Do not put
highly sensitive information into AI prompts if you do not want it processed
that way.

### 3.3 Other users

If you use social features, limited profile information (including optional
profile photo and last-seen status) and the messages or session data you share
become visible to the people you interact with (friends, chat members,
co-workout participants).

### 3.4 Legal requests

We may disclose information if required by law (valid subpoena, court order, or
similar binding legal process).

---

## 4. Data retention and deletion

- Data is kept while your account exists, unless a feature says otherwise
  (for example on-device meal photo thumbnails are purged after about 30 days).
- You can delete individual workouts, meals, friends, and similar items from
  the relevant screens.
- Local reset options in Settings (where available) clear data on that device;
  they may not delete everything on the server.
- **Delete account** — Settings → Account → "Delete account" runs a server-side
  deletion that removes your auth user and cascades deletion of associated app
  data (profile, workouts, templates, nutrition, friendships, chats you own as
  applicable, weight log, wallet-related rows, profile photos, etc.) and clears
  local app storage. Deletion is **irreversible**. Operational backups may retain
  copies for up to about 30 days before being overwritten.
- Without the app: follow
  [Delete your account](https://mishatokyo.github.io/solo-fitness-legal/account-delete.html).

Purchases made through Google Play or the App Store remain subject to the
store’s records and refund rules even after account deletion.

---

## 5. Your rights

Depending on where you live, you may have the right to access, correct, delete,
or export personal data we hold about you (including under GDPR / CCPA where
applicable). Use in-app deletion where possible, or email
**mikesot7@gmail.com**. We aim to reply within 30 days.

Children under 13 (or the equivalent minimum age in your country) should not
use the app.

---

## 6. Security

- Network traffic uses TLS.
- Auth is handled by Supabase Auth; we do not see Google or Apple passwords.
- Session tokens are stored on the device (AsyncStorage / app storage).
- Database access uses Row-Level Security and least privilege where applicable.

No system is 100% secure. Report vulnerabilities to **mikesot7@gmail.com**.

---

## 7. International processing

Our hosting and subprocessors may process data in regions where they operate
(including outside your country of residence). By using the app you understand
that your information may be transferred to those regions with appropriate
safeguards provided by those services.

---

## 8. Changes to this policy

If we materially change this policy we will update the "Effective date" at the
top and, where appropriate, notify you in the app or by email. The current
version is always available at the URL where you found this page.

---

## 9. Contact

Questions about this policy or your data:  
**mikesot7@gmail.com**
