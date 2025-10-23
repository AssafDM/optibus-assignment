# Optibus Vehicle Management System

A modern, full-stack vehicle management system built with React, TypeScript, and Express.js for tracking and managing fleet vehicles.

In this assignment i implemented a server on the backend, that stores its state on a json file for persistance,
and a frontend in react(+Vite) that present this data in a table and allows a user to create update and delete vehicles.

when creating the project i took as an assumption the that scale of the data fits in memory, so generaly the scalabilty is limited
in the backend and frontend. but given the assignment stated persistancy is a "nice to have" i chose to keep thing simpler in this area.

last thing, the port of the server is hardcoded in the frontend api and is a default to 3000 if needs to change it is all explained in the installation section

## Features

### Core Functionality

- **Vehicle Management**: Create, read, update, and delete vehicles -**Persistance**: Changed data persists between sessions.
- **Status Tracking**: Monitor vehicle status (Available, InUse, Maintenance)
- **License Plate Management**: Alphanumeric validation and formatting
- **Real-time Updates**: Live data synchronization

### Business Rules

- **Status Transitions**: Maintenance vehicles can only move to Available
- **Maintenance Cap**: Maximum 5% of vehicles can be in Maintenance
- **Delete Restrictions**: Only Available vehicles can be deleted
- **License Plate Validation**: Alphanumeric only, 2-10 characters

## Tech Stack

### Frontend

- **React 19** with TypeScript
- **Vite** for build tooling
- **Tailwind CSS** for styling
- **Lucide React** for icons
- **Headless UI** for accessible components

### Backend

- **Express.js** - Web framework for Node.js
- **Node.js** - Runtime environment
- **TypeScript**
- **CORS** enabled for cross-origin requests
- **File-based storage** (JSON)

## Quick Start

### Prerequisites

- Node.js 18+
- npm

### Installation

### 1. Extract the ZIP

Unzip the folder you received into any location on your computer

2. **Install dependencies**

   ```bash
   # Install backend dependencies
   cd backend
   npm install

   # Install frontend dependencies
   cd ../frontend
   npm install
   ```

3. **Start the development servers**

   **Terminal 1 - Backend:**

   ```bash
   cd backend
   npm run dev
   ```

   Backend should run on `http://localhost:3000`
   if not possible, please change API_BASE in `frontend/api/vehicles.ts`

   **Terminal 2 - Frontend:**

   ```bash
   cd frontend
   npm run dev
   ```

   Frontend will typicly run on `http://localhost:5173`

4. **Open your browser**
   Navigate to `http://localhost:5173`

## 🧪 Testing

To run all tests, please first make sure Maintenance max is not reached.

### Backend API Tests

```bash
cd backend
npm test
```

The test suite validates:

- Post validity
- License plate validation (alphanumeric, length)
- Status transition rules
- Duplicate plates prevention
- Maintenance cap enforcement
- Delete restrictions

## API Endpoints

### Vehicles

- `GET /api/vehicles` - Get all vehicles
- `POST /api/vehicles` - Create new vehicle
- `PUT /api/vehicles/:id` - Update vehicle (status/plate)
- `DELETE /api/vehicles/:id` - Delete vehicle

## Configuration

### Environment Variables

- `PORT` - Backend server port (default: 3000)
- `BASE_URL` - API base URL for tests (default: http://localhost:3000)

### License Plate Validation

- **Format**: Alphanumeric only (A-Z, a-z, 0-9)
- **Length**: not empty
- **Normalization**: Converted to uppercase
- **Duplicates**: Case-insensitive duplicates prevention

## UI Features

### Vehicle Table

- **Sortable columns**: License Plate, Status, Created At
- **Expandable rows**: Action buttons for each vehicle
- **Filters & search**: Filter and search to find a specific vehicle

### Actions

- **Change Status**: Update vehicle status with validation
- **Edit License Plate**: Modify plate with format validation
- **Delete Vehicle**: Remove vehicle (Available only)

## Production Deployment

### Build for Production

```bash
# Build frontend
cd frontend
npm run build

# Build backend
cd ../backend
npm run build
```

### Start Production Server

```bash
cd backend
npm start
```

**Created by Assaf Dimor for Optibus home assignment**
