# AlFirma 🌱

**AlFirma** is a cross-platform mobile app that connects the agricultural community: farmers,
merchants, workers, transporters, experts and veterinarians. Users can sell products, offer or
hire services, chat with each other, and check their crops for diseases with an on-device AI model.

Built with **Flutter** and **Firebase**, available in **Arabic, French and English**.

## Features

### Marketplace

- Publish products with photos, price and description; browse, search and filter them.
- Product and service detail pages with zoomable full-screen images.
- Likes, comments and offers on listings, plus following other users.
- Search history kept on the device.

### Agricultural services

- Dedicated sections for **consultation, expertise, hiring workers, equipment rental, repairs and
  transportation**.
- **User roles** (Farmer, Merchant, Worker, Transporter, Expert, Veterinarian): a user requests a
  role, an admin validates it, and the user is notified automatically.

### AI plant disease detection

- Take or pick a photo of a leaf and get a diagnosis **directly on the phone** (no internet
  needed for the prediction).
- A **TensorFlow Lite** image-classification model recognises **31 classes** (diseases and healthy
  leaves) for apple, cherry, corn, grape, peach, potato, strawberry and tomato.

### Messaging and notifications

- Real-time one-to-one chat between buyers, sellers and service providers, with read status.
- **Push notifications** (Firebase Cloud Messaging) for new messages, likes, comments, offers,
  follows and role approvals, sent by **Cloud Functions** triggered by Firestore changes.

### Accounts and experience

- Email/password and **Google Sign-In** (Firebase Authentication), profile picture and profile
  editing.
- **Multilingual** UI (Arabic by default, with French and English) and right-to-left layout.
- Light/dark theme, onboarding screens, settings, security and contact pages.

## Tech stack

| Layer            | Technology                                                       |
| ---------------- | ---------------------------------------------------------------- |
| Mobile app       | Flutter (Dart), Provider for state management                    |
| Backend          | Firebase: Authentication, Cloud Firestore, Storage, App Check    |
| Server logic     | Firebase Cloud Functions (Node.js), triggered by Firestore events |
| Notifications    | Firebase Cloud Messaging + flutter_local_notifications           |
| AI               | TensorFlow Lite (`tflite_flutter`), on-device inference          |
| Localization     | `intl` / ARB files (ar, fr, en)                                  |

## Project structure

```
lib/
├── Back_end/          Data models (User, Products) and Firestore mapping
├── Front_end/
│   ├── Authentication/  Login, sign-up, profile picture
│   ├── Home/            Home, explore, add product, AI disease detection, notifications
│   ├── Item detaille/   Product and service details, image viewer
│   ├── Meseges/         Conversations and chat
│   ├── Profile/         Profile, edit profile, settings
│   ├── ServicesF/       Consultation, expertise, workers, rent, repairs, transport
│   └── Providers/       Language and theme providers
├── Services/          Notification service
├── l10n/              Translations (ar, fr, en)
└── main.dart
functions/             Cloud Functions for notifications and role validation
assets/models/         TensorFlow Lite plant disease model
```

## Getting started

Requirements: Flutter SDK (Dart ≥ 2.17), a Firebase project, Android Studio or Xcode.

```bash
git clone https://github.com/B3LM0/AlFirma-App.git
cd AlFirma-App
flutter pub get
flutter run
```

To use your own Firebase project, run `flutterfire configure` to regenerate
`lib/firebase_options.dart`, then deploy the functions:

```bash
cd functions
npm install
firebase deploy --only functions
```

## Team

AlFirma is a team project built by four developers. See the
[contributors](https://github.com/B3LM0/AlFirma-App/graphs/contributors) page.
