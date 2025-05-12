# In Between - Flutter PWA Card Game

This archive contains the Flutter project files for the "In Between" PWA card game developed by Manus.

## Project Structure

The main application code is within the `in_between_game` directory.
- `lib/`: Contains all the Dart code.
  - `core/models/`: Data models (PlayingCard, UserModel, GameRoomModel).
  - `core/services/`: Firebase services (AuthService, FirestoreService).
  - `game_logic/`: Core game mechanics (InBetweenGame, DeckManager).
  - `presentation/screens/`: UI screens (Auth, Lobby, Splash, placeholder GameTable).
  - `main.dart`: Main application entry point with Firebase initialization.
- `web/`: Contains web-specific files, including `manifest.json` for PWA configuration.
- `pubspec.yaml`: Project dependencies, including Firebase SDKs.

## Setup Instructions

To run this project and connect it to your Firebase backend, please follow these steps:

1.  **Extract the Project:**
    *   Extract the `in_between_game_project.zip` archive to a location on your computer.

2.  **Set Up Your Firebase Project:**
    *   Go to the [Firebase Console](https://console.firebase.google.com/).
    *   Create a new Firebase project (or use an existing one).
    *   Within your Firebase project, you **must** register a **Web app**.
    *   Enable **Firebase Authentication**: Add the Email/Password sign-in method.
    *   Enable **Cloud Firestore**: Create a Firestore database. You can start in test mode for initial development, but remember to set up proper security rules for production.

3.  **Install FlutterFire CLI (if you haven't already):**
    *   Open your terminal/command prompt.
    *   Run: `dart pub global activate flutterfire_cli`

4.  **Configure Your Flutter App with Firebase:**
    *   Navigate to the root directory of the extracted `in_between_game` project in your terminal (e.g., `cd path/to/in_between_game`).
    *   Run: `flutterfire configure`
    *   This command will prompt you to log in to Firebase (if not already logged in) and select the Firebase project you created in step 2.
    *   It will automatically generate a `firebase_options.dart` file inside the `in_between_game/lib/` directory. This file is crucial as it contains the configuration details for your specific Firebase project.

5.  **Get Flutter Dependencies:**
    *   In the `in_between_game` project root directory, run: `flutter pub get`

6.  **Run the Application (PWA):**
    *   To run the game as a PWA in your browser (Chrome recommended for PWA features):
        `flutter run -d chrome --web-renderer html` (or `canvaskit` if you prefer, though `html` is often lighter for PWAs).
    *   The application should now connect to your Firebase backend.

7.  **Build the PWA for Deployment:**
    *   When ready to deploy, build the PWA:
        `flutter build web --pwa-strategy offline-first`
    *   This will create a `build/web` directory. You can deploy the contents of this directory to Firebase Hosting or any other static web hosting service.

## Firebase Studio

Once your app is connected to Firebase and deployed (e.g., to Firebase Hosting):
*   You can use **Firebase Studio** to visually manage your Firebase project's backend services.
*   This includes viewing/editing data in your Firestore database, managing authenticated users, monitoring analytics, and potentially building admin interfaces.
*   You don't upload the Flutter project code *into* Firebase Studio. Studio works with the live Firebase backend that your Flutter app communicates with.

## PWA Service Worker

The project includes a `manifest.json`. The `flutter build web --pwa-strategy offline-first` command will generate a service worker (`flutter_service_worker.js`) that provides basic offline caching. For more advanced offline capabilities or custom caching strategies, you might need to modify this generated service worker or implement your own.

## Important Notes

*   **Logo:** The game logo you provided (`1000000291.png`) is referenced in the design document but not yet fully integrated into all UI elements. You can find it in the `upload` directory of the provided zip (if I include it outside the main project folder) or you can place it in `in_between_game/assets/images/` and update the UI code accordingly.
*   **Game Table Screen:** The `GameTableScreen.dart` is currently a placeholder. The core game logic exists, but the UI for the actual gameplay (dealing cards, betting, showing results on the table) and its real-time synchronization with Firestore for multiplayer needs to be fully built out based on the services and models provided.
*   **2025 Updates:** The Firebase and Flutter dependencies in `pubspec.yaml` are recent versions. Always check for the latest stable versions when you continue development.

Good luck with your project!

