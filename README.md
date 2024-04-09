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
Copy the provided code into their respective files within the project directory, matching the file structure given in the hands-on lab.

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