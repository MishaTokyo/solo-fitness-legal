# Solo Fitness — Privacy Policy

**Effective date:** 19 June 2026
**Contact:** mikesot7@gmail.com

This Privacy Policy describes how the Solo Fitness mobile application
("Solo Fitness", "we", "us") collects, uses, and shares information from
the people who use it ("you").

By using Solo Fitness you agree to this policy. If you do not agree, do not
use the app.

---

## 1. Information we collect

Solo Fitness only collects data **you provide directly to the app**. We do
not buy data from third parties and we do not track you across other apps
or websites.

### 1.1 Account information (when you sign in)
- **Email address** — provided by you or by Google Sign-In.
- **Nickname / display name** — chosen by you during onboarding.

### 1.2 Fitness and health information
- **Body weight** — entered by you in onboarding and in Settings.
- **Workouts** — exercises, sets, repetitions, weights, dates, optional notes
  and duration that you log inside the app.
- **Workout templates** — reusable workout structures you save.
- **Body weight history** — every weigh-in you record.

### 1.3 Nutrition information (optional)
- **Meals** — foods, portion sizes, macronutrients, and the day/slot they
  belong to, that you log inside the app.
- **Custom foods** — foods you create yourself.
- **Nutrition goals** — daily calorie / macro targets and the wizard answers
  used to compute them.

### 1.4 Social information (optional)
- **Friendships** — pending and accepted friend requests between accounts.
  The friend's nickname is visible to you and yours is visible to them.

### 1.5 Information collected automatically
- **Camera** — used only when you open the barcode scanner in the nutrition
  tab to look up a food. Camera frames are processed on-device for barcode
  detection and are **never uploaded** anywhere. We do not record video or
  photos.
- **Device identifiers** — Google Play Services may collect anonymous
  install/crash identifiers required for app distribution; we do not link
  them to your account.

We do **not** collect: location, contacts, microphone audio, browsing
history, advertising IDs, or biometric data.

---

## 2. How we use information

We use your information only to operate the app:

- show you your profile, ranks, workouts, nutrition and friends;
- compute scores, XP, and rank changes from your training data;
- sync your data across your devices when you sign in;
- let you find friends by nickname (only when you search for them);
- diagnose crashes and improve reliability.

We do **not** use your data for advertising, profiling, or to train AI models.

---

## 3. How information is stored and shared

Your data is stored on [Supabase](https://supabase.com/) servers (PostgreSQL
+ object storage), under the developer's project. Connections use HTTPS/TLS.
Row-Level Security policies restrict access so that each user can only read
and write their own rows (and the rows of friendships where they appear).

We use the following third-party services:

| Service | Purpose | Data shared |
|---|---|---|
| Supabase (database & auth) | Account, sync, backup | All data listed in section 1 |
| Google Sign-In | Authentication | Email, Google account ID |
| OpenFoodFacts API | Look up barcodes / search foods | The barcode or query you typed (no account data) |
| Google Play / Apple App Store | App distribution and crash reports | Anonymous identifiers only |

We do **not** sell your personal information to anyone.

We do **not** share your personal data with anyone except as required by law
(valid subpoena, court order, or similar binding legal process).

---

## 4. Data retention

Your data is retained for as long as your account exists. You can:

- **Delete individual workouts / meals / friends** at any time from the
  relevant screen.
- **Erase profile and workouts** locally from Settings → Data → "Reset
  profile & workouts".
- **Delete your entire account** from Settings → Account → "Delete account".
  This triggers a server-side `delete_my_account()` call that:
  - removes your `auth.users` row;
  - cascade-deletes every row of yours in `profiles`, `workouts`,
    `workout_templates`, `nutrition_*`, `friendships`, `weight_log`, etc.;
  - clears local app storage.
  Deletion is **immediate and irreversible**. Operational backups may
  retain copies for up to 30 days, after which they are overwritten.

You can also request account deletion without installing the app — see the
"Delete your account" page at
`https://mishatokyo.github.io/solo-fitness-legal/account-delete.html`.

---

## 5. Your rights

Depending on where you live, you may have the right to:

- access the personal data we hold about you;
- ask us to correct it;
- ask us to delete it (the in-app "Delete account" button does this);
- export it (e-mail us at the address above; we will reply within 30 days).

European users (GDPR) and California users (CCPA) have these rights by law.
Children under 13 (or the equivalent age in your country) should not use the
app.

---

## 6. Security

- All network traffic uses TLS 1.2+.
- Passwords are stored hashed by Supabase Auth (bcrypt); we never see them.
- Session tokens are kept in encrypted device storage (`AsyncStorage`).
- We follow the principle of least privilege via Postgres Row-Level Security.

No system is 100 % secure. If you discover a vulnerability, please email
`mikesot7@gmail.com`.

---

## 7. Changes to this policy

If we materially change this policy we will update the "Effective date" at
the top and, where appropriate, notify you inside the app or by email. The
current version is always available at the URL where you found this page.

---

## 8. Contact

Questions about this policy or your data:
**mikesot7@gmail.com**
