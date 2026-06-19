# ShopEZ 🛍️ — Modern MERN Stack E-Commerce Platform

[![MERN Stack](https://img.shields.io/badge/MERN-Stack-blue.svg)](https://mongodb.com)
[![React](https://img.shields.io/badge/React-19.2-cyan.svg)](https://react.dev)
[![Node.js](https://img.shields.io/badge/Node.js-v18+-green.svg)](https://nodejs.org)
[![Express](https://img.shields.io/badge/Express-4.21-lightgrey.svg)](https://expressjs.com)
[![MongoDB](https://img.shields.io/badge/MongoDB-Atlas-green.svg)](https://www.mongodb.com/atlas)
[![Tailwind CSS](https://img.shields.io/badge/Tailwind-CSS%204.3-blueviolet.svg)](https://tailwindcss.com)

ShopEZ is a lightweight, feature-rich, and high-performance e-commerce platform engineered using the MERN stack (MongoDB, Express, React, Node.js). Designed for small-to-medium retail enterprises (SMEs), it delivers a premium customer storefront and a streamlined administrative cockpit to manage catalogs, track orders, and monitor metrics without administrative overhead.

> 📖 **Detailed SDLC Documentation**: For deep-dive specifications on empathy mapping, sprint planning, MVC patterns, database structures, and testing matrices, read the complete **[Project documentation.md](Project%20documentation.md)**.

---

## 🌟 Key Platform Features

### 🛒 Customer Storefront
*   **Adaptive Product Details**: The user interface reads categories dynamically, automatically hiding apparel sizing grids and selectors when displaying items like **Electronics** or **Home Decor**.
*   **Persistent Shopping State**: Shopping cart variables and wishlists are synced with browser LocalStorage and mapped directly to global React contexts to prevent cart loss on page refreshes.
*   **Protected Wishlists**: Automated route guards block unauthenticated users, redirecting them to log in before adding items to wishlists.
*   **Smart Recommendations**: Dynamic "similar products" sliders automatically suggest items matching the active product's category.
*   **Seamless Checkout Flow**: Lightweight, single-page customer checkout supporting local currency rendering (INR - ₹).

### 💼 Admin Portal
*   **Real-Time Analytics Dashboard**: Visual indicators track business health metrics (Total Revenue, Active Orders, Total Products, and Customer Profiles).
*   **Interactive Orders Table**: Review detailed order structures, customer metrics, and execute instant status updates (e.g., Mark as Shipped, Mark as Delivered, or Cancel Order).
*   **Smart Catalog Management**: Dynamic forms hide size selection grids and reveal a single "Stock Quantity" input automatically for non-apparel categories.
*   **Isolated Invoice Printing**: Custom print sheets leveraging isolated `@media print` CSS rules automatically strip dashboard menus, buttons, and headers, rendering clean physical receipts.
*   **Role-Based Route Guarding**: Detects JWT states and automatically redirects administrators directly to the `/admin` workspace upon login.
*   **Data Export**: Single-click actions compile database logs and export orders list to structured CSV files.

---

## 📂 Repository Folder Structure

```text
ShopEZ/
├── client/                 # Frontend React Application (Vite compiler)
│   ├── src/
│   │   ├── components/     # Reusable layout & common UI components
│   │   ├── context/        # React Context providers (Auth, Cart, Wishlist)
│   │   ├── pages/          # View pages (Admin Dashboard, Checkout, Cart, Products, etc.)
│   │   ├── routes/         # Protected and public routing definitions
│   │   ├── services/       # Axios API client integrations
│   │   ├── index.css       # Core Tailwind CSS imports & theme directives
│   │   └── main.jsx        # React entry file
│   ├── vite.config.js      # Vite compilation configuration
│   └── package.json        # Frontend scripts & dependencies
│
├── server/                 # Backend REST API Application (Node.js/Express)
│   ├── config/             # MongoDB Atlas connection setup
│   ├── controllers/        # Express request handlers (Auth, Catalog, Orders, Admin)
│   ├── models/             # Mongoose schemas (User, Admin, Product, Order, Cart)
│   ├── routes/             # Express API route configurations
│   ├── middleware/         # Custom JWT verification & role validation middleware
│   ├── seed.js             # Initial database seeding script
│   ├── index.js            # Node server bootstrapper
│   └── package.json        # Backend dependencies & npm scripts
│
└── MERN Phase Wise/        # Project planning, brainstorming & design artifacts (PDFs)
```

---

## 🚀 Getting Started & Local Setup

### Prerequisites
*   **Node.js**: `v18.x` or above installed locally.
*   **MongoDB**: A local MongoDB Community instance running, or a MongoDB Atlas Cloud connection string.

### 1. Initialize Server Environment
1.  Navigate into the backend directory:
    ```bash
    cd server
    ```
2.  Install dependencies:
    ```bash
    npm install
    ```
3.  Configure your environment parameters. Create a `.env` file in `/server`:
    ```env
    PORT=5000
    MONGO_URI=mongodb://localhost:27017/shopez
    JWT_SECRET=your_jwt_secret_key
    ```
4.  Seed the database with sample products and default credentials:
    ```bash
    npm run seed
    ```
    *Note: This creates an Admin account (`admin@shopez.com` / `admin123`) and a Customer account (`customer@shopez.com` / `customer123`).*
5.  Start the backend API server:
    ```bash
    npm run dev
    ```

### 2. Initialize Client Environment
1.  Open a new terminal tab and navigate into the frontend directory:
    ```bash
    cd client
    ```
2.  Install client dependencies:
    ```bash
    npm install
    ```
3.  Start the local development server:
    ```bash
    npm run dev
    ```
4.  Open your browser and navigate to `http://localhost:3001` (or the local server address shown in your console).

---

## 🛠️ Development Scripts

*   **Backend (`/server`)**:
    *   `npm run dev`: Bootstraps the Express API server with automatic reload (via `nodemon`).
    *   `npm run start`: Runs the Node server in production state.
    *   `npm run seed`: Clears active collections and inserts seed datasets.
*   **Frontend (`/client`)**:
    *   `npm run dev`: Starts the local hot-reloading development server.
    *   `npm run build`: Compiles production-optimized assets inside the `dist/` directory.
