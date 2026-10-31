# Bangal Traveller CRM — Android App

This is an Android WebView application connected to the **live** CRM:

**https://bangaltraveller.in/crm/login**

The app does not contain a separate CRM database or demo data. When a staff member signs in, the app displays the real CRM dashboard, records, modules, and actions permitted for that account. Any changes made to the web CRM are visible in the Android app when its pages are refreshed; no manual import is required.

## Unchanged app format / features

- Android WebView app layout, as in the supplied BookTripVibe project
- Login/session cookies retained
- Mobile rendering and Android Back navigation
- Upload file picker and regular file downloads
- Generated PDF/blob download handling
- Network error with Retry
- Geolocation permissions for CRM attendance/location features
- Cache cleared on each Android app version upgrade (cookies stay)

## Project configuration

| Setting | Value |
| --- | --- |
| App name | Bangal Traveller CRM |
| Application ID | `com.bangaltraveller.crm` |
| Login URL | `https://bangaltraveller.in/crm/login` |
| Minimum Android | Android 7.0 (API 24) |
| Target Android | API 35 |
| Version | 1.0.0 |

The visual app format is retained; Android metadata, displayed app name, code namespace, default download names, and launch URL are changed for Bangal Traveller. The supplied B launcher icon / app color palette are retained to avoid unrequested redesigns.

## Build an installable APK (GitHub Actions)

1. Create a GitHub repository and upload **the contents of this project directory to the repository root**, including the `.github` folder.
2. Under **Actions**, select **Build Android APK** and choose **Run workflow**. The workflow can also run after a push to `main`.
3. After the build finishes, download the **BangalTraveller-CRM-APK** artifact.
4. Extract and install `BangalTraveller-CRM.apk` on Android. You may need to allow the installation from the selected file manager/browser.
5. Log in using the credentials created in the Bangal Traveller CRM.

The existing workflow uses Gradle on GitHub, so Android Studio is not required for this path.

## Important notes

- This project is an **Android app source ZIP**, not a pre-built APK.
- `https://bangaltraveller.in/crm/login` was publicly accessible as a sign-in page on 31 Oct 2026.
- Authenticated CRM modules and permissions **cannot be verified without a valid CRM account**. Changes to the CRM PHP/backend or separate native screens are outside this wrapper.
- The Android wrapper shows the same data as the signed-in CRM website. It cannot independently bypass access controls, fetch unseen data, or change the CRM's server-side behavior.
- Building from this source requires Android SDK/Gradle or the included GitHub Actions workflow.

## Files where the CRM URL is configured

- `app/src/main/java/com/bangaltraveller/crm/MainActivity.java` — `HOME_URL`
- `app/src/main/AndroidManifest.xml` — Android app configuration
- `app/build.gradle` — Android application ID
- `.github/workflows/blank.yml` — APK build automation
