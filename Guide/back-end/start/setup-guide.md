# Basic Express.js Setup Guide

This guide provides the minimum setup to create a simple Express.js server.

## 1. Project Setup

```bash
# Create project directory and initialize npm
mkdir my-express-app
cd my-express-app
npm init -y
```

## 2. Install Dependencies

```bash
# Install Express
npm install express

# Install SQLite3 for database
npm install sqlite3

# Install development dependency
npm install --save-dev nodemon
```

## 3. Project Structure

Create the following directory structure:
```
src/
  ├── config/
  │   └── db.js
  └── index.js
```

## 4. Set Up Database Configuration

Create `src/config/db.js`:

```javascript
const sqlite3 = require('sqlite3').verbose();
const path = require('path');

// Database file path
const DB_PATH = path.join(__dirname, '../../database.sqlite');

// Create/connect to database
const db = new sqlite3.Database(DB_PATH, (err) => {
  if (err) {
    console.error('Error opening database:', err.message);
  } else {
    console.log('Connected to SQLite database');
  }
});

// Initialize database (create tables if needed)
db.serialize(() => {
  // Example: Create a simple test table
  db.run(`CREATE TABLE IF NOT EXISTS test (
    id INTEGER PRIMARY KEY AUTOINCREMENT,
    name TEXT NOT NULL,
    created_at DATETIME DEFAULT CURRENT_TIMESTAMP
  )`, (err) => {
    if (err) {
      console.error('Error creating table:', err.message);
    } else {
      console.log('Database initialized successfully');
    }
  });
});

module.exports = db;
```

## 5. Create the Express App

Create `src/index.js`:

```javascript
const express = require('express');
const db = require('./config/db');

const app = express();

// Middleware to parse JSON bodies (required for POST/PUT requests)
app.use(express.json());

// Basic route
app.get('/', (req, res) => {
  res.send('Hello, Express!');
});

const PORT = process.env.PORT || 4000;
app.listen(PORT, () => {
  console.log(`Server running on http://localhost:${PORT}`);
});
```

## 6. Update package.json Scripts

Add these scripts to your `package.json`:

```json
"scripts": {
  "start": "node src/index.js",
  "dev": "nodemon src/index.js"
}
```

## 7. Start the Server

```bash
# Development mode with hot-reload
npm run dev

# Production mode
npm start
```

## 8. Test the Application

Open your browser or use curl to test the endpoint:

```bash
curl http://localhost:4000
```

You should see: `Hello, Express!`

## 9. Verify Database Connection

After starting the server, you should see:
- `Connected to SQLite database`
- `Database initialized successfully`

Check that a `database.sqlite` file was created in your project root directory.

## 10. Next Step

- Implement CRUD operations (see `crud-implementation-guide.md`)
