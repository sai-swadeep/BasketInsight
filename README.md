# BasketInsight
An E-Commerce Website
# BasketInsight – Next-Generation Production E-Commerce Web Application

> **Academic Minor Project-II (Section A, Group A6)**  
> **Platform Name:** BasketInsight – E-Commerce Website  
> **Status:** Production-Ready Full-Stack Web Application  

---

## 1. Project Metadata & Author Attribution

| Author Name | Registration Number | University Roll Number | Role |
| :--- | :--- | :--- | :--- |
| **Sai Subham Patra** | `25UG010091` | `25CSE023` | Full-Stack Architecture & State Management |
| **Sai Swadeep Nayak** | `25UG010132` | `25CSE065` | Product Design, UI/UX System & Frontend |
| **Sumeet Patika** | `25UG010123` | `25CSE056` | REST API Layer, Controllers & Database Seeder |

- **Operating Environment:** Modern browsers (*Google Chrome, Microsoft Edge, Mozilla Firefox, Apple Safari*) with full responsiveness across mobile, tablet, and ultra-wide displays.
- **Academic Context:** Minor Project-II submission demonstrating enterprise MERN architectural principles, clean MVC layers, optimistic Redux data flow, and complete order processing workflows.

---

## 2. UI/UX Design System & Real-Life Visual Theme

The user interface follows a modern, minimalist design aesthetic featuring flat cards, crisp photography containers, subtle drop shadows (`0 4px 12px rgba(0, 0, 0, 0.05)`), high typography contrast, and soft pastel surfaces.

### SCSS Color Palette (`client/app/styles/core/_variables.scss` & `_custom.scss`):
- **Primary Brand Accent:** `rgb(78, 128, 245)` *(Soft Indigo Blue)*
- **Hover Accent State:** `rgb(54, 99, 212)`
- **Soft Pastel Surface:** `#f4f6fb` / `#ffffff`
- **Text Primary:** `#1e293b`
- **Text Secondary:** `#64748b`
- **Success / Stock Badge:** `#10b981` *(Emerald Green)*
- **Card Drop Shadow:** `0 4px 12px rgba(0, 0, 0, 0.05)`

---

## 3. Scalable System Architecture & File Blueprint

### Architecture Pattern: Layered MVC & Redux Data Flow
- **Client-Side Data Layer:** Single source of truth managed via Redux Store with async action creators handling REST API calls (`axios`), error boundaries, and optimistic UI updates for wishlist and persistent cart.
- **Server-Side REST Layer:**
  - **Controllers & API Routes (`/server/routes/api`):** Strict request processing, input validation via `validatorjs`, structured JSON responses, and HTTP response status codes ($200, 201, 400, 401, 403, 404, 500$).
  - **Data Layer (`/server/models`):** Mongoose schemas with indexed lookup fields (`slug`, `brand`, `isFeatured`, `isActive`).
  - **Middleware (`/server/middleware`):** JWT verification (`auth.js`), role-based access control (`role.js`), payload sanitization, and security headers via `helmet`.

```text
mern-ecommerce-master/
├── client/
│   ├── app/
│   │   ├── actions/          # Redux action creators (auth, product, cart, order, wishlist)
│   │   ├── components/       # Reusable UI: Navbar, Footer, ProductCard, SearchBar, RatingStars, Checkout
│   │   ├── containers/       # Views: Homepage, Shop, ProductPage, Cart, OrderSuccess, Dashboard
│   │   ├── reducers/         # Combined Redux state reducers
│   │   ├── styles/core/      # SCSS rules, mixins, and _variables.scss (configured with rgb(78, 128, 245))
│   │   └── utils/            # Axios API client, auth token storage, formatters
│   ├── public/               # HTML template with metadata, favicon, and manifest
│   └── webpack/              # Webpack configurations (dev, common, prod)
├── server/
│   ├── config/               # keys.js, passport strategies, and template engine
│   ├── constants/            # Application enums (order status, payment method, roles)
│   ├── middleware/           # auth.js, role.js
│   ├── models/               # Mongoose schemas (User, Product, Category, Brand, Cart, Order, Review)
│   ├── routes/api/           # Express endpoints (/auth, /user, /product, /category, /brand, /cart, /order)
│   ├── utils/                # seed.js (real-world dataset seeder), db.js (auto-reconnect & auto-seed)
│   └── server.js             # Main Express server entry point
└── package.json              # Root project script orchestrator
```

---

## 4. Fully Functional Real-World Workflows

1. **User Authentication & Identity:**
   - Account signup, secure bcrypt hashing, session persistence via JWT, and profile management.
   - Customer Dashboard: Edit profile details, manage saved shipping addresses, and view past orders with order status tracking timelines.

2. **Product Catalog & Real-Time Discovery:**
   - **Catalog Browsing:** Real-time search bar, category filtering (*Electronics, Wearables, Audio, Lifestyle & Accessories*), dynamic price range slider, brand filter, and pagination.
   - **Product Page:** High-resolution multi-image gallery, detailed technical specifications, real stock counters (*e.g., "Only 3 left in stock - order soon!"*), dynamic pricing (USD / INR reference), verified customer reviews, and star ratings.

3. **Shopping, Wishlist & Buy Now Actions:**
   - **Persistent Cart:** Side drawer mini-cart and full-page cart with live quantity updates, automated pricing calculations, and persistent `localStorage` synchronization.
   - **Wishlist Engine:** Instant 1-click heart icon toggle to save or remove products into personal saved wishlist.
   - **Buy Now Action:** Instant single-click checkout bypass button to purchase items immediately.

4. **Checkout, Payment Simulation & Receipt Generator:**
   - Multi-step checkout wizard with saved delivery address picker, address entry form, and payment simulation options:
     - 💵 Cash on Delivery (COD)
     - 💳 Credit / Debit Card (Simulated test card)
     - 📱 Instant UPI (Google Pay, PhonePe, Paytm simulation)
   - Automated pricing calculations ($Subtotal + Shipping + Tax = Total Amount$).
   - **Digital Order Receipt:** Order confirmation page generating an itemized, print-friendly purchase summary with unique Order IDs, estimated delivery, and `window.print()` support.

---

## 5. Real-World Seed Dataset (`server/utils/seed.js`)

The database seeder script populates MongoDB with 16 real-world products with high-resolution Unsplash images:

- **Categories:** Electronics, Wearables, Audio, Lifestyle & Accessories
- **Brands:** Sony, Apple, Bose, Logitech, Nike, Samsung
- **Featured Products:**
  1. *Sony WH-1000XM5 Wireless Noise-Canceling Headphones* ($399, Audio)
  2. *Apple Watch Series 9 GPS 45mm* ($429, Wearables)
  3. *Logitech MX Master 3S Ergonomic Mouse* ($99, Electronics)
  4. *Nike Air Max 270 Athletic Sneakers* ($160, Lifestyle & Accessories)
  5. *Apple AirPods Pro (2nd Generation)* ($249, Audio)
  6. *Bose QuietComfort Ultra Headphones* ($429, Audio)
  7. *Samsung Galaxy S24 Ultra 5G* ($1,299, Electronics)
  8. *Apple MacBook Air M3 13-inch* ($1,299, Electronics)
  9. *Sony PlayStation 5 Slim Console* ($499, Electronics)
  10. *Samsung Galaxy Watch 6 Classic* ($399, Wearables)
  11. *Nike Sportswear Windrunner Heritage Jacket* ($120, Lifestyle & Accessories)
  12. *Bose SoundLink Flex Bluetooth Portable Speaker* ($149, Audio)
  13. *Logitech MX Mechanical Wireless Keyboard* ($169, Electronics)
  14. *Nike Dri-FIT Tech Fleece Full-Zip Hoodie* ($145, Lifestyle & Accessories)
  15. *Samsung 32" Odyssey Neo G8 4K Curved Gaming Monitor* ($999, Electronics)
  16. *Sony WF-1000XM5 Truly Wireless Earbuds* ($299, Audio)

---

## 6. Getting Started & Setup Guide

### Prerequisites:
- **Node.js:** v18, v20, v22, or v24
- **MongoDB:** Local MongoDB daemon (`mongodb://localhost:27017/basketinsight`) or a MongoDB Atlas URI

### 1. Environment Configuration:
Copy `.env.example` to `.env` or verify default configurations:
```bash
cp .env.example .env
```
Default parameters in `.env`:
```env
PORT=5000
MONGO_URI=mongodb://localhost:27017/basketinsight
JWT_SECRET=basketinsight_jwt_super_secret_key_2026
CLIENT_URL=http://localhost:8080
BASE_API_URL=api
```

### 2. Populate Real-World Seed Data:
Run the seeder engine to populate categories, brands, real-world catalog items, admin user, and customer user:
```bash
npm run seed
```
**Default Seed Credentials:**
- **Admin Portal:** `admin@basketinsight.com` / `Admin@123`
- **Customer Account:** `customer@basketinsight.com` / `Customer@123`

### 3. Run Development Server:
Start both the Express backend API and Webpack frontend dev server concurrently:
```bash
npm run dev
```
- Frontend Client: `http://localhost:8080`
- Backend API Server: `http://localhost:5000`

### 4. Production Build:
Compile the production-optimized client bundle:
```bash
npm run build:client
```
The compiled assets will be written to `client/dist/`. Running `node server/server.js` will serve the entire application from `http://localhost:5000`.

---

## 7. License
Developed under the MIT License for Academic Minor Project-II (Section A, Group A6).
