# MediFollow

MediFollow (internal package name `careloop`) is a Flutter/Firebase Android app for a follow-up care system serving patients, doctors and admins. It provides the app architecture, navigation, theming and Firebase wiring; product features are being added incrementally.

## Tech stack

- Flutter (Dart `>=3.4.0 <4.0.0`), Android target
- Riverpod for dependency injection and state management
- GoRouter for navigation
- Firebase: Auth, Cloud Firestore, Cloud Messaging, Storage, Analytics, Crashlytics
- Clean Architecture by feature with an MVVM presentation layer

## Getting started

Prerequisites: Flutter stable, Android SDK, a Firebase project and the FlutterFire CLI.

```sh
flutter pub get
flutterfire configure      # generates lib/firebase_options.dart
flutter run
```

### Firebase configuration

The repository ships placeholder values. Replace them with your own project's:

- `lib/firebase_options.dart` - regenerate with `flutterfire configure`.
- `android/app/google-services.json` - copy `android/app/google-services.json.example` and fill in your values (download the real file from the Firebase console).

Do not commit real keys for production projects. `android/local.properties` is machine specific and is git-ignored; Flutter creates it on first build.

## Quality checks

```sh
flutter analyze
flutter test
```

The same commands run in CI (`.github/workflows/ci.yml`) on every push to `main` and every pull request.

## Project layout

```text
lib/
  app/                 App bootstrap, routing, theme
  core/                Config, errors, Firebase providers, result type, utils
  shared/              Reusable view model base and adaptive widgets
  features/
    auth/              Login, registration, OTP, splash
    patient/           Patient home
    doctor/            Doctor home
    admin/             Admin slice
    history/ notifications/ profile/ reminder/
```

Each feature follows `data` / `domain` / `presentation` (pages, viewmodels, widgets).

**Author:** [Saizul Amin](https://saizul.com)
