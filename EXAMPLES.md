# Challenge Examples and Templates

## Example 1: Basic HTML Source Inspection

**Points**: 50

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Company Portal</title>
</head>
<body>
    <h1>Welcome to SecureCorp</h1>
    <p>Please login to continue</p>
    
    <!-- TODO: Remove this before production! -->
    <!-- Admin credentials: admin / CTF{s0urc3_c0d3_l34k} -->
    
    <form>
        <input type="text" placeholder="Username">
        <input type="password" placeholder="Password">
        <button>Login</button>
    </form>
</body>
</html>
```

**Flag**: `CTF{s0urc3_c0d3_l34k}`

---

## Example 2: JavaScript Console Debug

**Points**: 75

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>API Dashboard</title>
</head>
<body>
    <h1>API Status Dashboard</h1>
    <div id="status">Loading...</div>
    
    <script>
        // Debug mode enabled
        const DEBUG = true;
        
        if (DEBUG) {
            console.log('=== DEBUG MODE ===');
            console.log('API Key:', 'sk_live_abc123');
            console.log('Secret Token:', 'CTF{c0ns0l3_d3bug_m0d3}');
            console.log('==================');
        }
        
        document.getElementById('status').textContent = 'All systems operational';
    </script>
</body>
</html>
```

**Flag**: `CTF{c0ns0l3_d3bug_m0d3}`

---

## Example 3: Hidden DOM Elements

**Points**: 100

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>User Profile</title>
    <style>
        .hidden { display: none; }
        .invisible { visibility: hidden; opacity: 0; }
    </style>
</head>
<body>
    <h1>User Profile</h1>
    <p>Username: john_doe</p>
    <p>Email: john@example.com</p>
    
    <!-- Hidden admin panel -->
    <div class="hidden" id="admin-panel">
        <h2>Admin Panel</h2>
        <p>Access Code: <span data-flag="CTF{h1dd3n_d0m_3l3m3nt}">REDACTED</span></p>
    </div>
    
    <div class="invisible">
        Secret: CTF{1nv1s1bl3_but_th3r3}
    </div>
</body>
</html>
```

**Flags**: 
- `CTF{h1dd3n_d0m_3l3m3nt}` (in data attribute)
- `CTF{1nv1s1bl3_but_th3r3}` (in invisible div)

---

## Example 4: Network Request Headers

**Points**: 150

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Weather App</title>
</head>
<body>
    <h1>Weather Forecast</h1>
    <button onclick="fetchWeather()">Get Weather</button>
    <div id="weather"></div>
    
    <script>
        function fetchWeather() {
            fetch('https://api.weather.example.com/forecast', {
                method: 'GET',
                headers: {
                    'Content-Type': 'application/json',
                    'X-API-Key': 'weather_api_key_12345',
                    'X-Secret-Flag': 'CTF{n3tw0rk_r3qu3st_h34d3rs}',
                    'Authorization': 'Bearer token123'
                }
            })
            .then(() => {
                document.getElementById('weather').textContent = 'Sunny, 72°F';
            })
            .catch(err => {
                document.getElementById('weather').textContent = 'Error loading weather';
            });
        }
    </script>
</body>
</html>
```

**Flag**: `CTF{n3tw0rk_r3qu3st_h34d3rs}` (visible in Network tab)

---

## Example 5: LocalStorage/SessionStorage

**Points**: 150

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Settings Panel</title>
</head>
<body>
    <h1>Application Settings</h1>
    <p>Theme: Dark</p>
    <p>Language: English</p>
    
    <script>
        // Store user preferences
        localStorage.setItem('theme', 'dark');
        localStorage.setItem('language', 'en');
        localStorage.setItem('user_config', JSON.stringify({
            notifications: true,
            autoSave: true,
            apiEndpoint: 'https://api.example.com',
            secretKey: 'CTF{l0c4l_st0r4g3_s3cr3ts}'
        }));
        
        sessionStorage.setItem('session_token', 'CTF{s3ss10n_st0r4g3_t0k3n}');
    </script>
</body>
</html>
```

**Flags**: 
- `CTF{l0c4l_st0r4g3_s3cr3ts}` (in localStorage)
- `CTF{s3ss10n_st0r4g3_t0k3n}` (in sessionStorage)

---

## Example 6: Base64 Encoded

**Points**: 200

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Secure Login</title>
</head>
<body>
    <h1>Login Portal</h1>
    <form id="loginForm">
        <input type="text" id="username" placeholder="Username">
        <input type="password" id="password" placeholder="Password">
        <button type="submit">Login</button>
    </form>
    
    <script>
        // Encoded configuration
        const config = {
            apiUrl: 'https://api.example.com',
            version: '1.0.0',
            // Base64 encoded secret
            secret: atob('Q1RGe2I0czY0X2VuYzBkM2RfZmw0Z30='),
            // Another encoded value
            token: atob('Q1RGe2QzYzBkM19tM19tNHkwM30=')
        };
        
        console.log('Config loaded:', config);
        
        document.getElementById('loginForm').addEventListener('submit', (e) => {
            e.preventDefault();
            alert('Login functionality not implemented');
        });
    </script>
</body>
</html>
```

**Flags**: 
- `CTF{b4s64_enc0d3d_fl4g}` (decode from base64)
- `CTF{d3c0d3_m3_m4y03}` (decode from base64)

---

## Example 7: CSS Content Property

**Points**: 175

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Styled Page</title>
    <style>
        body::before {
            content: "CTF{css_c0nt3nt_pr0p3rty}";
            display: none;
        }
        
        .secret::after {
            content: "CTF{css_4ft3r_ps3ud0}";
            position: absolute;
            left: -9999px;
        }
    </style>
</head>
<body>
    <h1>Welcome</h1>
    <p class="secret">This page looks normal...</p>
</body>
</html>
```

**Flags**: 
- `CTF{css_c0nt3nt_pr0p3rty}` (in ::before pseudo-element)
- `CTF{css_4ft3r_ps3ud0}` (in ::after pseudo-element)

---

## Example 8: JavaScript Obfuscation

**Points**: 250

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Protected Page</title>
</head>
<body>
    <h1>Protected Content</h1>
    
    <script>
        // Obfuscated flag
        const _0x1a2b = ['Q1RG', 'e29i', 'ZnVz', 'Y2F0', 'ZWRf', 'amF2', 'YXNj', 'cmlw', 'dH0='];
        const _0x3c4d = (a, b) => a + b;
        const _0x5e6f = _0x1a2b.join('');
        const flag = atob(_0x5e6f);
        
        // Another layer
        const parts = ['CTF{', 'obfu', 'scat', 'ed_j', 'avasc', 'ript}'];
        const realFlag = parts.join('');
        
        console.log('System initialized');
        
        // Hidden in function
        function checkAuth() {
            const secret = String.fromCharCode(67,84,70,123,99,104,52,114,95,99,48,100,51,115,125);
            return secret;
        }
    </script>
</body>
</html>
```

**Flags**: 
- `CTF{obfuscated_javascript}` (decode base64 and join)
- `CTF{ch4r_c0d3s}` (from charCode)

---

## Example 9: Fake Login with Hardcoded Credentials

**Points**: 100

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Admin Login</title>
    <style>
        body { font-family: Arial; max-width: 400px; margin: 50px auto; }
        input { width: 100%; padding: 10px; margin: 10px 0; }
        button { width: 100%; padding: 10px; background: #007bff; color: white; border: none; }
    </style>
</head>
<body>
    <h2>Admin Login</h2>
    <form id="loginForm">
        <input type="text" id="username" placeholder="Username" required>
        <input type="password" id="password" placeholder="Password" required>
        <button type="submit">Login</button>
    </form>
    <div id="message"></div>
    
    <script>
        // Hardcoded credentials (bad practice!)
        const validCredentials = {
            username: 'admin',
            password: 'super_secret_123',
            flag: 'CTF{h4rdc0d3d_cr3d3nt14ls}'
        };
        
        document.getElementById('loginForm').addEventListener('submit', (e) => {
            e.preventDefault();
            const username = document.getElementById('username').value;
            const password = document.getElementById('password').value;
            
            if (username === validCredentials.username && 
                password === validCredentials.password) {
                document.getElementById('message').textContent = 
                    'Login successful! But the flag is: ' + validCredentials.flag;
            } else {
                document.getElementById('message').textContent = 'Invalid credentials';
            }
        });
    </script>
</body>
</html>
```

**Flag**: `CTF{h4rdc0d3d_cr3d3nt14ls}` (in JavaScript object)

---

## Example 10: Multi-Layer Challenge

**Points**: 300

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Ultimate Challenge</title>
    <style>
        .hint::before { content: "Part 1: Check HTML comments"; display: none; }
    </style>
</head>
<body>
    <h1>Multi-Layer Challenge</h1>
    <p class="hint">Find all 5 parts of the flag!</p>
    
    <!-- Part 1: CTF{ -->
    
    <div style="display:none" data-part="mult1_">Part 2 here</div>
    
    <script>
        // Part 3
        console.log('Part 3:', 'l4y3r_');
        
        // Part 4
        localStorage.setItem('part4', 'ch4ll');
        
        // Part 5
        const part5 = atob('M25nM30='); // 3ng3}
        
        // Combine all parts: CTF{mult1_l4y3r_ch4ll3ng3}
    </script>
</body>
</html>
```

**Flag**: `CTF{mult1_l4y3r_ch4ll3ng3}` (combine all 5 parts)

---

## Tips for Creating Challenges

1. **Start Simple**: Begin with HTML comments, progress to obfuscation
2. **Be Creative**: Use realistic scenarios (login pages, dashboards, APIs)
3. **Test Thoroughly**: Ensure flags are discoverable but not obvious
4. **Provide Hints**: Guide participants without giving away the answer
5. **Multiple Flags**: Hide bonus flags for extra points
6. **Document Solutions**: Keep notes on how to solve each challenge
7. **Vary Challenge Complexity**: Mix easier and harder challenges for different skill levels
8. **Use Themes**: Create related challenges that tell a story

## Testing Checklist

- [ ] Flag is hidden (not visible on page)
- [ ] Flag is discoverable with standard tools (DevTools)
- [ ] No syntax errors in HTML/JavaScript
- [ ] File is accessible at `/challenges/filename.html`
- [ ] Challenge added to database with correct flag
- [ ] Tested in fresh browser window
- [ ] Hints are helpful but not too revealing
