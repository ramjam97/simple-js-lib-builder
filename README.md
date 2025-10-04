# 🧱 Simple JS Library Builder  
[![Node.js](https://img.shields.io/badge/Node.js-%3E%3D16.0.0-brightgreen)](https://nodejs.org/) 
[![License: ISC](https://img.shields.io/badge/License-ISC-blue.svg)](LICENSE)


**Author:** Ram Jam   
**GitHub:** https://github.com/ramjam97/js-lib-builder      
**Version:** `1.0.0`

A lightweight and reusable Node.js project template for building JavaScript libraries.
It automatically generates distributable files (``index.js``, ``index.min.js``, and documentation) and manages version folders based on your package.json configuration.

---

## 🚀 Features

- 🛠️ Simple structure for developing vanilla JS libraries   
- ⚡ Auto-builds and minifies your library using Terser
- 🧾 Auto-generates banner metadata (name, version, author, GitHub, description, and timestamp)
- 🗂️ Automatically creates versioned backups in ``/versions/<version>``
- 📦 Generates a clean /dist folder containing the latest build
- ✅ Works seamlessly with ES Modules

---

## 📁 Project Structure
```bash
js-lib-builder/
├── build.js          # The main builder script
├── package.json      # Library metadata and build configuration
├── src/
│   ├── index.js      # Your main source code (editable)
│   └── README.md     # Your library documentation (editable)
├── dist/             # Generated on build — contains the latest build
├── versions/         # Automatically created — stores historical versions
└── node_modules/     # Installed dependencies
```

---

## ⚙️ Getting Started
### 1. 🧩 Clone the Builder
```bash
git clone https://github.com/ramjam97/js-lib-builder.git
cd js-lib-builder
```

### 2. 📦 Install Dependencies
```bash
npm install
```
This installs **Terser**, which is used for code minification.

### 3. 🧠 Develop Your Library
Edit your main source file at:
```bash
src/index.js
```
and update the documentation at:
```bash
src/README.md
```
You can use ES Modules syntax since the project is configured with ``"type": "module"`` in package.json.

### 4. 🧰 Update Metadata
Open your ``package.json`` and modify these fields to match your library:
```json
{
  "name": "your-library-name",
  "version": "1.0.0",
  "description": "Short description of your library",
  "author": "Your Name",
  "git": "https://github.com/yourusername/your-repo",
}
```

### 5. 🏗️ Build Your Library
Run the build command:
```bash
npm run build
```

This will automatically:
- Create ``/dist`` and ``/versions/<version>`` folders
- Generate:
  - ``index.js``
  - ``index.min.js``
  - ``README.md``
- Add version banner headers
- Copy your documentation


---


## 📤 Output Summary
After building, your project will look like this:
```bash
dist/
├── index.js          # Non-minified build
├── index.min.js      # Minified build
└── README.md         # Library documentation

versions/
└── 1.0.0/
    ├── index.js
    ├── index.min.js
    └── README.md
```

Each build is timestamped and stored under ``/versions/<version>`` for easy version tracking.


---


## 🧾 Example Banner
Each generated JS file will begin with:
```js
/*!
 * YourLibraryName v1.0.0
 * Description: Library description
 * Author: Ram Jam
 * GitHub: https://github.com/ramjam97/js-lib-builder
 * Build Date: 2025-10-04 16:15:23 (Asia/Manila)
 */
```

---


## 📌 Tips for Reuse
To use this builder for a new library project:      

#### 1.  Clone the builder repository:
```bash
git clone https://github.com/ramjam97/js-lib-builder.git my-new-library
cd my-new-library
```

#### 2.  Update ``package.json`` info (name, version, description, etc.)
#### 3.  Write your new code in ``src/index.js``
#### 4.  Write your new documentation in ``src/README.md``
#### 5.  Run:
```bash
npm run build
```
#### 6.  Your distributable files will appear in ``/dist``.

## 📘 Example Workflow
```bash
# Step 1: Clone builder
git clone https://github.com/ramjam97/js-lib-builder.git my-lib
cd my-lib

# Step 2: Install dependencies
npm install

# Step 3: Update package.json and edit src/index.js

# Step 4: Build
npm run build

# Step 5: Check output
ls dist
# => index.js, index.min.js, README.md
```

---


## 🧩 Dependencies
| Package                                        | Purpose                        |
| ---------------------------------------------- | ------------------------------ |
| [terser](https://www.npmjs.com/package/terser) | Minify JS files for production |


---


## 💡 Bonus Tip: Host Your Library on jsDelivr CDN

Once your library is published on **GitHub**, you can serve it instantly through **jsDelivr CDN** — no npm publish or extra configuration required!


This allows developers (and you) to include your library directly in any web project using a simple `<script>` tag.


### 🌐 How to Deploy to jsDelivr
Follow these steps after building and committing your latest version:

#### 1.  Push your latest code to GitHub
```bash
git push origin master
```

#### 2. Tag your version release
Make sure the tag matches your library’s version in ``package.json`` (for example ``v3.0.0``):
```bash
git tag v3.0.0
```

#### 3. Push the tag to GitHub
```bash
git push origin v3.0.0
```

#### 4. Wait about a minute ⏱️
jsDelivr automatically scans GitHub repositories for new tags and hosts your files.

#### 4. Access your CDN link
Once processed, your library will be available using this URL pattern:
```text
https://cdn.jsdelivr.net/gh/<username>/<repository>@<version>/dist/<filename>.min.js
```

**Example (RamStateJs v3.0.0):**
```html
<script src="https://cdn.jsdelivr.net/gh/ramjam97/ram-state-js@v3.0.0/dist/ram-state.min.js"></script>
```

### 🧠 How It Works
When you push a Git tag like `v3.0.0`, jsDelivr:
- Detects the new tag in your public GitHub repo
- Caches the versioned files under that tag
- Makes them globally available through a CDN URL

This means every version you tag (`v3.0.1`, `v3.1.0`, etc.) gets its own CDN link that never changes or breaks.


### ✅ Example Integration

Once hosted, anyone can include your library via CDN:
```html
<!DOCTYPE html>
<html>
<head>
  <title>Using RamStateJs</title>
  <script src="https://cdn.jsdelivr.net/gh/ramjam97/ram-state-js@v3.0.0/dist/ram-state.min.js"></script>
</head>
<body>
  <script>
    console.log('RamStateJs loaded successfully!');
  </script>
</body>
</html>
```

> 💡 Tip:   
> Always tag stable versions (like `v1.0.0`, `v2.1.0`, etc.) after running npm run build.   
> This ensures the /dist folder in that tag contains your latest, production-ready build.


---
---


## 🧑‍💻 Author
Ram Jam   
📍 Philippines  
🔗 GitHub: [ramjam97](https://github.com/ramjam97)


## 📜 License
This project is licensed under the **ISC License** — free to use and modify.
