# 🛍️ Full‑Stack E‑Commerce App

A modern **full-stack e-commerce web application** built with **React (frontend)** and **Node.js + Express + Sequelize (backend)**.  
Supports **shopping cart**, **orders**, **delivery options**, and **tracking**, with persistence via SQLite in production.

---

**<h2>Table of Contents</h2>**

### •	 <ins>Features</ins>

### •	 <ins>Demo</ins>

### •	 <ins>Usage</ins>

### •	 <ins>Tech Stack</ins>

### •	 <ins>Project Structure</ins>

### •	 <ins>Getting Started</ins>

### •	 <ins>Environment Variables</ins>

### •	 <ins>Commit History Highlights</ins>

### •	 <ins>Future Enhancements</ins>

### •	 <ins>Contributing</ins>

### •	 <ins>Contact</ins>

---

## ✨ Features

### 🖥️ Frontend (React + SPA)
- Built with **React + React Router** for smooth navigation (Home, Cart, Checkout, Orders, Tracking).
- Interactive **cart system** (add, update, delete, auto-feedback messages).
- **Delivery options** selector with shipping costs and estimated delivery times.
- **Search bar** with keyword filtering across products.
- Async API calls with **Axios**, using `async/await`.
- Reusable UI components for headers, order summary, delivery dates.
- **NotFoundPage** for invalid routes.
- SPA fallback to `index.html` for deep links.

### ⚙️ Backend (Node.js + Express + Sequelize)
- RESTful JSON API endpoints:
  - `/api/products` – list/search products  
  - `/api/delivery-options` – shipping choices  
  - `/api/cart-items` – CRUD cart operations  
  - `/api/orders` – create & fetch user orders  
  - `/api/payment-summary` – compute total + taxes  
  - `/api/reset` – reset database with seed data  
- **Sequelize** v6 models:
  - `Product` (UUID, rating, keywords as array getter/setter)  
  - `Order` (UUID, products array, computed totals, order time)  
  - `CartItem` (productId, qty, deliveryOptionId)  
  - `DeliveryOption` (id, delivery days, priceCents)  
- Default DB: **SQLite (via sql.js-as-sqlite3)** with persistence to `database.sqlite`.  
- Production-ready: Switches to **AWS RDS MySQL/Postgres** via `DB_TYPE` and `RDS_*` env vars.  
- Static asset serving: `/images` and SPA build output (`dist`).  

### 📦 Persistence
- SQLite is in-memory by default; Sequelize model hooks export DB changes to **`database.sqlite`** for durability.  
- Seed data for products, delivery options, cart, and orders auto-created on first run or via `/api/reset`.

### 💳 Payments & Orders
- **Payment summary endpoint**:
  - Subtotals products  
  - Adds delivery charges  
  - Applies 10% tax and returns computed totals  
- **Orders**:
  - Created from the cart  
  - Stores product list as JSON  
  - Cleans up cart after checkout

---

## Demo

https://github.com/user-attachments/assets/d14bb479-bdb4-43ab-b98c-a15ad2222ef4

---

## Usage
- Browse products, filter via search, and add items to the cart.
- Update quantities, remove items, and choose delivery options.
- Proceed to checkout to create an order.
- View orders and track them with estimated delivery dates.
- Review payment summary for subtotal, shipping, tax, and total.

---

## 🚀 Tech Stack

**Frontend:**  
- React, React Router DOM  
- Axios (REST API integration)  

**Backend:**  
- Node.js (ES modules, top-level `await`)  
- Express (REST routing, JSON parsing, CORS, static middleware)  
- Sequelize ORM  
- SQLite (dev) / MySQL or Postgres (AWS RDS for prod)  

**Other Tools:**  
- ESLint (Airbnb-style rules; ES2021, Node + Browser env)  
- Nodemon (dev reload)  
- Archiver (bundling)  
- Patch-package  

---

## 📂 Project Structure

<br>├── server.js # Express app entrypoint</br>
<br>├── /api # Routes: products, cart, orders, etc.</br>
<br>├── /models # Sequelize models</br>
<br>├── /default-data # Seed data (products, orders, delivery options)</br>
<br>├── /dist # Frontend SPA build</br>
<br>├── /images # Static product images</br>
<br>├── /frontend # React source (components, pages, routes)</br>
<br>└── database.sqlite # Persisted SQLite DB</br>

---

## 🔧 Getting Started

### 1. Install dependencies
npm install

### 2. Run in development
npm run dev

- Starts **Express backend** with **Nodemon**  
- Runs frontend React app (via your setup or bundled dist)  

### 3. Build frontend (if in frontend project folder)
npm run build


### 4. Start in production
npm start

---

## 🌐 Environment Variables

| Variable         | Description                            | Example                  |
|------------------|----------------------------------------|--------------------------|
| `PORT`           | Server port                            | `3000`                   |
| `DB_TYPE`        | Database dialect (`sqlite`/`mysql`/`postgres`) | `sqlite`        |
| `RDS_HOSTNAME`   | AWS RDS Host (prod only)               | `mydb.xxxxx.rds.amazonaws.com` |
| `RDS_USERNAME`   | Database username                      | `admin`                  |
| `RDS_PASSWORD`   | Database password                      | `secret`                 |
| `RDS_DB_NAME`    | DB name                                | `ecommerce`              |
| `RDS_PORT`       | DB port                                | `3306` (MySQL)           |

---

## 📝 Commit History Highlights

- **Frontend Migration:** Converted all pages (Home, Checkout, Orders, Tracking) into React with React Router.  
- **Backend Integration:** Added ecommerce backend in Express + Sequelize with SQLite (later MySQL/Postgres support).  
- **Core Features:**  
  - Add to Cart & Cart Management (CRUD).  
  - Delivery option selection.  
  - Create Orders & Payment Summary (with tax).  
  - Order tracking & Cart state shared across pages.  
- **UX Improvements:**  
  - Interactive features (search bar, update button, add-to-cart message feedback).  
  - Async/await refactors.  
  - Componentized headers, delivery, and summary sections.  

---

## 🛠️ Future Enhancements
- 🔐 User authentication and accounts  
- 🛒 Persistent carts per user  
- 💳 Payment gateway integration (Stripe/PayPal)  
- 📊 Admin dashboard for products & orders  
- 🔍 Full‑text / fuzzy search  

---

## Contributing
Contributions are welcome. Please fork the repository and open a pull request. For major changes, open an issue first to discuss what you would like to change.

---

## Contact
For support or inquiries, please open an issue or email: ramnath2544@gmail.com.
