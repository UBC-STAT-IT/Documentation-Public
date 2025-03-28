# Nextcloud Migration/Startup Guide

Nextcloud (cloud.stat.ubc.ca) is a cloud storage service that provides Statistics users with 50GB of file storage. If you aren't already using Nextcloud, you can get started with the [startup guide](#startup-guide).

We will be migrating to a new Nextcloud server as the old Nextcloud server's operating system is reaching end of life status. This document aims to assist Statistics staff, faculty, and students with the transition over to the new server.

For context:
- cloud.stat.ubc.ca is the new Nextcloud server running RHEL9
- owncloud.stat.ubc.ca is the old Nextcloud server running RHEL7 (end of life)

owncloud.stat.ubc.ca will point to new server cloud.stat.ubc.ca after the migration.

During the migration window, access to Nextcloud will be temporarily suspended. Any files already synced locally to your device should still be accessible, however files will not be synced to or downloaded from the server.

After the migration, users who were already using Nextcloud before the migration should follow the [after migration steps](#after-migration-steps) to confirm that your Nextcloud client is able to sync with the new server.

If you encounter any issues with the guides below, contact STAT IT at help@stat.ubc.ca for assistance.

# Table of Contents
- [After Migration Steps](#after-migration-steps)
- [Startup Guide](#startup-guide)
- [Upgrade Nextcloud Client](#upgrade-nextcloud-client)
- [Add another Account](#add-another-account)

## After Migration Steps

**These steps are only for those who were already using Nextcloud before the migration**

The Statistics IT team will notify all users when the migration has completed through e-mail and Slack. Once you receive the notification, please follow the steps below if you were using Nextcloud before the migration.

1\. Go to your system tray and click the Nextcloud icon to open the Nextcloud window.

**Note**: The icon could also look like this &nbsp; ![Alt text](../images/Nextcloud/image2.png)

![Alt text](../images/Nextcloud/image1.png)

**If you already upgraded your client before the migration, skip to step 4.**

2\. Click the small downwards pointing arrow beside your name and then click Settings.

![Alt text](../images/Nextcloud/image3.png)

3\. Click the **General** menu option and click the **Check Now** button beside the "Automatically check for updates" checkbox.

![Alt text](../images/Nextcloud/image4.png)

Follow the prompts on screen to install the latest version of the Nextcloud client. Reboot your device once completed.

4\. Open the app like in step 1, if the window says you're "Offline" (example below) then you likely need to log back in to your account.

![Alt text](../images/Nextcloud/image8.png)

Click the small downwards pointing arrow beside your name and then the ellipses beside your account on the dropdown menu.

![Alt text](../images/Nextcloud/image6.png)

Click "Log In". 

![Alt text](../images/Nextcloud/image7.png)

A browser window will open, follow the prompts in the browser window to log back in to Nextcloud.

5\. Open the app like in step 1 and click the **Sync now** button in the window, wait for your files to sync and check if the window eventually shows a green checkmark and **All synced!**. 

If you do not receive the **All synced!** message, you can try re-installing Nextcloud from [here](https://nextcloud.com/install/) under **Download for Desktop**, try [adding another account](#add-another-account),  or contact Statistics IT support help@stat.ubc.ca.

**Note**: If you find the macOS 12+ installer does not work, try the macOS Virtual Files 12+ installer.

6\. Go to the Nextcloud folder located on your device and check that your files can be opened, renamed, and saved. If so, then your client has been migrated successfully.

## Startup Guide

**This section is only for those who are installing Nextcloud for the first time.**

1\. Install Nextcloud from [here](https://nextcloud.com/install/) under **Download for Desktop**. Reboot your system once the installer is finished.

**Note**: If you find the macOS 12+ installer does not work, try the macOS Virtual Files 12+ installer.

2\. For Mac, open the Nextcloud app under **Finder -> Applications**. For Windows, search for Nextcloud in the Start Menu search bar.

3\. A window will prompt for log in. Use **cloud.stat.ubc.ca** as the "Server address" and it will redirect to a browser to authenticate and grant access to the app. Use your StatNet username and password as credentials. 

4\. Once access is granted, return to the Nextcloud app window. To choose a different location for the Nextcloud folder on your device, click "Choose different folder". Otherwise, click the "Connect" button to complete setup.

5\. Go to your system tray and click the Nextcloud icon to open the Nextcloud window. Confirm that your account is syncing successfully. 

**Note**: The icon could also look like this &nbsp; ![Alt text](../images/Nextcloud/image2.png)

![Alt text](../images/Nextcloud/image1.png)

6\. Go to the Nextcloud folder on your device (through Finder on Mac or File Explorer on Windows) and test that you are able to save, delete, and rename files.

## Upgrade Nextcloud Client

1\. Go to your system tray and click the Nextcloud icon to open the Nextcloud window.

**Note**: The icon could also look like this &nbsp; ![Alt text](../images/Nextcloud/image2.png)

![Alt text](../images/Nextcloud/image1.png)

2\. Click the small downwards pointing arrow beside your name and then click Settings.

![Alt text](../images/Nextcloud/image3.png)

3\. Click the **General** menu option and click the **Check Now** button beside the "Automatically check for updates" checkbox.

![Alt text](../images/Nextcloud/image4.png)

Follow the prompts on screen to install the latest version of the Nextcloud client. Reboot your device once completed.


## Add another Account

**For beta testers or troubleshooting only**

1\. Go to your system tray and click the Nextcloud icon to open the Nextcloud window.

**Note**: The icon could also look like this &nbsp; ![Alt text](../images/Nextcloud/image2.png)

![Alt text](../images/Nextcloud/image1.png)

2\. Click the small downwards pointing arrow beside your name and then click **Add account**.

![Alt text](../images/Nextcloud/image5.png)

3\. A window will prompt for log in. Use **cloud.stat.ubc.ca** as the "Server address" and it will redirect to a browser to authenticate and grant access to the app. Use your StatNet username and password as credentials. 

4\. Once access is granted, return to the Nextcloud app window. To choose a different location for the Nextcloud folder on your device, click "Choose different folder". Otherwise, click the "Connect" button to complete setup.

5\. Go to your system tray and click the Nextcloud icon to open the Nextcloud window. Confirm that your account is syncing successfully. 

6\. Go to the Nextcloud folder for the new account on your device (through Finder on Mac or File Explorer on Windows) and test that you are able to save, delete, and rename files.
