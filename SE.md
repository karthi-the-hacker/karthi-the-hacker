
## 🛠 1. **Creating CLI App using Python to Find Open Redirect (Using `requests` module)**

### 📘 What is an Open Redirect?

An open redirect vulnerability allows attackers to redirect users to malicious sites using a vulnerable parameter in the URL.

### 📦 Install Requirements:

```bash
pip install requests
```

### 🧰 Libraries Used:

* `requests`
* `sys` (built-in)
* `urllib.parse` (built-in)

### 🔤 Sample Code (save as `open_redirect_finder.py`):

```python
import requests
import sys
from urllib.parse import urljoin

def check_open_redirect(base_url, param):
    payload = "https://evil.com"
    full_url = f"{base_url}?{param}={payload}"
    try:
        response = requests.get(full_url, allow_redirects=False)
        if 'Location' in response.headers and payload in response.headers['Location']:
            print(f"[VULNERABLE] {full_url}")
        else:
            print(f"[SAFE] {full_url}")
    except Exception as e:
        print(f"[ERROR] {e}")

if __name__ == "__main__":
    if len(sys.argv) != 3:
        print("Usage: python3 open_redirect_finder.py <url> <parameter>")
    else:
        check_open_redirect(sys.argv[1], sys.argv[2])
```

### ✅ Run:

```bash
python3 open_redirect_finder.py https://example.com/redirect url
```

---

## 🌐 2. **Creating Web App Using PHP**

### 📘 What is a Web App?

A web application interacts with users via a browser. We'll create a simple form-based app.

### 🛠 Setup Instructions:

1. Install XAMPP or any local server (Apache + PHP).
2. Place the files in the `htdocs` folder.

### 🔤 Files:

**`index.php`**

```php
<!DOCTYPE html>
<html>
<body>
    <form method="POST" action="welcome.php">
        <input type="text" name="name" placeholder="Enter your name"/>
        <input type="submit" value="Submit"/>
    </form>
</body>
</html>
```

**`welcome.php`**

```php
<?php
$name = htmlspecialchars($_POST['name']);
echo "Welcome, " . $name;
?>
```

### ✅ Run:

Open browser and go to:

```
http://localhost/index.php
```

---

## ⚙️ 3. **Creating API Using FastAPI**

### 📘 What is FastAPI?

FastAPI is a modern Python web framework for building APIs.

### 📦 Install Requirements:

```bash
pip install fastapi uvicorn
```

### 🧰 Sample Code (save as `main.py`):

```python
from fastapi import FastAPI

app = FastAPI()

@app.get("/")
def read_root():
    return {"message": "Hello World"}

@app.get("/greet/{name}")
def greet(name: str):
    return {"message": f"Hello {name}"}
```

### ✅ Run:

```bash
uvicorn main:app --reload
```

### 🔎 Access:

* Swagger UI: [http://127.0.0.1:8000/docs](http://127.0.0.1:8000/docs)
* API: [http://127.0.0.1:8000](http://127.0.0.1:8000)

---

## 🖥️ 4. **Creating GUI App Using Webview + Electron.js**

### 📘 What is Electron?

Electron lets you build cross-platform desktop apps using web technologies.

### 🛠 Setup Instructions:

1. Install Node.js
2. Create project folder:

```bash
mkdir electron-webview && cd electron-webview
npm init -y
npm install electron --save-dev
```

### 🔤 Files:

**`package.json`**

Add script inside `"scripts"`:

```json
"scripts": {
  "start": "electron ."
}
```

**`main.js`**

```javascript
const { app, BrowserWindow } = require('electron');

function createWindow() {
    const win = new BrowserWindow({ width: 800, height: 600 });
    win.loadFile('index.html');
}

app.whenReady().then(createWindow);
```

**`index.html`**

```html
<!DOCTYPE html>
<html>
<body>
    <h1>Hello from Electron!</h1>
</body>
</html>
```

### ✅ Run:

```bash
npm start
```

---

## 📱 5. **Creating Android Webview App (Java + Android Studio)**

### 📘 What is a WebView App?

It’s a native Android app that loads a website inside a WebView.

### 🛠 Project Setup:

1. Open Android Studio → New Project → Select **Empty Activity**
2. In `MainActivity.java`, use this code:

```java
package com.example.webviewapp;

import android.os.Bundle;
import android.webkit.WebView;
import android.webkit.WebViewClient;
import androidx.appcompat.app.AppCompatActivity;

public class MainActivity extends AppCompatActivity {
    WebView webview;

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        webview = new WebView(this);
        webview.setWebViewClient(new WebViewClient());
        webview.getSettings().setJavaScriptEnabled(true);
        webview.loadUrl("https://example.com");
        setContentView(webview);
    }
}
```

3. In `AndroidManifest.xml`, add:

```xml
<uses-permission android:name="android.permission.INTERNET" />
```

### ✅ Run:

* Connect Emulator or Android Device
* Click **Run** in Android Studio


