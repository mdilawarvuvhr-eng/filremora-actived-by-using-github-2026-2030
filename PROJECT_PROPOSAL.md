# Project Proposal & Technical Roadmap

## Project Title

**Free Trial System, Offline–Online Sync, and Google Drive Storage Integration**

## Purpose of This Document

This document clearly explains the required features, technical approach, and development roadmap. It can be used directly on **GitHub (README or proposal)** or shared with developers for implementation.

---

## 1. Free / Trial Usage System

### Objective

Allow new users to test **all features** of the application for learning and evaluation purposes without immediate payment.

### Requirements

- Trial duration: **7 or 14 days** (configurable from backend)
- Full access to all features
- No watermark during trial (optional but preferred)
- Trial should work **both online and offline**

### Technical Implementation

- User account-based trial activation
- Trial start date saved in:
  - Local storage (for offline validation)
  - Backend database (for security)
- Trial expiration logic:
  - App checks expiration date on startup
  - When expired, user is prompted to upgrade

### Edge Cases

- System clock manipulation prevention
- Trial status sync when device goes online

---

## 2. Offline + Online Sync System

### Objective

Allow users to work **offline without limitations**, and automatically sync data when internet becomes available.

### Requirements

- Full editing and project access in offline mode
- Automatic background sync when online
- Manual sync button (optional)

### Technical Implementation

- Local storage:
  - IndexedDB / SQLite (for web or desktop)
  - Store project files, metadata, and changes
- Sync engine:
  - Detect network availability
  - Upload pending changes to cloud storage
  - Resolve conflicts (latest version wins or user prompt)

### Sync Triggers

- App startup
- Network reconnect
- Manual sync action

---

## 3. Google Drive / Gmail Storage Integration (Core Feature)

### Objective

Use the **user’s own Google Drive storage** instead of limiting them to the app’s fixed 500 MB storage.

### User Flow

1. User clicks **“Connect Google Drive”**
2. Google permission screen appears
3. User grants access
4. App creates a dedicated folder in Drive
5. All projects are saved and synced to that folder

### Folder Structure

```text
Google Drive
 └── FilmoraProjects
     ├── Project_1
     ├── Project_2
     └── Exports
```

### Technical Stack

- **Google OAuth 2.0** – for secure authentication
- **Google Drive API** – for file operations
- Permissions scope:
  - Read access
  - Write access
  - App-specific folder access (preferred)

### Security Rules

- Access only after explicit user consent
- No access without login
- Tokens stored securely
- Refresh tokens handled properly

### Features

- Cloud sync ON/OFF toggle
- Manual disconnect option
- Storage usage shown to user

---

## 4. Multiple Projects & Unlimited Usage (Legal Model)

### Objective

Remove the need for license codes and replace with a **modern account-based system**.

### Requirements

- User login via:
  - Google account
  - Email and password
- Projects linked to user account
- Higher or unlimited project limit

### Benefits

- No illegal code usage
- Easy account management
- Scalable pricing model

---

## 5. Security & Privacy Standards

### Data Protection

- End-to-end encryption for sensitive data
- Secure token storage
- HTTPS for all communications

### User Control

- User can:
  - Revoke Google Drive access anytime
  - Delete their cloud data
  - Disable sync

### Compliance

- Follow Google API data usage policy
- No unauthorized data access

---

## 6. Development Roadmap

### Phase 1 – Planning & Setup

- Requirements finalization
- Tech stack selection
- Google Cloud project setup

### Phase 2 – Authentication & Trial System

- User login system
- Trial logic implementation
- Offline trial validation

### Phase 3 – Offline Storage Engine

- Local database setup
- Project save/load offline

### Phase 4 – Google Drive Integration

- OAuth 2.0 implementation
- Drive API integration
- Folder and file management

### Phase 5 – Sync Engine

- Auto-sync logic
- Conflict handling
- Manual sync option

### Phase 6 – Security & Testing

- Encryption checks
- Permission testing
- Offline/online edge cases

### Phase 7 – Deployment & Documentation

- Final build
- User documentation
- GitHub README and setup guide

---

## 7. Expected Benefits

- Reduced server storage cost
- Better user flexibility
- Legal and scalable architecture
- Professional-grade cloud workflow

---

## Conclusion

This roadmap provides a **legal, secure, and scalable** way to offer free trials, offline functionality, and unlimited cloud storage using the user’s own Google Drive. It improves user experience while reducing infrastructure cost for the company.
