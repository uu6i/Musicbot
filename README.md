# VAMPS MUSIC — GitHub auto-extract build

This repository is a small GitHub Actions launcher repository. It contains:
- `.github/workflows/android-apk.yml` — extracts the Android source archive and builds the APK.
- `VAMPS_MUSIC_SOURCE.zip` — the complete Android Gradle project.

## Use

1. Create a new GitHub repository named `vamps-music`.
2. Extract this outer ZIP on your phone.
3. Upload **both** `.github/workflows/android-apk.yml` (preserve its folders) and `VAMPS_MUSIC_SOURCE.zip` to the repository root. Also upload `README.md` if desired.
4. Commit the files to the `main` branch.
5. Open GitHub → repository → Actions → **Build VAMPS MUSIC APK** → **Run workflow**.
6. The workflow automatically extracts `VAMPS_MUSIC_SOURCE.zip` into `project/`, verifies the Gradle project files, and builds `:app:assembleDebug`.
7. Download the `VAMPS-MUSIC-debug` artifact from the completed workflow run.

A push to `main` also triggers a build automatically.

## Build configuration

- JDK 17
- Gradle 8.13 (installed by `gradle/actions/setup-gradle`)
- Android Gradle Plugin 8.11.1
- Kotlin 2.2.20
- Compile SDK 36

The workflow uses the installed Gradle executable, so the Android source ZIP does not need `gradlew` or `gradle-wrapper.jar`.

## Verification status

The outer archive structure, nested source archive contents, required Gradle files, workflow commands and YAML syntax have been checked. The workflow has not yet run on GitHub, so no successful APK build is claimed until Actions completes successfully.
