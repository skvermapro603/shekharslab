# Lovable CMS – Custom Code Setup

This repository contains **custom code, configuration, and extensions** for a Lovable-powered CMS project.  
It is designed to work alongside the Lovable visual builder while allowing advanced control over **roles, permissions, admin access, and integrations**.

---

## 🚀 Project Overview

- Built with **Lovable CMS**
- Custom role-based access (Admin / Editor / Viewer)
- Optional backend integration (Supabase, API, etc.)
- Version-controlled via GitHub
- Safe to extend without breaking Lovable core features

---

## 📂 Project Structure
├── lovable.json # Lovable project configuration
├── accessConfig.js # Role & permission definitions
├── permissionChecker.js # Access guards and helpers
├── admin/
│ ├── AdminDashboard.js # Custom admin UI logic
│ └── routes.js # Admin-only routes
├── api/
│ └── cms.js # Custom CMS API handlers
├── utils/
│ └── auth.js # Auth helpers
└── README.md


> Folder names may vary depending on how you structure your Lovable project.

---

## 🔐 Roles & Permissions

This project supports custom CMS roles:

| Role   | Permissions |
|------|-------------|
| Owner | Full access, billing, user management |
| Admin | Publish, manage users, manage content |
| Editor | Create & edit content |
| Viewer | Read-only access |

Permissions are defined in `accessConfig.js` and enforced using `permissionChecker.js`.

---

## 🛠️ Custom Code Usage

### Example: Role Configuration

```js
// accessConfig.js
export const roles = {
  owner: ['*'],
  admin: ['publish', 'edit', 'delete', 'view'],
  editor: ['edit', 'view'],
  viewer: ['view'],
};

// permissionChecker.js
export function hasPermission(userRole, action) {
  const permissions = roles[userRole] || [];
  return permissions.includes('*') || permissions.includes(action);
}
