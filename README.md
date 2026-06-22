# FoodHub — Frontend

<div align="center">

![Next.js](https://img.shields.io/badge/Next.js-15-000000?style=for-the-badge&logo=next.js&logoColor=white)
![React](https://img.shields.io/badge/React-19-61DAFB?style=for-the-badge&logo=react&logoColor=black)
![Tailwind CSS](https://img.shields.io/badge/Tailwind_CSS-4-06B6D4?style=for-the-badge&logo=tailwindcss&logoColor=white)
![Radix UI](https://img.shields.io/badge/Radix_UI-161618?style=for-the-badge&logo=radix-ui&logoColor=white)
![Socket.io](https://img.shields.io/badge/Socket.io-010101?style=for-the-badge&logo=socket.io&logoColor=white)
![Google Maps](https://img.shields.io/badge/Google_Maps-4285F4?style=for-the-badge&logo=google-maps&logoColor=white)
![Docker](https://img.shields.io/badge/Docker-2496ED?style=for-the-badge&logo=docker&logoColor=white)

A modern, responsive food delivery web application built with Next.js 15 and React 19 — featuring real-time delivery tracking, multi-role dashboards, and Google Maps integration.

</div>

---

## Table of Contents

- [Features](#features)
- [Tech Stack](#tech-stack)
- [App Structure](#app-structure)
- [Role-Based Dashboards](#role-based-dashboards)
- [Getting Started](#getting-started)
- [Environment Variables](#environment-variables)
- [Docker](#docker)

---

## Features

- **Multi-Role Authentication** — Separate dashboards for customers, restaurant owners, delivery personnel, and admins
- **OTP Verification** — Email and SMS one-time password flow for secure registration
- **Google OAuth** — Sign in with Google support
- **Restaurant Discovery** — Browse and search restaurants, view menus with nutritional info
- **Cart & Checkout** — Persistent cart with Stripe payment integration and cash on delivery option
- **Real-Time Delivery Tracking** — Live map view of the delivery courier's GPS location via Socket.io
- **Google Maps Integration** — Interactive location picker and delivery route visualization
- **Restaurant Owner Dashboard** — Manage restaurants, menus, orders, and availability in real time
- **Admin Dashboard** — System-wide management of users, restaurants, orders, and transactions
- **Delivery Dashboard** — Couriers accept, update, and complete deliveries with live location broadcasting
- **Responsive Design** — Fully mobile-friendly UI built with Tailwind CSS and Radix UI

---

## Tech Stack

| Category | Technology |
|---|---|
| Framework | Next.js 15.2.4 (App Router) |
| UI Library | React 19 |
| Styling | Tailwind CSS 4 |
| Components | Radix UI (headless, accessible primitives) |
| Maps | Google Maps API, Leaflet Routing Machine |
| Real-Time | Socket.io Client |
| State | React Context API + Custom Hooks |
| HTTP Client | Native Fetch API |
| Containerization | Docker |

---

## App Structure

```
app/
├── page.jsx                          # Landing page
├── login/                            # Login
├── register/                         # Registration
├── verify-otp/                       # OTP verification
├── forgot-password/                  # Password reset
├── home/                             # Home after login
└── dashboard/
    ├── user/                         # Customer dashboard
    │   ├── page.jsx                  # Overview
    │   ├── restaurants/              # Browse restaurants & menus
    │   ├── orders/                   # Order history & detail
    │   ├── checkout/                 # Checkout flow
    │   └── [id]/track/              # Live delivery tracking map
    ├── restaurant/                   # Restaurant owner dashboard
    │   ├── my-restaurants/           # Manage restaurants
    │   ├── create/                   # Create new restaurant
    │   ├── edit/[id]/               # Edit restaurant
    │   ├── menu/                     # Menu management
    │   ├── orders/                   # Incoming orders
    │   └── settings/                 # Restaurant settings
    ├── delivery/                     # Delivery person dashboard
    └── admin/                        # Admin dashboard
        ├── users/                    # Manage users
        ├── restaurants/              # Manage all restaurants
        ├── orders/                   # All orders
        └── transactions/             # Payment transactions

components/
├── delivery-map.jsx                  # Live delivery map (Leaflet)
├── delivery-tracker.jsx              # Real-time tracking component
├── location-picker.jsx               # Google Maps location selector
├── google-maps-loader.jsx            # Maps API loader
├── admin-sidebar.jsx                 # Admin navigation
└── ui/                               # Radix UI components

context/
└── auth-context.jsx                  # Auth state + role flags

hooks/
├── use-auth.js                       # Authentication hook
├── use-cart.js                       # Cart management (localStorage)
├── use-mobile.js                     # Responsive detection
└── use-toast.js                      # Toast notifications

lib/
├── api.js                            # Auth & order API calls
├── restaurant-api.js                 # Restaurant API calls
├── delivery-api.js                   # Delivery API calls
└── utils.js                          # Utility helpers
```

---

## Role-Based Dashboards

### Customer (`/dashboard/user`)
Browse restaurants, add items to cart, place orders with card or cash, and track deliveries live on a map.

### Restaurant Owner (`/dashboard/restaurant`)
Create and manage restaurants, build menus with nutritional details, toggle item availability, and manage incoming orders through their full lifecycle.

### Delivery Person (`/dashboard/delivery`)
View assigned orders, accept deliveries, broadcast GPS location in real time, and mark orders as picked up or delivered.

### Admin (`/dashboard/admin`)
Full system oversight — view and manage all users, restaurants, orders, and payment transactions across the platform.

---

## Getting Started

### Prerequisites

- [Node.js 18+](https://nodejs.org/)
- npm
- The [FoodHub Backend](https://github.com/IT22056320/food-delivery-system-backend) running (locally or via Kubernetes)

### Install & Run

```bash
git clone https://github.com/IT22056320/food-delivery-system-frontend.git
cd food-delivery-system-frontend
npm install
```

Copy the environment template and configure your values:

```bash
cp .env.template .env.local
```

Start the development server:

```bash
npm run dev
```

Open [http://localhost:3000](http://localhost:3000) in your browser.

### Build for Production

```bash
npm run build
npm start
```

---

## Environment Variables

Create a `.env.local` file in the project root with the following variables:

```env
# Backend API base URL (Kubernetes ingress or local)
NEXT_PUBLIC_API_URL=http://localhost

# Individual service URLs (used when calling services directly)
NEXT_PUBLIC_AUTH_SERVICE_URL=http://localhost:5000
NEXT_PUBLIC_RESTAURANT_SERVICE_URL=http://localhost:5001
NEXT_PUBLIC_ORDER_SERVICE_URL=http://localhost:5002
NEXT_PUBLIC_DELIVERY_SERVICE_URL=http://localhost:5003

# Google Maps
NEXT_PUBLIC_GOOGLE_MAPS_API_KEY=your_google_maps_api_key
```

---

## Docker

A `Dockerfile` is included for containerized deployment.

```bash
# Build the image
docker build -t foodhub-frontend .

# Run the container
docker run -p 3000:3000 --env-file .env.local foodhub-frontend
```

---

## Related Repository

[FoodHub Backend](https://github.com/IT22056320/food-delivery-system-backend) — Node.js microservices with Express, MongoDB, Docker, and Kubernetes.

---

<div align="center">
Built with Next.js · React · Tailwind CSS · Socket.io · Google Maps
</div>
