# Code Chase

Code Chase is a Flutter application for competitive programmers who want to track daily problem solving, measure progress, follow upcoming contests, and compare growth with friends.

It combines Firebase-backed practice tracking with Codeforces-powered contest insights in a single cross-platform app.

## Overview

Code Chase is built around four main workflows:

- Track daily practice problems with timing, tags, ratings, notes, and solving status
- Review progress through dashboard summaries and analytics charts
- Monitor upcoming Codeforces contests and inspect contest performance by handle
- Search for friends, add them, and view their progress snapshots

## Features

### Authentication

- Email and password registration
- Email verification during account setup
- Secure sign in with verification check
- Forgot password flow
- Password update screen

### Practice Tracker

- Add a problem with expected time and difficulty rating
- Start and stop an in-app timer while solving
- Save platform, URL, tags, notes, and final status
- Edit or delete saved entries
- Mark solved problems as favorites for later review
- Keep attempted problems visible for revisit

### Analytics

- Dashboard summary for today, this week, and the recent month
- Daily goal progress bar
- Weekly analytics with summary cards and charts
- Monthly analytics grouped into rolling multi-day phases
- Goal-aware tracking using values stored in Firestore

### Contest Tools

- Fetch upcoming contests from Codeforces
- Show live countdowns for contest start times
- Open contest pages directly from the app
- Analyze a Codeforces handle for:
  - total contests
  - unique problems solved
  - average solved per day
  - recent rating changes

### Social Features

- Search users by email
- Add friends
- Browse the friend list
- Open a friend detail page with summary, weekly analytics, and monthly analytics

### Profile Management

- Edit name
- Edit institution
- Edit programming handle
- Set daily goals
- Set weekly goals

## Tech Stack

- Flutter
- Dart
- Firebase Authentication
- Cloud Firestore
- Firebase Core
- HTTP
- `fl_chart`
- `url_launcher`

## Project Structure

```text
lib/
  main.dart                    App entry point and route registration
  firebase_options.dart        Local FlutterFire-generated configuration
  pages/                       Feature screens
  components/                  Reusable UI and analytics helpers
  services/                    API service classes

test/
  widget_test.dart             Default Flutter sample test

android/ ios/ web/
windows/ macos/ linux/         Platform runners
```

## Data Model

### `users` collection

The app reads and writes these fields in user documents:

- `name`
- `email`
- `institution`
- `programminghandle`
- `dailygoals`
- `weeklygoals`
- `friends`

### `problems` collection

The app reads and writes these fields in tracked problem documents:

- `name`
- `rating`
- `expectedTime`
- `actualTime`
- `platform`
- `url`
- `tags`
- `status`
- `notes`
- `isFavorite`
- `updatedAt`
- `user`

## Getting Started

### Prerequisites

Make sure you have:

- Flutter SDK installed
- Dart SDK available through Flutter
- A simulator, emulator, browser, or physical device
- A Firebase project if you want to run the app against your own backend

Verify your environment:

```bash
flutter doctor
```

### Install dependencies

```bash
flutter pub get
```

### Configure Firebase

Firebase client configuration files are intentionally not committed to the repository.

Generate your local configuration with FlutterFire:

```bash
dart pub global activate flutterfire_cli
flutterfire configure
```

For Android, also place your project-specific `google-services.json` in `android/app/`.

You should also enable these Firebase products:

- Authentication
- Cloud Firestore

### Run the app

```bash
flutter run
```

Examples:

```bash
flutter run -d chrome
flutter run -d android
flutter run -d windows
```

## Implementation Notes

- User profile data is stored in the `users` collection.
- Practice history is stored in the `problems` collection.
- Analytics are derived from `updatedAt`, `status`, and `actualTime`.
- Upcoming contests and contest performance are currently based on Codeforces APIs.
- Firebase options are expected to be generated locally for Android, iOS, macOS, Windows, and Web.
- Linux Firebase configuration is not currently implemented in `lib/firebase_options.dart`.

## Current Status

The app already includes a meaningful end-to-end feature set, but the repository still reflects an actively evolving project rather than a production-hardened release.

Current gaps worth noting:

- `test/widget_test.dart` is still the default Flutter sample test
- Package naming still uses `profileapp` in places
- Platform folders exist for multiple targets, but readiness may vary by platform

## Suggested Next Improvements

- Add real widget and integration tests
- Add screenshots or demo GIFs to the repository
- Document Firestore rules and expected indexes
- Clean up naming consistency between branding and package identifiers
- Expand contest integrations beyond Codeforces

## License

No license file is currently included in the repository. Add one explicitly if you plan to distribute or open-source the project.
