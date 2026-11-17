[Tiếng Việt](./terms-of-service.md) | [English](./terms-of-service-en.md)

# Terms of Service

**Last updated:** November 17, 2026  

## 1. Acceptance of Terms

By downloading, installing, accessing, or using **Family Alarm** ("the App" or "the Service"), you confirm that you have read, understood, and agree to be bound by these **Terms of Service**, along with our [Privacy Policy](./privacy-policy-en.md) and [License & Attributions](./license-en.md). If you do not agree with any part of these terms, please stop using and uninstall the App.

---

## 2. Description of the Service

**Family Alarm** is an Android alarm clock utility designed for household alarm synchronization and personal alarms, offering:

- **Family Alarms:** Enables a **Representative** device to create, edit, enable/disable, or delete shared alarms that sync over the Internet to connected **Member** devices.
- **Personal Alarms:** Stored strictly locally on each user's device without sharing or affecting other family members.
- **Device & Role Management:** Links devices via a temporary pairing code (`FA-XXXXX-XXXXX-XXXXX`, valid for 5 minutes) or QR code requiring explicit approval from the Representative; supports **Representative** and **Member** access roles.
- **Offline Support:** Continues triggering locally saved alarms even without an active Internet connection.

---

## 3. Requirements & Device Permissions

To ensure alarms and synchronization work as expected, you must:

1. Use a compatible Android device (Android 8.0 / API 26 or higher) and provide Internet access when creating, joining, or syncing a family group.
2. Grant and maintain necessary system permissions according to your needs, including **Notifications**, **Exact Alarms**, **Show on Lock Screen (`USE_FULL_SCREEN_INTENT`)**, and optionally **Ignore Battery Optimizations**.
3. Verify alarm sound, vibration, and lock-screen behavior using **Test alarm ring** in Settings before relying on the App for important schedules.

---

## 4. Family Group Responsibilities & Security

1. **Consent of Participating Devices:** You agree to link only devices that you own or whose owners have consented to join the family alarm group. Changes to shared alarms ring on all connected devices where those alarms are enabled.
2. **Confidentiality of Pairing Codes & QR Codes:** Pairing codes and QR deep links (`familyalarm://join?...`) expire after **5 minutes**. Do not share them publicly. Representatives are responsible for verifying device names before approving any join request.
3. **Representative Role Assignment:** Representatives can modify family alarms, remove devices, and promote other devices to Representative role. Grant Representative access carefully.
4. **Leaving or Removing Devices:** Member devices may disconnect at any time via **Settings → Reset family setup**, and Representatives may remove devices from the **Devices** screen.

---

## 5. Prohibited Conduct

You agree not to:

- Use the App to harass, disturb, or remotely trigger unwanted alarms on someone else's device without consent.
- Reverse-engineer, decompile, disassemble, tamper with, extract source code, exploit vulnerabilities, spoof requests, or disrupt the synchronization backend (Firebase Realtime Database).
- Redistribute modified APK builds, commercially resell the App without permission, or abuse pairing codes or deep links for fraudulent or unlawful purposes.

---

## 6. Disclaimers & Limitation of Liability

1. **Not for Medical or Life-Safety Use:** Family Alarm is a household convenience and wake-up utility. **It is NOT designed for medical timing, medication alerts, emergency notification, or life/safety-critical operations.**
2. **Hardware & OS Dependencies:** Actual alarm execution depends on factors outside our control, including battery depletion, device power-off, third-party volume/Do-Not-Disturb overrides, aggressive OEM background/battery killers, revoked OS permissions, or network outages affecting remote sync.
3. **Local Data on Uninstall:** The App uses anonymous device tokens and disables Android auto-backup (`allowBackup="false"`). Uninstalling the App or clearing App storage removes local personal alarms and the current device pairing without recovery.
4. **"As-Is" Basis:** To the fullest extent permitted by applicable law, the App is provided *"AS IS"* and *"AS AVAILABLE"* without warranties of any kind, express or implied.

---

## 7. Intellectual Property

**Family Alarm** is **closed-source proprietary software**. All proprietary source code, visual assets, UI designs, custom graphics, brand marks, and the **Family Alarm** name are exclusively owned by **Jexopy** (excluding third-party open-source components governed by their respective licenses as detailed in [License & Attributions](./license-en.md)). Unauthorized copying, modification, or redistribution is prohibited.

---

## 8. Changes to Terms

Jexopy may update these Terms of Service from time to time to reflect app updates or legal requirements. The "Last updated" date at the top indicates the latest revision. Continued use after updates constitutes acceptance of the revised Terms.

---

## 9. Contact Information

For questions or support regarding these Terms of Service, please contact:

- **Developer:** JexOpy
- **Support Email:** superhien65@gmail.com
- **Website:** [https://jexopy.github.io/FamilyAlarm/](https://jexopy.github.io/FamilyAlarm/)
