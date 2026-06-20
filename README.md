# Sparkon EV Charging Slot Booking Platform

Sparkon is a premium, high-integrity EV Charging Slot Booking and Fleet Management web system constructed using standard Vite, React, TypeScript, and Google Firebase (Authentication & Cloud Firestore). It leverages a midnight black atmospheric visual interface designed to matches high-voltage charger environments.

---

## Technical Architecture

The platform is designed around a fully secure, role-based architecture. If standard hot-credentials or live Firebase client variables are unresolved at runtime, the application gracefully initializes a dual-persistence client offline sandbox. This allows complete dashboard testing immediately, retaining mock profiles and bookings inside the subscriber browser local storage.

### Technology Stack
- **Framework Core**: React (Functional hooks with TypeScript type safety)
- **Dev-Server Bundle**: Vite + TSX
- **Aesthetic Styling Engine**: Tailwind CSS
- **Database Backend**: Google Cloud Firestore (Dual synchronised offline fallback option)
- **Identity Gateway**: Firebase Authentication (Supporting Email & Password and Google sign-ins popup flow)
- **Illustration Assets**: Custom cinematic AI and premium open layouts
- **Operational Icons**: Lucide React

---

## Firestore Database Collection Schemes

```
users:
  uid: string (Doc ID)
  name: string
  email: string
  role: "user" | "admin"
  createdAt: string (date-time)

bunks:
  bunkId: string (Doc ID)
  name: string
  address: string
  mobile: string
  mapLink: string (Google map URL)
  latitude: number
  longitude: number
  createdBy: string
  createdAt: string (date-time)

slots:
  slotId: string (Doc ID)
  bunkId: string
  date: string (YYYY-MM-DD)
  time: string (HH:MM 24h)
  chargerType: "CCS2" | "Type 2" | "CHAdeMO" | "DC Fast"
  price: number
  status: "available" | "booked" | "maintenance"
  createdAt: string (date-time)

bookings:
  bookingId: string (Doc ID)
  userId: string
  bunkId: string
  slotId: string
  status: "active" | "cancelled"
  chargingStatus: "Pending" | "Charging" | "Completed"
  bookedAt: string (date-time)
```

---

## Features & Core Modules

### 1. Immersive Landing Page
- **Power Forward Hero**: Translucent glass navigation bars paired with cinematic white sports car representations and high-voltage charging poles.
- **Dynamic Fleet Map Grid**: Live station search displaying bunk vacancies before signing up.
- **Interactive Benefits**: Diagrams pointing to high-rate CCS2 lines, transparency pricing metrics, and renewable wind integration commitments.
- **How It Works**: 3-step operations guides (Search -> Check vacancy -> Reserve slots).

### 2. Symmetrical Role-Based Sign In
- Dynamic Email form with validations paired with instant Google authentication popup workflows.
- User accounts are bootstrapped using registration selectors (EV Driver vs Fleet Admin).
- *Strict Rule Verification*: Pre-configured developer mail **meghanarp29@gmail.com** automatically overrides to System Admin role on boot.

### 3. EV Admin Control Center
- **Bento Indicators**: Overview of fleet numbers, charging slots count, active sessions, and revenue calculations.
- **Station Deployer**: Complete forms and coordinates fields to create and manage active bunks.
- **Slot Grid Generator**: Interactive date/time/plug schedulers with specific rates per minute settings.
- **Live Monitor**: Active charging tables. Admins can update current status (`Pending` -> `Charging` -> `Completed`) or cancel bookings with one click to restore slot vacancies.

### 4. EV Driver Space
- **Radius Search**: Neighborhood stations list filterable down by street or names.
- **Real-Time Timetables**: Direct layout grids showing open, booked, or offline charging cords.
- **Live Power Delivery Status Loop**: Implements real-time visual battery meters that pulse during voltage delivery animations and complete automatically as admins toggle states.
- **Secure Reservation Logs**: Historical logs with the option to cancel upcoming appointments to release ports.

---

## Firebase Setup Guidelines

To transition from Offline Sandbox Mode to Live Cloud, follow these steps:

1. Create a Firebase project in the [Firebase Console](https://console.firebase.google.com).
2. Enable **Firestore Database** and **Authentication** under the Build panel:
   - Within Authentication, activate the **Email/Password** provider and the **Google** Identity standard.
3. Register a Web application inside your Firebase project. Copy the resulting configuration block.
4. Replace the values inside the `/firebase-applet-config.json` file:
   ```json
   {
     "apiKey": "YOUR_ACTUAL_API_KEY",
     "authDomain": "YOUR_AUTH_DOMAIN",
     "projectId": "YOUR_PROJECT_ID",
     "storageBucket": "YOUR_STORAGE_BUCKET",
     "messagingSenderId": "YOUR_SENDER_ID",
     "appId": "YOUR_APP_ID",
     "firestoreDatabaseId": "(default)"
   }
   ```
5. Deploy Security Rules: Write the project rules block in the `/firestore.rules` file in your repository, and run deploy scripts through CLI:
   ```bash
   firebase deploy --only firestore:rules
   ```

---

## How to Run locally

1. Clone current workspace or export files and run dependencies setup:
   ```bash
   npm install
   ```
2. Run Vite dev server bound on default container rules:
   ```bash
   npm run dev
   ```
3. Open standard test URLs: `http://localhost:3000` to inspect.

---

## GitHub Workflow & Deployment
- Deployments to production branches trigger automatic GitHub Action compilation.
- Continuous delivery bundles Vite assets into `dist/` directory, pushing static outputs safely onto target hosting configurations.

---

## Future Scope Roadmaps
- Integrate actual GPS Geolocation distance calculations.
- Incorporate Stripe billing loops to allow drivers to securely charge credit cards after `Completed` power loop cycles.
- Integrate vehicles diagnostics metrics using standard API adapters.
