# CTF Challenge Files

This directory contains static HTML files and downloadable resources for CTF challenges.

## Directory Structure

```
server/public/challenges/
├── README.md                      # This file
├── example-web-challenge.html     # Example challenge with hidden flags
└── [your-challenge-files]         # Add your challenge files here
```

## How to Create a Challenge

### 1. Create Your Challenge HTML/Files

Place your HTML files or downloadable resources in this directory. These files will be served at:
- `{{PUBLIC_URL}}/challenges/your-file.html`
- `{{PUBLIC_URL}}/challenges/your-download.zip`

Note: The `{{PUBLIC_URL}}` is configured in your `.env` file (e.g., `http://localhost:3001` for development or `https://hit.techfoss.live` for production).

### 2. Hide the Flag

You can hide flags in multiple ways:

#### A. Hidden in HTML Source
```html
<!-- Flag: CTF{h1dd3n_1n_c0mm3nt} -->
<div style="display:none">CTF{h1dd3n_1n_d1v}</div>
<div class="hidden" data-flag="CTF{d4t4_4ttr1but3}"></div>
```

#### B. Hidden in JavaScript Console
```javascript
console.log('Debug info:', { flag: 'CTF{c0ns0l3_fl4g}' });
```

#### C. Hidden in Network Requests
```javascript
fetch('/api/data', {
    headers: { 'X-Flag': 'CTF{n3tw0rk_h34d3r}' }
});
```

#### D. Hidden in LocalStorage/SessionStorage
```javascript
localStorage.setItem('config', JSON.stringify({
    flag: 'CTF{st0r4g3_fl4g}'
}));
```

#### E. Obfuscated in JavaScript
```javascript
const flag = atob('Q1RGe2I0czY0X2VuYzBkM2R9'); // CTF{b4s64_enc0d3d}
```

### 3. Add Challenge to Database

Update your database with the challenge details:

```sql
INSERT INTO challenges (
    title, 
    description, 
    points, 
    flag,
    external_link,
    download_file_url
) VALUES (
    'Web Inspector Challenge',
    'Inspect this webpage carefully. The flag is hidden somewhere...',
    100,
    'CTF{1nsp3ct_th3_s0urc3_luk3}',
    '{{PUBLIC_URL}}/challenges/example-web-challenge.html',
    NULL
);
```

### 4. Field Usage

- **external_link**: URL to an HTML page or external resource (opens in new tab)
- **download_file_url**: URL to a downloadable file (ZIP, PDF, etc.)
- Both fields are optional - only buttons for provided URLs will be shown

## Security Notes

1. **Never expose flags directly** - Always hide them in a way that requires inspection/analysis
2. **Files are publicly accessible** - Don't put sensitive information in this directory
3. **No directory listing** - Users cannot browse the directory, only access known files
4. **CORS enabled** - These files can be accessed from the web frontend

## Example Challenges

### Easy: HTML Source Inspection
- Hide flag in HTML comments or hidden divs
- Participants use browser DevTools

### Medium: JavaScript Analysis
- Obfuscate flag in JavaScript code
- Require console inspection or code analysis

### Hard: Network Analysis
- Hide flag in HTTP headers or request payloads
- Require Network tab inspection

## Testing Your Challenge

1. Place your file in this directory
2. Restart the server (or it will auto-reload in dev mode)
3. Access at: `{{PUBLIC_URL}}/challenges/your-file.html` (PUBLIC_URL is set in .env)
4. Test that the flag is properly hidden but discoverable
5. Add the challenge to the database with the correct URL

## Tips

- Make challenges progressively harder
- Provide hints in the challenge description
- Test with fresh eyes - is the flag too easy or too hard to find?
- Consider multiple flags in one challenge for bonus points
- Use realistic scenarios (fake login pages, API docs, etc.)
