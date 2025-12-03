# 📦 Inventory Management System

A modern, full-stack inventory management dashboard built with **Next.js**, **TypeScript** **Prisma**, **PostgreSQL**, **Shadcn UI**, and **Clerk Authentication**.

This project allows users to securely sign up / sign in, then access their personalized **dashboard** where they can manage products, categories, stock levels, and view analytics.

---

## 🚀 Tech Stack

| Layer              | Technology                                               |
| ------------------ | -------------------------------------------------------- |
| **Frontend**       | Next.js 14 (App Router), React, TailwindCSS              |
| **UI Components**  | Shadcn/UI                                                |
| **Backend**        | Next.js API Routes                                       |
| **ORM**            | Prisma                                                   |
| **Database**       | PostgreSQL                                               |
| **Authentication** | Clerk                                                    |

---

## ✨ Features

* 🔐 **Secure Authentication** with Clerk (Sign In / Sign Up / Email verification).
* 📊 **Dynamic Dashboard** per user at:

  ```
  /dashboard
  ```
* 📦 **Products Management**

  * Add, edit, delete products
  * Upload images
  * Track quantity & status
* 🏷️ **Category Management**

  * Create & manage product categories
* 📉 **Stock Tracking**

  * Low-stock alerts
  * Status indicators
* 📈 **Analytics & KPIs**

  * Total products
  * Total categories
  * Low stock count
* 🎨 **Clean UI** thanks to Shadcn components
* ⚡ **High Performance** using Next.js App Router & Server Actions

---

## 📁 Project Structure (Simplified)

```
/app
  /dashboard
    page.tsx
    layout.tsx
    components/*
  /api
    /products
    /categories
  /auth
/prisma
  schema.prisma
/src
  components/*
  lib/*
```

---

## 🧩 Database Model (Prisma)

```prisma
model User {
  id        String    @id @default(cuid())
  email     String    @unique
  products  Product[]
  categories Category[]
}

model Product {
  id          String   @id @default(cuid())
  name        String
  quantity    Int
  categoryId  String
  userId      String
  user        User      @relation(fields: [userId], references: [id])
  category    Category  @relation(fields: [categoryId], references: [id])
}

model Category {
  id      String    @id @default(cuid())
  name    String
  userId  String
  user    User      @relation(fields: [userId], references: [id])
  products Product[]
}
```

---

## 🔧 Installation & Setup

### 1️⃣ Clone the repo

```bash
git clone https://github.com/omar-elsayed10/Inventory-Management-System.git
cd inventory-management-system
```

### 2️⃣ Install dependencies

```bash
npm install
```

### 3️⃣ Create env file

```env
DATABASE_URL="your_postgresql_connection"
NEXT_PUBLIC_CLERK_PUBLISHABLE_KEY=your_key
CLERK_SECRET_KEY=your_key
```

### 4️⃣ Push Prisma schema

```bash
npx prisma db push
```

### 5️⃣ Start the dev server

```bash
npm run dev
```

---

## 🔐 Authentication Flow (Clerk)

1. User creates an account via Clerk UI.
2. After login, the user is automatically redirected to:

```
/dashboard
```

3. Each user sees **their own data only** (products, categories, analytics).

---

## 📌 Roadmap

* Add multi-warehouse support
* Export inventory as Excel/PDF
* Add suppliers module
* Add activity logs
* Add role-based permissions

---

## 🤝 Contributing

Pull requests are welcome. For major changes, please open an issue first to discuss what you would like to improve.

---

## ⚡ Author

**Omar Elsayed**
Full-Stack Developer (MERN / Next.js)

---


