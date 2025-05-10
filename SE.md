

## 🛠 1. **Creating CLI App using Python to Find Open Redirect (Using `requests` module)**

### 📘 What is an Open Redirect?

An open redirect vulnerability allows an attacker to redirect users to malicious sites using a vulnerable parameter in the URL.

### 🧰 Libraries Used:

* `requests`
* `sys` (for CLI arguments)
* `urllib.parse` (for URL parsing)

### 🔤 Sample Code:

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

### ✅ Example:

```bash
python3 open_redirect_finder.py https://example.com/redirect url
```

---

## 🌐 2. **Creating Web App Using PHP**

### 📘 What is a Web App?

A web application allows users to interact via browser. We'll create a simple form-based PHP app.

### 🔤 Sample Code:

**index.php**

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

**welcome.php**

```php
<?php
$name = htmlspecialchars($_POST['name']);
echo "Welcome, " . $name;
?>
```

### ✅ How to Run:

Place the files in `htdocs` folder (if using XAMPP) and access via:

```
http://localhost/index.php
```

---

## ⚙️ 3. **Creating API Using FastAPI**

### 📘 What is FastAPI?

FastAPI is a modern Python framework to build REST APIs.

### 🔤 Sample Code:

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

### ✅ Run with:

```bash
uvicorn main:app --reload
```

### 🔎 Access:

```
http://127.0.0.1:8000
http://127.0.0.1:8000/docs (Swagger UI)
```

---

## 🖥️ 4. **Creating GUI App Using Webview + Electron.js**

### 📘 What is Electron?

Electron allows building desktop GUI apps using web technologies.

### 🔤 Sample Code:

**Folder Structure**

```
electron-webview/
├── main.js
├── index.html
├── package.json
```

**package.json**

```json
{
  "name": "gui-app",
  "main": "main.js",
  "scripts": {
    "start": "electron ."
  },
  "devDependencies": {
    "electron": "^26.0.0"
  }
}
```

**main.js**

```javascript
const { app, BrowserWindow } = require('electron');
function createWindow() {
    const win = new BrowserWindow({ width: 800, height: 600 });
    win.loadFile('index.html');
}
app.whenReady().then(createWindow);
```

**index.html**

```html
<!DOCTYPE html>
<html>
<body>
    <h1>Hello from Electron!</h1>
</body>
</html>
```

### ✅ How to Run:

```bash
npm install
npm start
```

---

## 📱 5. **Creating Android Webview App (Java + Android Studio)**

### 📘 What is a WebView App?

It loads a website inside an Android app.

### 🔤 Sample Code:

**`MainActivity.java`**

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

**AndroidManifest.xml**

```xml
<uses-permission android:name="android.permission.INTERNET"/>
<application ...>
    <activity android:name=".MainActivity">
        <intent-filter>
            <action android:name="android.intent.action.MAIN"/>
            <category android:name="android.intent.category.LAUNCHER"/>
        </intent-filter>
    </activity>
</application>
```

### ✅ How to Run:

1. Open in Android Studio
2. Connect Emulator or Phone
3. Click "Run"

