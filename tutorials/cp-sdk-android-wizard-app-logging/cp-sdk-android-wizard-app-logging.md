---
author_name: Bruce Meng
author_profile: https://github.com/flyingfish162
title: See How Logging Can Be Used in Your Android Application
description: Explore how the logging component can help make deployed applications more supportable.
primary_tag: products>sap-cloud-platform-sdk-for-android
auto_validation: true
tags: [  tutorial>beginner, operating-system>android, topic>mobile, products>sap-cloud-platform-sdk-for-android, products>sap-cloud-platform ]
time: 15
---

## Prerequisites
- You completed [Try Out the SAP Cloud Platform SDK for Android Wizard](cp-sdk-android-wizard-app).

## Details
### You will learn
- How to use the Logging component to log messages
- How to change the log level
- How to upload and view logs in the SAP Cloud Platform Mobile Services cockpit

---

[ACCORDION-BEGIN [Step 1: ](Use the logging component)]

[OPTION BEGIN [Java]]

1.  In Android Studio, on Windows, press **`Ctrl+N`**, or, on a Mac, press **`command+O`**, and enter **`EntitySetListActivity`** to open `EntitySetListActivity.java`.

2.  On Windows, press **`Ctrl+F12`**, or, on a Mac, press **`command+F12`**, and enter **`onOptionsItemSelected`** to move to the `onOptionsItemSelected` method.

    Note that the following method contains two LOGGER statements:

    ```Java
    @Override
    public boolean onOptionsItemSelected(MenuItem item) {
        LOGGER.debug("onOptionsItemSelected: " + item.getTitle());
        switch (item.getItemId()) {
            case SETTINGS_SCREEN_ITEM:
                LOGGER.debug("settings screen menu item selected.");
                Intent intent = new Intent(this, SettingsActivity.class);
                this.startActivityForResult(intent, SETTINGS_SCREEN_ITEM);
                return true;

            default:
                return false;
        }
    }
    ```

    These messages will be logged when the app's log level is set to **Debug** or **Path** and the app's **Settings** menu item is opened.

[OPTION END]

[OPTION BEGIN [Kotlin]]

1.  In Android Studio, on Windows, press **`Ctrl+N`**, or, on a Mac, press **`command+O`**, and enter **`EntitySetListActivity`** to open `EntitySetListActivity.kt`.

2.  On Windows, press **`Ctrl+F12`**, or, on a Mac, press **`command+F12`**, and enter **`onOptionsItemSelected`** to move to the `onOptionsItemSelected` method.

    Note that the following method contains two LOGGER statements:

    ```Kotlin
    override fun onOptionsItemSelected(item: MenuItem): Boolean {
        LOGGER.debug("onOptionsItemSelected: " + item.title)
        return when (item.itemId) {
            SETTINGS_SCREEN_ITEM -> {
                LOGGER.debug("settings screen menu item selected.")
                val intent = Intent(this, SettingsActivity::class.java)
                this.startActivityForResult(intent, SETTINGS_SCREEN_ITEM)
                true
            }
            else -> false
        }
    }
    ```

    These messages will be logged when the app's log level is set to **Debug** or **Path** and the app's **Settings** menu item is opened.

[OPTION END]

[DONE]
[ACCORDION-END]

[ACCORDION-BEGIN [Step 2: ](Change the log level)]

1.  Navigate to the entity list screen and open the app's menu.

    ![Settings menu button](settings_menu_button.png)

2.  Choose **Settings**.

    ![Settings menu opened](settings_menu.png)

3.  Select **Log Level**.

    ![Log level settings option](log_level_option.png)

4.  Set the level to **Debug**.

    ![Debug log level option](debug_log_level_option.png)

5.  Navigate back to the entity list screen, then back into the **Settings** screen to see the effect of changing the log level.

    ![Settings menu opened](settings_menu.png)

6.  Examine the **Logcat** (Located at the bottom of Android Studio, click it and you can see logs). In the filter, add the name of the class that we are interested in seeing the log from: **`com.sap.wizapp.mdui.EntitySetListActivity`**.

    Notice that the messages were logged since the log level of the app was set to **Debug** or **Path**.

    ![Debug log level output](debug_log.png)

---

The SDK libraries also log output based on the app's log level.

1.  Change the filter to **`com.sap.cloud.mobile.foundation`**.

2.  Press **Back** to exit the app and you will see the logged lines from the foundation library.

    ![Debug log level output for foundation](debug_log_foundation.png)

[VALIDATE_1]
[ACCORDION-END]

[ACCORDION-BEGIN [Step 3: ](Upload and view the log)]

1.  Navigate back to the **Settings** menu in the app, and this time tap **Upload Log**.

    ![Upload log button in settings menu](upload_log_button.png)

    A Toast message is displayed confirming that the upload succeeded.

    ![Log upload succeeded](log_uploaded.png)

2.  In the Mobile Services cockpit, navigate to **Analytics** > **Logs** > **Technical Logs**.

    ![Analytics > Logs > Technical Logs](select_and_download_log.png)

3.  You should be able to see the log you just uploaded in the list of technical logs. You can inspect the log in the browser by clicking on its table entry, or you can download the text version by selecting it and clicking **Download**. If the log doesn't appear immediately, wait for a few moments, then click **Go** to refresh the view.

    ![View log](view_log.png)

4.  Additionally, you can access the logs locally on an emulator. You can browse the file system of an Android emulator using the **Device File Explorer** to view the log files as shown below, in **data** > **data** > **com.sap.wizapp** (or the package name of your project) > **files**.

    ![View logs in emulator](local_log_location.png)

5.  You can manage the initial log level of the application and the ability for mobile services to accept logs using the **Client Policies** feature, as shown below.

    ![Log Policy](client_policies.png)

6.  You can also set the log level of an individual registration in the **Management Cockpit**, as shown below. Click **User Registrations** and then select certain **Registration ID** to change **Log Settings**. In the pop-up, you can set the log level for this specific registration.

    ![User Registrations](log_settings.png)

    ![User Registration Log Settings](user_reg_log_setting.png)

>For further information on logging, see [Logging](https://help.sap.com/doc/c2d571df73104f72b9f1b73e06c5609a/Latest/en-US/docs/user-guide/foundation/logging.html).

Congratulations! You have explored how you can use the logging feature to debug or support a deployed application.

[DONE]
[ACCORDION-END]

---
