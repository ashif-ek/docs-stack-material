# Todo Redux Advanced

> **A production-ready Todo application engineered with React, Vite, and Redux Toolkit.**

This project demonstrates advanced state management architectural patterns, integrating async thunks, debounced search features, and throttled actions for optimal performance and API coordination. It is built to showcase how to handle complex application states in a clean, scalable, and responsive manner.

[View Repository on GitHub](https://github.com/ashif-ek/todo-redux-adv){ .md-button .md-button--primary }

---

## 🚀 Key Features

### Advanced Redux Implementations
- **Async Thunks**: Manages complex asynchronous data flow and handles loading/error states seamlessly.
- **Debounced Search**: Improves application performance and reduces unnecessary API calls or state updates by debouncing user input during search operations.
- **Throttled Actions**: Limits the rate at which certain high-frequency actions dispatch, enhancing rendering efficiency.
- **Persistent State**: Leverages browser storage mechanisms to persist the Redux store natively, ensuring data continuity across sessions.

### UI & UX Excellence
- **Responsive Interface**: Designed to offer a flawless experience across all devices, from mobile phones to desktop monitors.
- **Instant Feedback**: Optimistic UI updates provide immediate visual feedback upon user interactions.
- **Clean Animations**: Smooth transitions for adding, removing, and completing tasks.

---

## 🛠️ Technology Stack

| Technology | Purpose |
|------------|---------|
| **React** | Component-based UI rendering |
| **Vite** | Blazing-fast frontend build tooling |
| **Redux Toolkit** | Standardized, efficient Redux state management |
| **CSS/SCSS** | Custom styling and responsive layouts |

---

## 🏗️ Architecture & Patterns

### State Slice Organization
The application divides the Redux store into feature-centric slices, encapsulating reducers, actions, and selectors within specialized modules. This pattern promotes:
- Better code splitting.
- Enhanced testability for isolated logic blocks.
- Easier scalability when adding new domain features.

### Performance Optimization
By utilizing specific middleware and utility hooks (like `useDebounce` and `useThrottle`), the app minimizes rendering cycles. `createAsyncThunk` is used extensively to manage API request lifecycles (`pending`, `fulfilled`, `rejected`) gracefully without boilerplate, demonstrating modern React ecosystem best practices.

---

## 🏁 Getting Started

To run this project locally:

1. **Clone the repository:**
   ```bash
   git clone https://github.com/ashif-ek/todo-redux-adv.git
   cd todo-redux-adv
   ```

2. **Install dependencies:**
   ```bash
   npm install
   ```
   *(or `yarn install` / `pnpm install`)*

3. **Start the development server:**
   ```bash
   npm run dev
   ```

4. **Navigate to your browser:**
   Open `http://localhost:5173` to interact with the application.
