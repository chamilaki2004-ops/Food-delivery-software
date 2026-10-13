<div align="center">

# 🍔 FoodHub
### Food Delivery Management System

**Discover food. Order with ease. Manage everything in one place.**

A VS Code-oriented web application starter built with **Vue 3**, **C++17 / Crow**, and **SQLite**.

![Vue 3](https://img.shields.io/badge/Vue.js-3-42b883?style=for-the-badge&logo=vuedotjs&logoColor=white)
![C++](https://img.shields.io/badge/C%2B%2B-17-00599C?style=for-the-badge&logo=cplusplus&logoColor=white)
![SQLite](https://img.shields.io/badge/SQLite-Database-003B57?style=for-the-badge&logo=sqlite&logoColor=white)
![Vite](https://img.shields.io/badge/Vite-Frontend-646CFF?style=for-the-badge&logo=vite&logoColor=white)

</div>

---

## 📖 About the Project

**FoodHub** is a food ordering and administration web application starter. It provides a customer-facing menu and ordering flow alongside an administrator area for managing food items and reviewing orders.

The frontend is built with Vue 3 and Vite. A C++17 REST API powered by Crow handles application requests, while SQLite stores application data.

> ⚠️ **Project status:** This repository is a development starter, not a production-ready application. The full build and runtime have not been verified in every environment. Review the limitations and assignment notes before relying on it for a formal submission.

## ✨ Features

### 🛍️ Customer experience
- 🔐 Register an account and sign in.
- 🍽️ Browse available food items and categories.
- 🔎 Search and filter the menu.
- 🛒 Add items to the cart and update quantities.
- 🧾 Place orders and review order history.
- 🔔 View notifications.
- 👤 Update profile details and change password.

### 🛡️ Administrator area
- 📊 View dashboard analytics.
- 🍔 Add and edit food items.
- 🖼️ Upload food images (PNG, JPEG, or WebP; maximum 5 MB).
- 📦 Review customer orders and update their status.
- 👥 Enable or disable user accounts.
- 📈 View order and sales-related summary metrics.

### 🧩 Application foundations
- 🔌 REST API between the frontend and backend.
- 🗄️ SQLite database storage.
- 🧮 Cart totals and order-line calculations.
- 📦 Stock reduction when an order is placed.
- 🔑 Role-aware customer and administrator navigation.

*Feature scope reflects the implementation currently included in this starter; see [Known Limitations](#️-known-limitations).*

## 🧰 Tech Stack

| Technology | Role |
|---|---|
| 🟩 **Vue 3** | Interactive web interface |
| ⚡ **Vite** | Frontend development server and build tool |
| 🎨 **Lucide Vue Next** | Interface icons |
| 📊 **Chart.js** | Charting dependency |
| 🔵 **C++17** | Backend application logic |
| 🌐 **Crow** | C++ REST API framework |
| 🗃️ **SQLite3** | Local relational database |
| 🔐 **OpenSSL** | Cryptographic support used by the backend |
| 🛠️ **CMake** | Backend build configuration |
| 📦 **vcpkg** | C++ dependency management |
| 🧑‍💻 **Visual Studio Code** | Suggested editor |

## 🏗️ Architecture

```text
┌──────────────────────────────┐
│       Customer / Admin       │
└──────────────┬───────────────┘
               │ Browser
               ▼
┌──────────────────────────────┐
│       Vue 3 + Vite UI        │
│       localhost:5173         │
└──────────────┬───────────────┘
               │ /api and /uploads
               ▼
┌──────────────────────────────┐
│       C++17 + Crow API       │
│       localhost:8080         │
└──────────────┬───────────────┘
               │
               ▼
┌──────────────────────────────┐
│        SQLite3 Database      │
│     backend/data/            │
└──────────────────────────────┘
```

## 📁 Project Structure

```text
FoodHub_Web_VSCode/
├── backend/
│   ├── CMakeLists.txt
│   ├── main.cpp
│   └── third_party/
│       └── sqlite/
│           ├── sqlite3.c
│           └── sqlite3.h
├── frontend/
│   ├── package.json
│   ├── vite.config.js
│   ├── index.html
│   └── src/
│       ├── App.vue
│       ├── main.js
│       └── style.css
├── docs/
│   └── ICT1306_NOTES.md
├── .gitignore
├── vcpkg.json
├── COMPILER_FIX.md
└── README.md
```

## ⚙️ Requirements

Before running the project, install/configure:

- 🪟 Windows 11 (recommended environment described by this project)
- 🧑‍💻 Visual Studio Code
- 🧱 Visual Studio 2022 or compatible MSVC Build Tools with **Desktop development with C++**
- 🛠️ CMake 3.20 or newer
- 📦 vcpkg, with the `VCPKG_ROOT` environment variable configured
- 🟢 Node.js 20.19+ or 22+, and npm
- 🧩 VS Code extensions: **C/C++**, **CMake Tools**, and **Vue - Official**

## 🚀 Getting Started

### 1. Open the project

Extract the repository archive, then open the `FoodHub_Web_VSCode` folder in VS Code.

### 2. Configure the backend

Open a **PowerShell terminal** at the project root:

```powershell
$env:VCPKG_ROOT = "C:\vcpkg"
$env:FOODHUB_ADMIN_CODE = "ChooseYourOwnLocalDemoCode"

cmake -S backend -B backend/build `
  -DCMAKE_TOOLCHAIN_FILE="$env:VCPKG_ROOT/scripts/buildsystems/vcpkg.cmake"

cmake --build backend/build --config Debug
```

Change `C:\vcpkg` to the actual location of your vcpkg installation. Set your own local demo administrator code; do not commit secrets or real credentials to GitHub.

### 3. Start the backend

From the project root, run:

```powershell
cd backend
.\build\Debug\foodhub.exe
```

Depending on the CMake generator, the executable may instead be located at `build\foodhub.exe`.

Run the backend **from the `backend` directory** so its relative database and upload paths resolve as expected. The API listens at:

```text
http://localhost:8080
```

### 4. Start the frontend

Open a **second terminal**:

```powershell
cd frontend
npm install
npm run dev
```

Open the URL shown by Vite, usually:

**http://localhost:5173**

> Do not open `frontend/index.html` directly. Run the Vite development server so API requests can be proxied to the backend.

## 🧭 Quick Demo Workflow

1. ▶️ Start the backend and frontend.
2. 🧑 Create an account and choose the **Administrator** role, using the local administrator code configured in `FOODHUB_ADMIN_CODE`.
3. 🔐 Sign in and open **Food Items**.
4. 🍔 Add a food item with a category, price, stock amount, and an optional supported image.
5. 👤 Register a separate **Customer** account and sign in.
6. 🛒 Browse the menu, add food to the cart, and place an order.
7. 📦 Sign in as the administrator to review the order and update its status.

### 🖼️ Food image notes
- Accepted formats: PNG, JPEG, and WebP.
- Maximum upload size: 5 MB.
- Prepare images in a square (1:1) format before upload; automatic cropping/resizing is not implemented.

## 🗄️ Data and Storage

The original design terms `CUSTOMER`, `ORDER`, `ITEM`, and `ORD_ITEM` are represented in this starter by application tables such as:

- 👤 `users`
- 🧾 `orders`
- 🍔 `foods`
- 🛒 `order_items`

Application data and uploaded images are expected under `backend/data/` and `backend/data/uploads/` when the server is launched from the backend directory.

## 🧯 Troubleshooting

### CMake cannot find Crow or another dependency
- Confirm that vcpkg is installed.
- Check that `VCPKG_ROOT` points to the correct directory.
- Re-run the CMake configure command with the vcpkg toolchain file.
- Review the exact CMake error output.

### Backend build fails in Visual Studio
See **[`COMPILER_FIX.md`](COMPILER_FIX.md)** for the fixes already applied to the source. The project notes that a successful MSVC build has not been independently verified in the original development environment, so additional environment-specific issues may remain.

### Frontend cannot reach the API
- Make sure the backend is running on port `8080`.
- Run the frontend using `npm run dev`.
- Open the Vite URL, normally `http://localhost:5173`.
- Check the terminal and browser console for the exact error.

### Database or upload files appear in an unexpected location
Launch `foodhub.exe` from the `backend` directory as shown above. The application uses relative paths for its local data folders.

## ⚠️ Known Limitations

This project is an **unverified development starter**. The following limitations are documented in the included project notes:

- ❌ No online payment integration.
- 🖼️ No built-in image cropper/resizer.
- 🧑‍💼 No full administrator user-creation/editing form; account enable/disable is provided.
- 🗂️ No category CRUD interface.
- 🛵 Rider, vehicle, and assignment workflows are not implemented.
- 💳 Payment verification is not automated.
- 🧾 No detailed audit interface.
- ✉️ No email delivery.
- 🧪 Automated tests are not included.
- 📊 “Completed Order Value” should not be interpreted as verified collected revenue.
- 🔐 Production hardening is needed for authentication/session handling, rate limiting, upload validation, HTTPS, and order-status policies.

Do not deploy this starter publicly with demo credentials or without a security review.

## 🎓 ICT1306 Assignment Note

The included `docs/ICT1306_NOTES.md` explains a key scope difference: the assignment brief calls for a **desktop GUI** (WinForms/MFC recommended), while this repository is a **web application** using Vue, Crow, and SQLite.

The current web starter should **not be described as automatically satisfying the desktop assignment requirements**. Confirm acceptability with the lecturer or prepare a separate compliant desktop deliverable.

## 🔧 Compiler Fix Notes

The file [`COMPILER_FIX.md`](COMPILER_FIX.md) records two changes made for Visual Studio/Crow compilation:

- An explicit `std::string` return to resolve a mixed-type ternary expression.
- `#undef DELETE` to avoid a Windows macro collision with `crow::HTTPMethod::DELETE`.

These changes are documented, but a complete MSVC build still needs to be tested on the target machine.

## 🤝 Contributing

1. Create a branch for your change.
2. Make and test the update locally.
3. Keep credentials, database secrets, and generated build files out of commits.
4. Submit a pull request or push the change to your team repository.

## 📚 Documentation

- [`COMPILER_FIX.md`](COMPILER_FIX.md) — notes on compiler fixes.
- [`docs/ICT1306_NOTES.md`](docs/ICT1306_NOTES.md) — assignment requirements and scope comparison.

## 👥 Project Team

Add or update team member names, student IDs, and contributions here if required by your submission.

## 📜 License

No license is specified in the supplied project files. Add a license only if the project owner/team has chosen one.

---

<div align="center">

**🍔 FoodHub — Food ordering made simpler.**

Made as a development and academic project.

</div>
