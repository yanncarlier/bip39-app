This project is a derivative work, inspired by and built upon the original code from the repository at https://github.com/iancoleman/bip39. The application, bip39-app, serves as a wrapper around this codebase, adapting it for cross-platform use.

Or you can use it on line here:  
https://yanncarlier.github.io/bip39-app/  

I also changed the CSS to have the theme dark.



# Cross-Platform Framework

Electron is an excellent choice because it:

- Supports building applications for Windows, macOS, and Linux from a single codebase.
- Provides tools to package the application into platform-specific formats, including AppImage for Linux.
- Uses familiar web technologies, making development accessible if you're comfortable with HTML, CSS, and JavaScript.


Test the Application: Run the app locally to ensure it works:

   bash

   ```bash
   npm i
   npm start  
   npm run package  
   npm run build
   ```

# Package the Application for All Platforms

To create distributables, including an AppImage for Linux, use electron-builder:

1. Install electron-builder:

   bash

   ```bash
   npm install --save-dev electron-builder
   ```


   - linux: Targets AppImage, which is a portable format for Linux with a .AppImage extension.
   - win: Targets an installer (NSIS) for Windows, producing an .exe.
   - mac: Targets a disk image (DMG) for macOS.

3. Build the Application:

   - For Linux (AppImage):

     bash

     ```bash
     npx electron-builder --linux
     ```

     This generates an AppImage file (e.g., MyApp-x.y.z.AppImage) in the dist folder.

   - For Windows:

     bash

     ```bash
     npx electron-builder --win
     ```

   - For macOS:

     bash

     ```bash
     npx electron-builder --mac
     ```

   Note: Building for all platforms may require running these commands on the respective operating systems or using a CI/CD pipeline with cross-compilation support. For simplicity, you can assume access to the necessary environments.

# Step 5: Test Across Platforms

- Linux: Run the .AppImage file by making it executable (chmod +x bip39-app-0.5.6.AppImage) and executing it (./bip39-app-0.5.6.AppImage).
- Windows: Install or run the .exe file.
- macOS: Open the .dmg file and drag the app to the Applications folder, then launch it.

Key Considerations

- AppImage Specificity: The .AppImage extension is Linux-specific, so it applies only to the Linux version. For Windows and macOS, you’ll use their respective formats (.exe and .dmg/.app).
- Cross-Platform Compatibility: Ensure your application logic avoids OS-specific features unless handled appropriately via Electron’s APIs.
- Size: Electron apps include Chromium and Node.js, making them larger than some alternatives, but this trade-off enables broad compatibility.

