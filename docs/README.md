# Appium APK test workflow

This project is configured to run Android Appium smoke tests against the APK in this directory.

## Local setup

1. Install prerequisites:
   - Node.js 20+
   - Android SDK + emulator
   - Java 17
   - `ANDROID_HOME` or `ANDROID_SDK_ROOT` environment variable pointing to your Android SDK
2. Install dependencies:
   ```bash
   npm install
   npm run appium:driver
   ```
3. Run tests:
   ```bash
   npm run test:e2e
   ```

## Configuration

- `APK_PATH` (optional): absolute or relative path to an APK file.  
  If not set, the test runner auto-detects a single `.apk` file in the project root.
- `APP_PACKAGE` (optional but recommended): expected Android package name for stronger validation.

Example:

```bash
APK_PATH=./Jibble-v2.52.3.210100(210100)-flavorProduction-release-unsigned-signed.apk APP_PACKAGE=com.example.app npm run test:e2e
```

## CI/CD (GitHub Actions)

Workflow file: `.github/workflows/appium-android.yml`

- Boots an Android emulator (API 34)
- Installs dependencies and Appium UiAutomator2 driver
- Runs `npm run test:e2e`

Set repository variable `APP_PACKAGE` in GitHub for package assertion in CI.
