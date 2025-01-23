# Expo Linking.getInitialURL() Inconsistent Null Return

This repository demonstrates a bug where `Linking.getInitialURL()` in Expo inconsistently returns `null`, even when a deep link is opened. The issue is particularly noticeable when the app is launched from the background or after being completely killed.

## Steps to Reproduce

1. Clone the repository.
2. Run the app on a physical device or emulator.
3. Open a deep link (e.g., `myapp://myroute`).
4. Observe the inconsistent behavior of `Linking.getInitialURL()`.  Sometimes it correctly returns the URL; other times, it returns `null`, especially after killing the app and restarting.

## Potential Causes

The root cause seems to be related to the timing of the app's initialization and the availability of the initial URL.  It might be an issue with how Expo handles the app's lifecycle or the way the underlying platform (iOS/Android) processes deep links.

## Proposed Solution

The solution involves adding a listener to the `Linking` events to handle the situation where `getInitialURL()` returns `null`.  By listening for URL changes, the app becomes more robust against this inconsistency.