# cmsc190-special-problem-pena

This project is a full-stack web application developed by **Joseph Ryan P. Peña** as a requirement for CMSC 190 (Special Problem) under the Bachelor of Science in Computer Science program at the Institute of Computer Science, University of the Philippines Los Baños.

This repository also contains the following supplementary materials related to the study:
*   `Peña_Journal.pdf`: The research paper in journal format.
*   `Peña_Manuscript.pdf`: The full manuscript of the special problem.
*   `Peña_Poster.pdf`: The poster presented for the study.
*   `Peña_Presentation.pdf`: The presentation slides used for the defense of the study.

## Features

*   **User Authentication:** Secure login and registration for users.
*   **Role-Based Access Control:** Different functionalities for administrators, teachers, and students.
*   **Class and Section Management:** Allows administrators/teachers to create and manage classes and sections.
*   **Student Enrollment:** Students can enroll in available classes/sections.
*   **Grading System:** Teachers can input and manage student grades.
*   **Messaging System:** Enables communication between users within the platform.
*   **Configuration Management:** Admin panel for system configurations.

## Tech Stack

*   **Frontend:** React, Vite, Tailwind CSS, Zustand (for state management)
*   **Backend:** Node.js, Express.js
*   **Database:** MongoDB (with Mongoose ODM)
*   **Real-time Communication:** Socket.IO
*   **Image/File Storage:** Cloudinary (assumed from `cloudinary.js`)
*   **Testing:** Jest, Supertest

## Prerequisites

*   Node.js (v18.x or later recommended)
*   npm (comes with Node.js)
*   MongoDB instance (local or cloud-based)

## Getting Started

### 1. Clone the repository:

```bash
git clone <repository-url>
cd cmsc190-special-problem-pena
```

### 2. Install Dependencies:

This command will install dependencies for the root, backend, and frontend.

```bash
npm install
```

If the above command doesn't install all dependencies correctly, you can try installing them individually:

```bash
# Install root dependencies (if any, though typically not needed for this setup)
# npm install

# Install backend dependencies
npm install --prefix Code/backend

# Install frontend dependencies
npm install --prefix Code/frontend
```

### 3. Environment Variables:

The backend requires environment variables for database connection, JWT secrets, Cloudinary credentials, etc.

Create a `.env` file in the `Code/backend` directory. Example content:

```env
PORT=3000
MONGODB_URI=your_mongodb_connection_string
JWT_SECRET=your_jwt_secret
CLOUDINARY_CLOUD_NAME=your_cloudinary_cloud_name
CLOUDINARY_API_KEY=your_cloudinary_api_key
CLOUDINARY_API_SECRET=your_cloudinary_api_secret
# Add other necessary environment variables
```

The frontend might require a `.env` file in the `Code/frontend` directory if you have environment-specific configurations (e.g., API base URL). Example:

```env
VITE_API_BASE_URL=http://localhost:3000/api
```
*(Adjust the port if your backend runs on a different one)*

### 4. Initialize Configuration (Backend):

The backend has a script to initialize some configurations. Run this after setting up your `.env` file and ensuring your MongoDB instance is running.

```bash
npm run initConfig --prefix Code/backend
```

### 5. Seed Database (Optional):

To populate the database with initial data (e.g., sample students, teachers):

```bash
npm run seed --prefix Code/backend
```

### 6. Running the Application:

#### Development Mode:

*   **Backend:**
    ```bash
    npm run dev --prefix Code/backend
    ```
    This will start the backend server, typically on `http://localhost:3000` (or the port specified in your `.env`).

*   **Frontend:**
    ```bash
    npm run dev --prefix Code/frontend
    ```
    This will start the Vite development server, typically on `http://localhost:5173`.

#### Production Mode:

1.  **Build the Frontend:**
    ```bash
    npm run build --prefix Code/frontend
    ```
    This creates a `dist` folder in `Code/frontend` with the optimized static assets.

2.  **Start the Backend (serves frontend build):**
    The root `package.json` has a script that should handle building everything and starting the backend.
    ```bash
    npm run build  # Installs all dependencies and builds the frontend
    npm run start  # Starts the backend server
    ```
    The backend is expected to be configured to serve the static files from the frontend's build directory.

## Available Scripts

### Root (`./package.json`)

*   `npm run build`: Installs dependencies for both backend and frontend, then builds the frontend.
*   `npm run start`: Starts the backend server (intended for production).

### Backend (`./Code/backend/package.json`)

*   `npm run dev --prefix Code/backend`: Starts the backend server with Nodemon for development (auto-restarts on file changes).
*   `npm run start --prefix Code/backend`: Starts the backend server using Node.
*   `npm run seed --prefix Code/backend`: Seeds the database with initial data.
*   `npm run initConfig --prefix Code/backend`: Initializes application configurations.
*   `npm run test:protectRoute --prefix Code/backend`: Runs tests for route protection.
*   `npm run test:roleBasedAccessControl --prefix Code/backend`: Runs tests for RBAC.
*   `npm run test:hashedPassword --prefix Code/backend`: Runs tests for password hashing.
*   `npm run test:noSQLInjection --prefix Code/backend`: Runs tests for NoSQL injection vulnerabilities.
*   `npm run test:inputValidation --prefix Code/backend`: Runs tests for input validation.

### Frontend (`./Code/frontend/package.json`)

*   `npm run dev --prefix Code/frontend`: Starts the Vite development server.
*   `npm run build --prefix Code/frontend`: Builds the frontend application for production.
*   `npm run lint --prefix Code/frontend`: Lints the frontend codebase.
*   `npm run preview --prefix Code/frontend`: Serves the production build locally for preview.

## Project Structure

```
cmsc190-special-problem-pena/
├── Code/                     # Main application code
│   ├── backend/              # Node.js, Express.js backend
│   │   ├── src/
│   │   │   ├── config/       # Configuration files (DB, Cloudinary, etc.)
│   │   │   ├── controllers/  # Request handlers
│   │   │   ├── middlewares/  # Express middlewares
│   │   │   ├── models/       # Mongoose models
│   │   │   ├── routes/       # API routes
│   │   │   ├── seeds/        # Database seed scripts
│   │   │   └── tests/        # Backend tests
│   │   └── package.json
│   ├── frontend/             # React, Vite frontend
│   │   ├── public/           # Static assets
│   │   ├── src/              # Frontend source code
│   │   │   ├── assets/
│   │   │   ├── components/   # Reusable React components
│   │   │   ├── lib/          # Utility functions, helpers
│   │   │   ├── pages/        # Page components
│   │   │   └── store/        # Zustand stores
│   │   ├── eslint.config.js
│   │   ├── index.html
│   │   ├── package.json
│   │   └── vite.config.js
│   └── package.json          # Root package.json for build/start scripts
├── Peña_Journal.pdf
├── Peña_Manuscript.pdf
├── Peña_Poster.pdf
├── Peña_Presentation.pdf
└── README.md                 # This file
```


## License

[ISC](https://opensource.org/licenses/ISC) (Based on the `license` field in `Code/package.json`)