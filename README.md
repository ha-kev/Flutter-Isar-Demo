# FLutter Isar Demo App

A Flutter showcase demonstrating CRUD operations, reactive UI updates, and watcher streams on the Isar local database.

## Architecture Overview

- **UI & State**: [`lib/main.dart`](lib/main.dart) wires the `MaterialApp`, renders the dashboard widgets (`UtilsView`, `UserView`), and injects controllers via GetX.
- **Domain Model**: [`lib/user.dart`](lib/user.dart) defines the `User` collection annotated for Isar; the generated schema and query helpers live in [`lib/user.g.dart`](lib/user.g.dart).
- **Persistence Layer**: [`lib/user_repository.IsarDB`](lib/user_repository.dart) opens the database, wraps transactions, and exposes CRUD helpers.
- **Service Layer**: [`lib/user_service.UserService`](lib/user_service.dart) orchestrates repository calls, exposes observable lists/current user, and manages the optional `watchLazy` subscription.
- **External Data**: [`lib/user_fetcher.RandomUserFetcher`](lib/user_fetcher.dart) pulls mock users from randomuser.me or generates fallbacks for quick demos.

## Feature Highlights

- Create, read, update, delete, and bulk-delete users via the controls in [`lib/main.dart`](lib/main.dart).
- Auto-fill form fields when selecting list items thanks to the reactive bindings in [`lib/user_service.UserService`](lib/user_service.dart).
- Toggle the “Watcher” checkbox to subscribe/unsubscribe from live Isar updates using `watchLazy`.
- Fetch realistic seed data through [`lib/user_fetcher.RandomUserFetcher.fetchUser`](lib/user_fetcher.dart) to showcase asynchronous inserts.