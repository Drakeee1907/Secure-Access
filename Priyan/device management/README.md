# Enterprise Device Management Concepts — Theory Docs

Theory reference material for the **Android secure-access / anti-theft
application** project. This section documents the enterprise device
management concepts that inform the app's design: how organizations
manage a device's identity, applications, data, and security policies.

## Contents

| File | Covers |
|---|---|
| [`03-enterprise-device-management-concepts.md`](./03-enterprise-device-management-concepts.md) | MIM, EMM, UEM — definitions, components, architecture, and how they relate to this project |

## Why this matters for the project

The app deals with device security, remote administration, theft prevention,
and enterprise-style control of an Android device. Three enterprise concepts
explain how this space normally works:

- **MIM (Mobile Identity Management)** — identity & access: *who is this
  user/device, and what can it do?*
- **EMM (Enterprise Mobility Management)** — mobile device/app/data
  management: *how do we manage devices, apps, and data securely?*
- **UEM (Unified Endpoint Management)** — the broader evolution of EMM,
  managing all endpoint types (mobile, desktop, etc.) from one platform.

These aren't three separate technologies — they're three layers:

```
MIM  → manages identity
EMM  → manages the mobile device/app/data environment
UEM  → manages the entire endpoint ecosystem
```

## Key takeaway for implementation

EMM/UEM platform capabilities (remote lock, wipe, policy enforcement, etc.)
are **not automatically available to an ordinary Android application**. Some
of these operations require Android Enterprise / device-management roles,
provisioning, or platform-supported APIs (Device Policy Controller, Android
Management API). This gap between "enterprise theory" and "what a normal app
can implement" is called out explicitly in the main doc and should guide the
project's technical scoping.

## Suggested next reading

- Android Enterprise
- Managed Google Play
- Work Profile / Fully Managed Device / Dedicated Device
- Device Policy Controller (DPC)
- Android Management API
