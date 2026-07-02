# React Food Order App

A modern React application for browsing meals, managing a shopping cart, and completing checkout with smooth interactions and dynamic state updates. The app provides a clean interface for exploring available meals and submitting orders efficiently.

## Features

- 🍽️ Browse meals with detailed descriptions, images, and prices
- 🛒 Add, remove, and clear items from the shopping cart
- 📝 Multi-step checkout form for submitting customer information
- 🔄 Global state management for cart and user progress (Context API + `useReducer`)
- 🌐 Custom hook for HTTP requests to fetch meals and submit orders
- ⚠️ Error handling for failed requests
- 📱 Responsive and clean UI for mobile and desktop

## Tech Stack

**Frontend:** React 19, Vite, CSS Modules

**State Management:** Context API & `useReducer`

**Backend:** Node.js, Express, body-parser (simple JSON file-based data store)

## Project Structure

```
react-food-order-app/
├── backend/                    # Simple Express API server
│   ├── app.js                  # Server entry point
│   ├── data/                   # JSON "database" (meals, orders)
│   └── public/images/          # Meal images served by the backend
├── src/
│   ├── components/             # UI components (Meals, Cart, Checkout, etc.)
│   │   └── UI/                 # Shared UI primitives (Button, Input, Modal)
│   ├── hooks/                  # Custom hooks (useHttp)
│   ├── store/                  # Context providers (Cart, UserProgress)
│   └── util/                   # Formatting helpers
├── index.html
└── vite.config.js
```

## Getting Started

### Prerequisites

- Node.js 18+

This project has two parts that need to run together: the **frontend** (Vite/React) and the **backend** (Express API that serves meal data and handles orders). Both must be running for the app to work.

### Installation

1. Clone the repository

   ```bash
   git clone https://github.com/CoraxMuninn/react-food-order-app.git
   cd react-food-order-app
   ```

2. Install frontend dependencies

   ```bash
   npm install
   ```

3. Install backend dependencies

   ```bash
   cd backend
   npm install
   cd ..
   ```

### Running the App

1. Start the backend server (from the `backend` folder)

   ```bash
   cd backend
   npm start
   ```

   The API server runs on [http://localhost:3000](http://localhost:3000) by default.

2. In a separate terminal, start the frontend dev server (from the project root)

   ```bash
   npm run dev
   ```

   Open the local URL shown in your terminal (typically [http://localhost:5173](http://localhost:5173)) in your browser.

## Available Scripts

**Frontend (root directory):**

| Command           | Description                          |
| ----------------- | ------------------------------------ |
| `npm run dev`     | Start the Vite development server    |
| `npm run build`   | Build the app for production         |
| `npm run lint`    | Run ESLint                           |
| `npm run preview` | Preview the production build locally |

**Backend (`backend/` directory):**

| Command     | Description                  |
| ----------- | ---------------------------- |
| `npm start` | Start the Express API server |

## How It Works

- The **Meals Page** fetches meal data from the backend using a custom HTTP hook (`useHttp`) and displays them as interactive meal items.
- The **Cart** allows users to add, remove, and clear meals, showing a live total price.
- The **Checkout** page collects customer information and submits the order to the backend, where it's stored in `backend/data/orders.json`.
- Global state is handled with **Context API** and `useReducer`, managing cart contents and checkout progress (`CartContext`, `UserProgressContext`).
- Error messages and loading states are displayed dynamically to guide the user through failed requests or slow responses.
