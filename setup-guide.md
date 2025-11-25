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

# Install development dependency
npm install --save-dev nodemon
```

## 3. Project Structure

Create the following directory structure:
```
src/
  └── index.js
```

## 4. Create the Express App

Create `src/index.js`:

```javascript
const express = require('express');

const app = express();

// Basic route
app.get('/', (req, res) => {
  res.send('Hello, Express!');
});

const PORT = process.env.PORT || 4000;
app.listen(PORT, () => {
  console.log(`Server running on http://localhost:${PORT}`);
});
```

## 5. Update package.json Scripts

Add these scripts to your `package.json`:

```json
"scripts": {
  "start": "node src/index.js",
  "dev": "nodemon src/index.js"
}
```

## 6. Start the Server

```bash
# Development mode with hot-reload
npm run dev

# Production mode
npm start
```

## 7. Test the Application

Open your browser or use curl to test the endpoint:

```bash
curl http://localhost:4000
```

You should see: `Hello, Express!`

## 8. Next Steps

- Add more routes
- Implement error handling
- Add middleware (logging, CORS, etc.)
- Connect to a database
- Add environment variables
- Set up testing
- Add API documentation
