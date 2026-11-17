[Tiếng Việt](./privacy-policy.md) | [English](./privacy-policy-en.md)

# Privacy Policy

**Last updated:** November 17, 2026  

## 1. Overview & Privacy Commitment

**Family Alarm** follows the principle of **data minimization**. The App **does not require personal account registration**, does not collect real names, email addresses, phone numbers, contacts, GPS location, photos/files, or advertising IDs, and **contains no third-party ads or behavioral tracking SDKs**.

This policy transparently explains what data is processed locally or synced online solely to deliver family alarm functionality, alongside our [Terms of Service](./terms-of-service-en.md).

---

## 2. Information Processed & Purpose

### 2.1. Locally Stored Data (`SharedPreferences`)
Stored exclusively within the App's private storage on your device (with Android cloud auto-backup disabled via `allowBackup="false"`):

| Data Item | Purpose | Shared Off-Device? |
| :--- | :--- | :--- |
| **Random Device ID (`deviceId`)** (`dev_...`) | Identifies this app installation within a family group and handles join requests. Not tied to hardware IMEI or serial numbers. | Sent only when creating or joining a Family group. |
| **Device Model Name (`Build.MODEL`)** | Displays a recognizable label in the family Devices list (e.g., `SM-A176B`). | Visible only to members of the same Family group. |
| **Personal Alarms** | Stores time, label, repeat schedule, active duration, and toggle state for private alarms. | **Never** uploaded or shared. |
| **App Preferences** (theme mode, color palette, language, ringtone URI/title, volume, vibration, snooze duration) | Preserves your chosen UI and alarm preferences. | **Never** uploaded. |
| **Firebase Anonymous Auth Credentials** (`refreshToken`, `authUid`) | Authenticates anonymous sync requests with Firebase for your family group. | Exchanged securely only with Google Firebase Auth. |

### 2.2. Cloud-Synced Data (Only when using Family Sync online)
When you create an online family group or join via pairing code / QR code, the following data is transmitted over **HTTPS** to **Google Firebase Realtime Database** (`asia-southeast1` Singapore region):

1. **Family Group Metadata:** Random `familyId`, member `deviceId`, `deviceName` (`Build.MODEL`), anonymous `authUid`, access role (`REPRESENTATIVE` or `MEMBER`), and last-seen timestamp (`lastSeenMs`) to show Online/Offline status.
2. **Family Alarms:** Hour, minute, alarm label (up to 120 chars), repeat days, active duration, and enabled status.
3. **Sync Event Notice (`lastChangeEvent`):** Brief event title/message and timestamp to notify linked devices of alarm/role changes.
4. **Ephemeral Pairing Records (`pairingCodes`, `joinRequests`):** Temporary 5-minute pairing codes and pending join requests awaiting Representative approval.

> **Offline Mode:** Choosing **"Continue offline"** keeps all alarms strictly on your device without uploading anything to Firebase.

---

## 3. Android Permissions & Usage

| Permission | Reason Needed |
| :--- | :--- |
| `INTERNET` & `ACCESS_NETWORK_STATE` | Sync family alarms, pairing codes, and device membership with Firebase, and display in-app legal/license pages in the WebUI. |
| `POST_NOTIFICATIONS` | Show ringing alarm notifications and family alarm sync updates. |
| `SCHEDULE_EXACT_ALARM` / `USE_EXACT_ALARM` | Trigger alarms reliably at the exact scheduled minute. |
| `USE_FULL_SCREEN_INTENT` | Show the ringing screen above the lock screen when an alarm fires. |
| `FOREGROUND_SERVICE` & `FOREGROUND_SERVICE_MEDIA_PLAYBACK` | Keep alarm playback and countdown active reliably while ringing. |
| `WAKE_LOCK` & `VIBRATE` | Wake the screen and vibrate during an active alarm. |
| `RECEIVE_BOOT_COMPLETED` | Reschedule saved alarms and sync after device reboot or app update. |
| `REQUEST_IGNORE_BATTERY_OPTIMIZATIONS` *(optional)* | Helps prevent OS background throttling from delaying alarms or sync. |

The App **does not** request Camera, Microphone, Location, Contacts, or external Storage permissions.

---

## 4. Third-Party Services

**Family Alarm** relies solely on **Google Firebase** (**Firebase Anonymous Authentication** and **Firebase Realtime Database**) as cloud infrastructure for family synchronization. All connections use **HTTPS / TLS encryption**.

- Google Privacy Policy: [https://policies.google.com/privacy](https://policies.google.com/privacy)

We **do not** sell, rent, or share user data with advertisers, data brokers, or unrelated third parties.

---

## 5. Data Retention & Deletion

1. **Local Data:** Deleted immediately when you reset setup in Settings, clear app storage, or uninstall the App.
2. **Pairing Codes & Join Requests:** Pairing codes expire automatically after **5 minutes** and are deleted upon approval, rejection, or expiration check.
3. **Leaving or Removing a Device:**
   - Removing a member in **Devices** immediately deletes that member entry and join request from Firebase.
   - Resetting setup on a Member device (`Settings → Reset family setup`) removes that device from the family group on Firebase (when online) and clears local session state.
4. **Shared Family Group Persistence:** If a Representative uninstalls locally without removing other members first, shared `familyId` data may remain in Firebase while active members continue syncing, or can be removed upon request via the contact email below.

---

## 6. User Rights & Control

You can view and edit alarms/device roles inside the App, revoke any Android permission in **Settings → App Permissions** or system Settings, reset or leave a family group at any time, or contact `superhien65@gmail.com` to request manual deletion of a family group record.

---

## 7. Children's Privacy

Family Alarm does not knowingly collect personally identifiable information from anyone, including children. Linking a child's device into a family alarm group is initiated and managed by a parent or guardian (the Representative). Parents or guardians may contact us anytime to request removal of group records.

---

## 8. Changes to This Policy

JexOpy may update this Privacy Policy as the App evolves or to meet legal / Google Play requirements. Updates will be posted with a revised "Last updated" date.

---

## 9. Contact Us

If you have questions or privacy requests, please contact:

- **Developer:** JexOpy
- **Email:** superhien65@gmail.com
- **Website:** [https://jexopy.github.io/FamilyAlarm/](https://jexopy.github.io/FamilyAlarm/)
