# Privacy Policy for CCRtools

**Last updated: April 11, 2026**

## 1. Overview

CCRtools ("the App") is an iOS application for closed-circuit rebreather (CCR) divers. This Privacy Policy explains how the App handles information when you use it.

The App is designed with privacy in mind: it does not collect, transmit, or share any personal data.

---

## 2. Data Collected and Stored

### Data stored locally on your device

The App stores the following data exclusively on your device:

- **O₂ sensor readings** – millivolt measurements you enter manually (ambient and oxygen values, battery levels, scrubber time). Stored using Apple's SwiftData framework in the App's private sandbox. This data never leaves your device.
- **Checklists** – checklist files you create, import, or download, stored as JSON files in the App's Documents folder. This data never leaves your device unless you explicitly share a file using the built-in share function.

No data is transmitted to the Developer or any third party.

### Data not collected

The App does **not** collect:

- Names, email addresses, or any other contact information
- Location data
- Device identifiers or advertising IDs
- Usage statistics or analytics
- Crash reports (outside of Apple's standard TestFlight / App Store mechanisms, which are governed by Apple's own privacy policy)

---

## 3. Network Access

The App accesses the internet only when you explicitly use the **Download Checklists** feature. In this case, the App fetches a list of available checklists and downloads selected files from the following server:

```
https://raw.githubusercontent.com/ksattler/ccrtools/main
```

This is a public GitHub repository. The request contains no personal data. GitHub's privacy policy applies to this connection: https://docs.github.com/en/site-policy/privacy-policies/github-general-privacy-statement

No other network requests are made by the App.

---

## 4. Text-to-Speech

The App optionally uses the device's built-in Text-to-Speech engine (Apple's AVSpeechSynthesizer) to read out checklist items. This processing happens entirely on your device. No audio or text is transmitted externally.

---

## 5. iCloud

The App does **not** use iCloud or any other cloud synchronization service. All data remains on your device.

---

## 6. Children's Privacy

The App does not knowingly collect data from anyone, including children under the age of 13.

---

## 7. Changes to This Policy

If this Privacy Policy is updated, the new version will be published at the same location with an updated date. Continued use of the App after changes constitutes acceptance of the updated policy.

---

## 8. Contact

If you have questions about this Privacy Policy, please contact:

**Kai-Uwe Sattler**
GitHub: https://github.com/ksattler/ccrtools
