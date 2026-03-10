---
name: "html-to-image"
description: "Convert HTML files to PNG images using Puppeteer Core. Invoke when user wants to screenshot, export, or convert HTML/charts to images."
---

# HTML to Image Converter

This skill converts local HTML files into high-quality PNG images using `puppeteer-core` and the system's installed Google Chrome. This approach is robust because it avoids downloading Chromium and works with the existing browser.

## Dependencies

This skill requires:
1.  Node.js installed
2.  `puppeteer-core` package
3.  Google Chrome installed at standard location (macOS: `/Applications/Google Chrome.app`)

## How to Use

1.  **Check/Install Dependencies**:
    Ensure `puppeteer-core` is installed in the project.
    ```bash
    npm list puppeteer-core || npm install puppeteer-core
    ```

2.  **Create Script**:
    Create a temporary script (e.g., `screenshot-tool.js`) with the following content.

3.  **Run Script**:
    Execute with `node screenshot-tool.js`.

## Script Template

Use this template to generate the screenshot script. Replace `TARGET_HTML_FILE` and `OUTPUT_PNG_FILE` with actual paths.

```javascript
const puppeteer = require('puppeteer-core');
const path = require('path');
const fs = require('fs');

// Configuration
const HTML_FILE = 'TARGET_HTML_FILE'; // e.g., 'chart.html'
const OUTPUT_FILE = 'OUTPUT_PNG_FILE'; // e.g., 'chart.png'
const WIDTH = 1400;
const HEIGHT = 1200; // Initial height, will resize to full page

(async () => {
  try {
    // 1. Find Chrome Executable
    const chromePath = '/Applications/Google Chrome.app/Contents/MacOS/Google Chrome';
    if (!fs.existsSync(chromePath)) {
      console.error('Error: Google Chrome not found at ' + chromePath);
      process.exit(1);
    }

    // 2. Launch Browser
    const browser = await puppeteer.launch({
      executablePath: chromePath,
      headless: true,
      args: ['--no-sandbox', '--disable-setuid-sandbox'] // Safer for CI/container envs
    });

    const page = await browser.newPage();
    
    // 3. Set Viewport
    await page.setViewport({ width: WIDTH, height: HEIGHT, deviceScaleFactor: 2 });

    // 4. Navigate to File
    const fileUrl = 'file://' + path.resolve(HTML_FILE);
    console.log(`Navigating to: ${fileUrl}`);
    
    await page.goto(fileUrl, { 
      waitUntil: 'networkidle0', // Wait until network is idle (no loading)
      timeout: 30000 
    });

    // 5. Screenshot
    await page.screenshot({ 
      path: OUTPUT_FILE, 
      fullPage: true 
    });
    
    console.log(`Successfully saved screenshot to: ${OUTPUT_FILE}`);

    await browser.close();
  } catch (error) {
    console.error('Screenshot failed:', error);
    process.exit(1);
  }
})();
```

## Troubleshooting

*   **Chrome not found**: Check if Chrome is installed in `/Applications`. If using Edge or Brave, update `executablePath`.
*   **Permissions**: Ensure the terminal has disk access.
*   **Timeout**: If the page has heavy animations, increase `timeout` or change `waitUntil` to `domcontentloaded`.
