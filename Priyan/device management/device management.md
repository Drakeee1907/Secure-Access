# 03. Enterprise Device Management Concepts

Theory documentation for the Android secure-access / anti-theft application project.
Covers **Mobile Identity Management (MIM)**, **Enterprise Mobility Management (EMM)**,
and **Unified Endpoint Management (UEM)** — the three enterprise concepts that explain
how organizations manage a device's identity, applications, data, and security policies.

> Framing: these are not three unrelated acronyms — they're three related layers.
> - **MIM** → manages *identity*
> - **EMM** → manages the *mobile* workforce/device environment
> - **UEM** → manages the *entire endpoint ecosystem*

---

## 3.1 Mobile Identity Management (MIM)

### Definition
Mobile Identity Management (MIM) is the set of technologies and policies used to
identify, authenticate, authorize, and manage users and devices accessing
organizational resources through mobile devices.

**Core question:** *Who is this user/device, and what is it allowed to access?*

### Why MIM is needed
Mobile devices access corporate apps, email, cloud services, internal servers,
VPNs, databases, documents, APIs, and SaaS applications. Knowing a device is
"an Android phone" isn't enough — the system needs a chain of trust:

```
User Identity
     ↓
Device Identity
     ↓
Authentication
     ↓
Authorization
     ↓
Resource Access
```

### Major components

**1. User Identity** — identifies the person: username, employee ID, email, directory account.

**2. Device Identity** — identifies the actual device: enrollment identity, device
certificate, hardware-backed keys, managed-device identifier, app/device registration.
> Note: modern Android security systems generally avoid relying on hardware
> identifiers such as IMEI as the primary application identity mechanism.

**3. Authentication** — verifies the user is who they claim to be: password, PIN,
biometrics, OTP, security keys, digital certificates, OAuth/OIDC, SAML, MFA.

**4. Authorization** — determines what an authenticated user/device may do, e.g.:

```
Employee → Authenticated → Managed Android device
    ├── Corporate email        → ALLOWED
    ├── Corporate database     → ALLOWED
    └── Administrative console → DENIED
```

### MIM and Zero Trust
MIM aligns with Zero Trust Architecture: instead of *"the device is inside the
company network, therefore trust it,"* the model becomes *"verify the identity
and device before granting access."*

```
User → Authentication → Device Identity → Security State → Authorization → Corporate Resource
```

### Example for this project
The management server could maintain a record such as:

```
Device: A10291
User: Employee-42
Status: Online
Management: Active
Security: Compliant
Remote Lock: Allowed
Location Request: Allowed
Alarm: Allowed
```

Chain: `Device ID → Registered User → Authentication Token → Device Security Status → Allowed Commands`

---

## 3.2 Enterprise Mobility Management (EMM)

### Definition
EMM is a broader framework for managing mobile devices, applications, data, and
users within an organization.

**Core question:** *How does an organization securely manage employees' mobile
devices and the data/apps they use?*

MIM focuses on identity and access; EMM goes further, typically composed of:

```
                 EMM
                  │
      ┌───────────┼───────────┐
      │           │           │
     MDM         MAM         MIM
      │           │           │
 Device Mgmt   App Mgmt   Identity
      │           │           │
      └───────────┼───────────┘
                  │
                 MCM
                  │
             Content/Data
```
(Terminology varies by vendor — this is a conceptual model, not a strict spec.)

### 3.2.1 Mobile Device Management (MDM)
Controls the device itself: enrollment, configuration, security policies, password
requirements, screen-lock policies, encryption requirements, remote lock, remote
wipe, compliance, app installation, restrictions, certificate management.

```
Administrator → Management Server → Android Device
                                       ├── Lock
                                       ├── Wipe
                                       ├── Configure
                                       ├── Restrict
                                       ├── Monitor compliance
                                       └── Deploy application
```

### 3.2.2 Mobile Application Management (MAM)
Focuses on applications rather than the whole device — useful for BYOD scenarios.

```
Corporate App
     ├── Authentication
     ├── Data encryption
     ├── Copy/paste restrictions
     ├── Screenshot restrictions
     ├── App-level policies
     └── Remote data removal
```

```
Personal Android Phone
        ├── Personal WhatsApp
        ├── Personal Photos
        ├── Personal Games
        └── Corporate Application
                ├── Managed
                ├── Encrypted
                └── Controlled
```
The organization doesn't necessarily need control over the entire phone.

### 3.2.3 Mobile Content Management (MCM)
Deals with access to and protection of organizational content (documents, PDFs,
company files, cloud storage, shared files, databases) via encryption, access
control, download/sharing restrictions, remote removal, authentication.

### 3.2.4 EMM Architecture

```
                  IT Administrator
                         │
                ┌─────────────────┐
                │ Management      │
                │ Console         │
                └────────┬────────┘
                         │
                ┌─────────────────┐
                │ EMM Server      │
                └────────┬────────┘
                         │
          ┌──────────────┼──────────────┐
          ▼              ▼              ▼
        MDM            MAM            MIM
          │              │              │
          └──────────────┼──────────────┘
                         ▼
                  Android Device
```

---

## 3.3 Unified Endpoint Management (UEM)

### Definition
UEM is a centralized approach for managing and securing multiple types of
endpoints from a single management platform.

**Core question:** *How can an organization manage all of its endpoints using one
unified management system?*

```
                    UEM
                     │
       ┌─────────────┼─────────────┐
       │             │             │
    Android        Windows       macOS
       │             │             │
     iOS/iPadOS    Linux        Other
```

---

## 3.4 MIM vs EMM vs UEM

| Feature | EMM | UEM |
|---|---|---|
| Primary focus | Mobile devices | All endpoints |
| Android | ✅ | ✅ |
| iOS/iPadOS | ✅ | ✅ |
| Windows PCs | Limited/varies | ✅ |
| macOS | Limited/varies | ✅ |
| Application management | ✅ | ✅ |
| Mobile security | ✅ | ✅ |
| Device policies | ✅ | ✅ |
| Identity integration | ✅ | ✅ |
| Centralized endpoint management | Partial | Strong |
| Scope | Mobile-centric | Enterprise-wide |

```
                 UEM
                  │
       ┌──────────┴──────────┐
       │                     │
      EMM              Desktop Management
       │
 ┌─────┼─────┐
 │     │     │
MDM   MAM   MIM
```
Not a strict technical hierarchy — modern products overlap heavily — but a useful
conceptual model.

### Relationship summary

**MIM** — identity-centric — *Who are you?*
```
User → Authentication → Identity → Authorization
```

**EMM** — mobile-management-centric — *How do we securely manage mobile devices, apps and data?*
```
Identity + Device + Applications + Data → EMM
```

**UEM** — endpoint-centric — *How do we manage the organization's entire endpoint fleet?*
```
                    UEM
        ┌────────────┼────────────┐
        ▼            ▼            ▼
     Mobile       Desktop       Other
     Devices      Devices      Endpoints
```

---

## 3.5 Relevance to this Android security project

```
                    YOUR SYSTEM
                         │
             ┌───────────┴───────────┐
             │                       │
        Management Server       Android App
             │                       │
             ▼                       ▼
           UEM/EMM                 Device
             │
      ┌──────┼────────┐
      │      │        │
     MDM    MAM      MIM
      │      │        │
      │      │        └── User/device identity
      │      └─────────── App control
      └────────────────── Device control
```

The management server acts as the management plane:

```
                 ADMIN
                   │
          ┌─────────────────┐
          │ Management      │
          │ Server          │
          └────────┬────────┘
                   │
             Authentication
                   │
             Device Registry
                   │
             Policy Engine
                   │
             Command Engine
                   │
        ┌──────────┼──────────┐
        ▼          ▼          ▼
      Lock       Locate      Alarm
        │          │          │
        └──────────┼──────────┘
                   ▼
             Android Device
```

---

## 3.6 Management Plane vs Data Plane

- **Management Plane** — controls the device: enroll, authenticate, lock, wipe,
  configure, push policies, send commands, check compliance.
- **Data Plane** — carries the actual application/user data.

```
                Management Plane
                       │
                 Control/Policy
                       ▼
              ┌────────────────┐
              │ Android Device │
              └────────────────┘
                       ▲
                       │
                 User/Data Traffic
                       │
                  Data Plane
```
This distinction matters when designing the server architecture.

---

## 3.7 Device Enrollment

Before an organization can manage a device, it establishes a management relationship:

```
1. Device starts
2. User/company identifies device
3. Enrollment
4. Authentication
5. Management credentials established
6. Policies downloaded
7. Device becomes managed
8. Server can manage device
```

For Android enterprise environments, research **Android Enterprise** concepts:
- Managed Google Play
- Work Profile
- Fully Managed Device
- Dedicated Device
- Device Policy Controller (DPC)
- Android Management API

---

## 3.8 Policy Management

EMM/UEM systems maintain policies rather than sending arbitrary commands, e.g.:

```json
{
  "screen_lock": true,
  "minimum_password_length": 8,
  "encryption_required": true,
  "camera_allowed": false,
  "usb_data_transfer": false
}
```

```
Device State + Security Policy → Compliance Engine → Compliant / Non-compliant
```

---

## 3.9 Device Compliance

| Condition | State |
|---|---|
| Device enrolled | ✅ |
| Encryption enabled | ✅ |
| Screen lock enabled | ✅ |
| Required application installed | ✅ |
| OS version approved | ✅ |
| Device compromised | ❌ |

```
                    Compliance Engine
              ┌────────────┴────────────┐
              ▼                         ▼
          Compliant                 Non-compliant
              │                         │
              ▼                         ▼
        Normal access             Restrict access
```

---

## 3.10 Remote Commands (relevant to theft prevention)

```
Server
  ├── Lock device
  ├── Wipe corporate data
  ├── Change policy
  ├── Request device status
  ├── Trigger application action
  └── Locate device
```

**Critical distinction for this project:** EMM/UEM capabilities are not equivalent
to capabilities available to an ordinary Android application. Some privileged
management operations require Android Enterprise/device-management roles,
provisioning, or platform-supported APIs. This limitation should be explicitly
documented in the research and considered when scoping what the app can
realistically implement.

---

## 3.11 Next theory layer to study

To bridge these enterprise concepts with what's actually implementable on Android:
- Android Enterprise
- Device Policy Controller (DPC)
- Device enrollment / provisioning
- Android Management API

---

## Document Outline Reference

```
03. Enterprise Device Management Concepts
├── 3.1 Mobile Identity Management (MIM)
├── 3.2 Enterprise Mobility Management (EMM)
│   ├── 3.2.1 MDM
│   ├── 3.2.2 MAM
│   ├── 3.2.3 MCM
│   └── 3.2.4 EMM Architecture
├── 3.3 Unified Endpoint Management (UEM)
├── 3.4 MIM vs EMM vs UEM
├── 3.5 Relevance to this project
├── 3.6 Management Plane vs Data Plane
├── 3.7 Device Enrollment
├── 3.8 Policy Management
├── 3.9 Device Compliance
├── 3.10 Remote Commands
└── 3.11 Next theory layer to study
```
