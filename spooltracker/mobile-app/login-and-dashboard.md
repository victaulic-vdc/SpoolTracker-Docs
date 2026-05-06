# Login & Dashboard

## Splash Screen and Opt-In

When the user opens SpoolTracker, a splash screen appears for a few seconds, then the application redirects to the **Opt-In screen**. The user must accept the terms and conditions to use the application. This is a one-time event.

<p>
  <img src="./images/splash-android.jpeg" width="200" alt="Splash screen on Android">
  <img src="./images/splash-ios.jpeg" width="200" alt="Splash screen on iOS">
</p>

<p>
  <img src="./images/optin-android.png" width="200" alt="Opt-in screen on Android">
  <img src="./images/optin-ios.png" width="200" alt="Opt-in screen on iOS">
</p>

## Login

The user can log in with a valid **Project code** or **Organization code**.

<p>
  <img src="./images/login-android.jpeg" width="200" alt="Login screen on Android">
  <img src="./images/login-ios.jpeg" width="200" alt="Login screen on iOS">
</p>

## Code Suggestions

The application provides the last successfully entered Project or Organization codes as suggestions, making it faster to log in to frequently used projects.

<p>
  <img src="./images/code-suggestions-android.jpeg" width="200" alt="Code suggestions on Android">
  <img src="./images/code-suggestions-ios.jpeg" width="200" alt="Code suggestions on iOS">
</p>

## Validation Warnings

The application displays a warning to the user if:

- The **Project code** entered is less than 8 characters
- The **Organization code** entered is less than 10 characters

<p>
  <img src="./images/validation-warning-android.png" width="200" alt="Validation warning on Android">
  <img src="./images/validation-warning-ios.jpeg" width="200" alt="Validation warning on iOS">
</p>

## Login Errors

The application displays an error when an incorrect Project or Organization code is entered.

<p>
  <img src="./images/login-error-android-1.png" width="200" alt="Login error on Android — loading">
  <img src="./images/login-error-android-2.png" width="200" alt="Login error on Android — project not found">
  <img src="./images/login-error-android-3.png" width="200" alt="Login error on Android — organization not found">
</p>

<p>
  <img src="./images/login-error-ios-1.jpeg" width="200" alt="Login error on iOS — loading">
  <img src="./images/login-error-ios-2.jpeg" width="200" alt="Login error on iOS — project not found">
  <img src="./images/login-error-ios-3.jpeg" width="200" alt="Login error on iOS — organization not found">
</p>

## Dashboard and Scan History

After a successful login, the application fetches the spool scan history for the entered Project or Organization code. On the home page, the user has the following options:

- **Refresh** — Pull down the history list to refresh it
- **Filter** — Filter options for scan history based on spool name and/or date range
- **Menu** — Contains two options: Settings and Logout

<p>
  <img src="./images/dashboard-android.jpeg" width="200" alt="Dashboard with scan history on Android">
  <img src="./images/dashboard-ios.jpeg" width="200" alt="Dashboard with scan history on iOS">
</p>

If there are no scans available in the history, the dashboard displays an empty state:

<p>
  <img src="./images/empty-history-android.jpeg" width="200" alt="Empty scan history on Android">
  <img src="./images/empty-history-ios.jpeg" width="200" alt="Empty scan history on iOS">
</p>

## Filtering Scan History

### Filter by Date Range

The user can filter scan history by tapping the date icon and selecting a date range.

<p>
  <img src="./images/date-filter-android.jpeg" width="200" alt="Date range filter on Android">
  <img src="./images/date-filter-ios.jpeg" width="200" alt="Date range filter on iOS">
</p>

### Filter by Spool Name

The user can also filter scan history by spool name.

<p>
  <img src="./images/spool-filter-android.jpeg" width="200" alt="Spool name filter on Android">
  <img src="./images/spool-filter-ios.jpeg" width="200" alt="Spool name filter on iOS">
</p>

### No Results

If no data is available based on the applied filters, the application displays an empty state:

<p>
  <img src="./images/no-filter-results-android.jpeg" width="200" alt="No filter results on Android">
  <img src="./images/no-filter-results-ios.jpeg" width="200" alt="No filter results on iOS">
</p>

## Settings

The user can access Settings by tapping the **menu icon** (&#8942;) and selecting **Settings**. In Settings, the user can:

- Give a **name to the device** for identification
- Set a **default status** for new scans
- Change the **maximum number of QRs** allowed in a multi-scan
- Change the **location settings**

<p>
  <img src="./images/settings-android.jpeg" width="200" alt="Settings on Android — menu">
  <img src="./images/settings-android-2.jpeg" width="200" alt="Settings on Android — settings screen">
</p>

<p>
  <img src="./images/settings-ios.jpeg" width="200" alt="Settings on iOS — menu">
  <img src="./images/settings-ios-2.jpeg" width="200" alt="Settings on iOS — settings screen">
</p>

## Logout

The user can log out by tapping the **menu icon** (&#8942;) and selecting **Logout**.

> **Warning:** If there are offline records that need to be synced, the application will **not** allow the user to log out. Ensure all offline records are synced before logging out.

<p>
  <img src="./images/logout-android-1.jpeg" width="200" alt="Logout on Android — step 1">
  <img src="./images/logout-android-2.jpeg" width="200" alt="Logout on Android — step 2">
  <img src="./images/logout-android-3.jpeg" width="200" alt="Logout on Android — step 3">
</p>

<p>
  <img src="./images/logout-ios-1.jpeg" width="200" alt="Logout on iOS — step 1">
  <img src="./images/logout-ios-2.jpeg" width="200" alt="Logout on iOS — step 2">
  <img src="./images/logout-ios-3.jpeg" width="200" alt="Logout on iOS — step 3">


