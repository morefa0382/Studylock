# StudyLock status

Last updated: 2026-11-17

## Build status
- Cloud build (GitHub Actions): NOT YET RUN. No APK exists until a build succeeds.
- Tested on the Samsung Galaxy S24 FE: NO.

## Stages
| Stage | Feature | State |
|---|---|---|
| 1 | Project skeleton, Material 3 theme, 4-tab navigation, cloud build workflow | Written, not yet built |
| 2 | Persistent timed sessions (no cancel, survives reboot) | Not started |
| 3 | Installed-app list and app blocking (AccessibilityService) | Not started |
| 4 | Daily usage quotas | Not started |
| 5 | Website blocking (local VPN, DNS) | Not started |
| 6 | Emergency unlock with 30-minute delay | Not started |
| 7 | Bypass and reboot testing | Not started |
| 8 | Final APK | Not started |

## Known decisions
- Built against Android API 36 with Android Gradle Plugin 8.13 (it supports up to API 36.1).
  The app still runs on Android 17. Moving to API 37 needs Android Gradle Plugin 9 and is planned after the pipeline is proven.
- The signing key in `app/debug.keystore` is a personal debug key kept in the repository so new builds install over old ones.
  It is not secure enough for publishing the app publicly.
