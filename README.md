# 💬 Private

> **A full-featured, multimedia-enabled social platform built with a hybrid architecture.**
> *Developed: [Year] | Status: Archived (Educational Project)*

![Firebase](https://img.shields.io/badge/firebase-%23039BE5.svg?style=for-the-badge&logo=firebase) ![JavaScript](https://img.shields.io/badge/javascript-%23323330.svg?style=for-the-badge&logo=javascript&logoColor=%23F7DF1E) ![Android](https://img.shields.io/badge/Android-3DDC84?style=for-the-badge&logo=android&logoColor=white)

## 📖 Overview

**Private** represents a significant evolution from my earlier ephemeral messaging tools. Unlike simple text-stream apps, this project was engineered to handle **persistent user identities**, **multimedia blobs**, and **relational contact discovery** within a NoSQL environment.

It features a custom-built hybrid interface that bridges native device capabilities (Camera, Gallery, File System) with a serverless Firebase backend.

---

## 📸 Interface & Capabilities

| **Real-Time Chat & Dark Mode** | **Multimedia Pipeline & Preview** |
|:---:|:---:|
*| <img src="./images/chat_ui_sample.png" width="250" /> | <img src="./images/media_preview.jpg" width="250" /> |*
| *Supports inline image rendering, dark mode UI, and instant message synchronization.* | *Custom pre-upload stage for compressing and confirming media (images/video) before blob storage commitment.* |

*(Note: Replace `chat_ui_sample.png` with your chat screenshot and `media_preview.jpg` with the Aarti preview image)*

---

## 🚀 Key Features

### 🔐 1. Identity & Onboarding
- **Mobile-First Auth:** Implemented phone number authentication as the primary unique identifier (UID).
- **Profile Management:** Users can set persistent profile pictures and status updates, stored in Cloud Storage and synced across sessions.

### 🔍 2. Contact Discovery Engine
- **Search by Number:** Solved the NoSQL "search" limitation by indexing user profiles by mobile number keys.
- **Smart Sync:** Users can discover friends by searching their mobile numbers, mimicking the contact resolution flow of industry-standard apps like WhatsApp.

### 📹 3. Multimedia Handling
- **Blob Storage Strategy:** Instead of clogging the Realtime Database with Base64 strings, I implemented a proper storage pipeline:
    1.  **Capture/Select:** Native bridge to OS Gallery/Camera.
    2.  **Compression:** Client-side optimization.
    3.  **Upload:** File sent to Firebase Storage buckets.
    4.  **Reference:** Download URL injected into the chat stream.

---

## 🛠️ Technical Stack

* **Frontend Logic:** JavaScript (ES6)
* **UI/Rendering:** Custom CSS/JS (influenced by p5.js creative coding principles)
* **Backend:** Firebase Realtime Database (JSON Tree)
* **Storage:** Firebase Cloud Storage (Images/Videos/Docs)
* **Wrapper:** Android Native WebView (Hybrid Architecture)

---

## 🧠 Engineering Challenges Solved

### The "NoSQL Relational" Problem
* **Challenge:** How to allow User A to "add" User B without a relational `JOIN` table?
* **Solution:** Designed a denormalized data structure where user relationships are stored as nested objects under `users/{uid}/contacts`, allowing O(1) retrieval of friend lists without expensive queries.

### Latency vs. Quality
* **Challenge:** Sending high-res images (like the Aarti capture shown above) instantly.
* **Solution:** Implemented the "Preview" state (seen in screenshots). This allows the UI to remain responsive while the heavy upload happens in the background, updating the chat bubble state from "Sending..." to "Sent" only upon storage confirmation.

---

## 📜 Context
*This project was developed independently during my high school years as an exploration into full-stack mobile architecture.*
