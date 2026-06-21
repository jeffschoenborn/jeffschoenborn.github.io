# Jeff Schoenborn Campaign Website
## Baltimore City Republican Central Committee

---

## Files

```
schoenborn-campaign/
├── index.html          ← Home page
├── about.html          ← About Jeff
├── issues.html         ← Issues & Positions
├── involved.html       ← Get Involved / Contact
├── styles.css          ← All shared styles
├── images/             ← Put your photos here (see below)
└── README.md           ← This file
```

---

## Deploying the Site

This site is plain HTML/CSS — no build step required.

**Option 1 – Netlify (recommended, free)**
1. Go to https://netlify.com and create a free account
2. Drag-and-drop this entire folder onto the Netlify dashboard
3. Your site goes live instantly. Connect a custom domain in Settings.

**Option 2 – GitHub Pages (free)**
1. Push this folder to a GitHub repository
2. Go to Settings → Pages → Deploy from branch
3. Choose `main` and root `/`

**Option 3 – Any web host**
Upload all files via FTP/SFTP to your host's `public_html` folder.
No server-side code required — works on any static host.

---

## Adding Your Photos

### Your Headshot (required)
1. Name your photo: `jeff.jpg`
2. Place it in the `images/` folder
3. In `index.html`, find this comment and replace:
   ```html
   <!-- Replace with: <img src="images/jeff.jpg" alt="Jeff Schoenborn" class="hero-photo" /> -->
   <div class="hero-photo-placeholder">...</div>
   ```
   Replace the entire `<div class="hero-photo-placeholder">` block with:
   ```html
   <img src="images/jeff.jpg" alt="Jeff Schoenborn" class="hero-photo" />
   ```
4. Do the same in `about.html` — find `photo-placeholder` and replace similarly.

### Baltimore Neighborhood / Background Photo (optional)
1. Name it: `baltimore-skyline.jpg` (or any Baltimore photo)
2. Place in `images/` folder
3. In `styles.css`, the `.hero-bg-img` rule already references `images/baltimore-skyline.jpg`
4. It will appear automatically as the hero background

### About Page / Neighborhood Photo
- In `about.html`, find `<div class="img-placeholder">` and replace with:
  ```html
  <img src="images/baltimore-neighborhoods.jpg" alt="Baltimore neighborhood" />
  ```

### Recommended Photo Specs
- Headshot: Portrait orientation, at least 600×800px, JPG or WebP
- Background/skyline: Landscape, at least 1400×800px, JPG

---

## Connecting the Contact Form

The contact form currently shows a success message but doesn't send data anywhere.
To make it functional:

**Easiest — Formspree (free tier)**
1. Go to https://formspree.io and create an account
2. Create a new form, get your form endpoint (looks like `https://formspree.io/f/xxxxx`)
3. In `involved.html`, replace the `handleSubmit()` function with:
   ```javascript
   async function handleSubmit() {
     const data = {
       firstName: document.getElementById('firstName').value,
       email: document.getElementById('email').value,
       // ... etc
     };
     const res = await fetch('https://formspree.io/f/YOUR_ID', {
       method: 'POST',
       headers: { 'Content-Type': 'application/json' },
       body: JSON.stringify(data)
     });
     if (res.ok) {
       document.getElementById('submitBtn').style.display = 'none';
       document.getElementById('formSuccess').style.display = 'block';
     }
   }
   ```

**Alternative — Netlify Forms**
If hosting on Netlify, add `netlify` attribute to the form tag and Netlify handles submissions automatically.

---

## Customization Quick Reference

| What to change | Where |
|---|---|
| Email address | `involved.html` — search for `jeff@schoenborn4baltimore.com` |
| Quote on home page | `index.html` — `<blockquote>` in `.intro-strip` |
| Years on committee | `index.html` — `hero-photo-badge` |
| Stats (16+ years, etc.) | `index.html` — `.bmore-stat` sections |
| Issue positions | `issues.html` — each `.issue-block` |
| Bio text | `about.html` — `.about-content` paragraphs |
| Color scheme | `styles.css` — `:root` CSS variables at top |

---

## Colors & Fonts

- **Navy** `#1B2A4A` — primary dark color
- **Gold** `#C4982A` — accent, highlights
- **Cream** `#F7F3EE` — page background
- **Fonts**: Playfair Display (headings) + Lora (body) + Barlow (UI labels)
  — loaded from Google Fonts (requires internet connection to display correctly)

To use local fonts (for offline/intranet use), download from fonts.google.com
and update the `@import` line at the top of `styles.css`.

---

*Built for Jeff Schoenborn — Baltimore City Republican Central Committee*
