# electron-starter
A toy desktop application using native UI components for teaching the development of OAuth workflow between desktop app via web-based API. 
To run the Electron application from the previous hands-on lab, students would need to follow these steps, which you can include in the handout:

### Step 1: Install Node.js
Make sure Node.js is installed on the system. It can be downloaded from [nodejs.org](https://nodejs.org/).

### Step 2: Set Up the Electron Project
1. **Create a Project Directory**: If not already done, create a directory for the Electron project and navigate into it.
   ```bash
   mkdir electron-starter
   cd electron-starter
   ```

2. **Initialize the Project**: Initialize the project with `npm` to create a `package.json` file.
   ```bash
   npm init -y
   ```

3. **Install Electron**: Install Electron as a dependency.
   ```bash
   npm install electron --save-dev
   ```

### Step 3: Add the Provided Code
Follow this step to  a window using Electron's native window capabilities.

**File Structure:**
```
electron-starter/
|-- package.json
|-- main.js
|-- preload.js
|-- index.html
|-- renderer.js
|-- styles.css
```

**`package.json`:**
```json
{
  "name": "electron-starter",
  "version": "1.0.0",
  "description": "A simple Electron app for desktop authentication without a web browser UI.",
  "main": "main.js",
  "scripts": {
    "start": "electron ."
  },
  "keywords": [],
  "author": "Worwan",
  "license": "ISC",
  "dependencies": {
    "electron": "^15.0.0"
  }
}
```

**`main.js`:**
```javascript
const { app, BrowserWindow } = require('electron');
const path = require('path');

function createWindow() {
  // Create the browser window.
  const mainWindow = new BrowserWindow({
    width: 800,
    height: 600,
    webPreferences: {
      preload: path.join(__dirname, 'preload.js')
    }
  });

  // Load the index.html of the app.
  mainWindow.loadFile('index.html');
}

app.whenReady().then(() => {
  createWindow();
  
  app.on('activate', () => {
    if (BrowserWindow.getAllWindows().length === 0) createWindow();
  });
});

app.on('window-all-closed', () => {
  if (process.platform !== 'darwin') app.quit();
});
```

**`preload.js`:**
```javascript
window.addEventListener('DOMContentLoaded', () => {
  // All Node.js APIs are available in this preload script.
  // It has the same sandbox as a Chrome extension.
});
```

**`index.html`:**
```html
<!DOCTYPE html>
<html>
  <head>
    <meta charset="UTF-8">
    <title>Electron Starter</title>
    <link rel="stylesheet" type="text/css" href="styles.css">
  </head>
  <body>
    <h1>Welcome to Electron Starter</h1>
    <div id="auth-status">
      <p>Authentication status will appear here.</p>
    </div>
    <script src="renderer.js"></script>
  </body>
</html>
```

**`renderer.js`:**
```javascript
// This file is required by the index.html file and will
// be executed in the renderer process for that window.
// All of the Node.js APIs are available in this process.
```

**`styles.css`:**
```css
body {
  font-family: Arial, sans-serif;
  display: flex;
  justify-content: center;
  align-items: center;
  height: 100vh;
  margin: 0;
}

h1 {
  color: #333;
}
```

This is a basic setup for an Electron application with a native-looking interface. It creates a single window and loads an HTML file that will serve as the UI for the application. The `renderer.js` file is where you would control the elements on the page and handle events. To authenticate users, you would implement an authentication flow using Electron's IPC (inter-process communication) to securely handle tokens and credentials.

### Step 4: Run the Application
1. **Start the Application**: Use the npm start script defined in `package.json` to run the application.
   ```bash
   npm start
   ```

This command will launch Electron and open the main window of the desktop application, as defined in `main.js`.

### Troubleshooting Tips:
- If students encounter an error where Electron cannot be found, they should ensure they're in the correct project directory and have run `npm install`.
- If the application window does not appear, students should check the `main.js` file for any errors and ensure that `index.html` is in the correct location.
- Students should make sure all file paths are correct, and there are no typos in the file names or extensions.

By running these steps, students will be able to see their Electron application in action and proceed with the lab exercises.
