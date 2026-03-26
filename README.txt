╔══════════════════════════════════════════════════════════════════════╗
║        ZETA INTERNATIONAL — WEBSITE DEPLOYMENT PACKAGE              ║
║                    zetalink.com / zetainternational.com              ║
╚══════════════════════════════════════════════════════════════════════╝

WHAT IS THIS?
─────────────
This is a complete, standalone website. NO build tools, NO Node.js,
NO server-side language required. It runs on ANY web hosting that
serves HTML files (cPanel, FTP, Netlify, Apache, Nginx, etc.)

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
  FOLDER CONTENTS
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

  index.html          ← THE ENTIRE WEBSITE (1 file — HTML + CSS + JS)
  .htaccess           ← Apache server config (cPanel hosting)
  images/
    europe-bg.jpg     ← Milan Cathedral / Europe hero image
    tunisia-bg.jpg    ← Sidi Bou Said / Tunisia hero image
    hero-bg.jpg       ← Fallback hero image
  README.txt          ← This file

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
  DEPLOYMENT — cPANEL / FTP (Standard shared hosting)
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

  STEP 1: Log into your hosting cPanel
  STEP 2: Open "File Manager"
  STEP 3: Navigate to public_html/ (or httpdocs/ or www/)
  STEP 4: Delete any existing index.html or index.php
  STEP 5: Upload ALL files and the images/ folder:
            - index.html
            - .htaccess
            - images/ (entire folder with 3 images)
  STEP 6: Done. Visit your domain — the site is live.

  NOTE: .htaccess is a hidden file. Make sure "Show Hidden Files"
        is enabled in your FTP client or File Manager.

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
  DEPLOYMENT — NETLIFY (Free, drag & drop)
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

  STEP 1: Go to https://app.netlify.com → Sign up free
  STEP 2: Click "Add new site" → "Deploy manually"
  STEP 3: Drag and drop the entire zeta-deploy/ FOLDER onto the page
  STEP 4: Site is live instantly at a Netlify URL
  STEP 5: Add your custom domain in Site Settings → Domains

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
  DEPLOYMENT — NGINX SERVER (VPS/Dedicated)
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

  STEP 1: Upload all files to /var/www/zetainternational/
  STEP 2: Configure Nginx (see nginx.conf block below)
  STEP 3: sudo nginx -t && sudo systemctl reload nginx

  Nginx config block:
  ──────────────────
  server {
      listen 80;
      server_name zetainternational.com www.zetainternational.com;
      root /var/www/zetainternational;
      index index.html;
      location / {
          try_files $uri $uri/ /index.html;
      }
      location ~* \.(jpg|jpeg|png|css|js)$ {
          expires 30d;
          add_header Cache-Control "public, no-transform";
      }
  }

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
  HOW TO MODIFY CONTENT
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

  Open index.html in any text editor (VS Code, Notepad++, etc.)

  CHANGE TEXT:
    Find the TRANSLATIONS object near the bottom of the file.
    Each language (en/fr/it) has all text as key-value pairs.
    Example: change 'hero-h1b': 'Zeta Link'  to  'hero-h1b': 'Zeta International'

  CHANGE COLORS:
    Find :root { at the top of the <style> block.
    --gold: #c9a84c   ← change this to any color
    --navy: #0a0f1e   ← change the dark background

  CHANGE IMAGES:
    Replace the files in the images/ folder with your own JPGs.
    Keep the SAME filenames:
      images/europe-bg.jpg   (recommended: 1920×1080, under 500KB)
      images/tunisia-bg.jpg  (recommended: 1920×1080, under 500KB)

  ADD MORE SLIDESHOW IMAGES:
    In the HTML, duplicate a <div class="hero-slide"> block.
    Add a new <button class="hero-dot"> for the new slide.
    Update totalSlides = 2  to  totalSlides = 3
    Add the new caption to the slideCaptions array.

  CHANGE CONTACT INFO:
    Search for "Tunis, Tunisia" — replace with your actual address.
    Search for "info@zetalink.com" — replace with your email.
    Search for "+216 XX XXX XXX" — replace with your phone.

  CHANGE PAGE TITLE / SEO:
    Find <title> near the top and update it.
    Find <meta name="description"> and update the description.

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
  CONTACT FORM — HOW TO MAKE IT SEND EMAILS
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

  This package is pure HTML — the contact form does not send emails
  by default. Choose one of these free options:

  OPTION A — Formspree (easiest, free):
    1. Go to https://formspree.io and create a free account
    2. Create a new form, copy your form endpoint URL
    3. In index.html, find:
         <form class="contact-form" onsubmit="return false">
       Replace with:
         <form class="contact-form" action="https://formspree.io/f/YOUR_ID" method="POST">

  OPTION B — Web3Forms (free, no account needed):
    1. Go to https://web3forms.com — enter your email, get an access key
    2. In index.html, find the <form> tag and change to:
         <form class="contact-form" action="https://api.web3forms.com/submit" method="POST">
    3. Add inside the form (before the first input):
         <input type="hidden" name="access_key" value="YOUR_ACCESS_KEY">

  OPTION C — EmailJS (free tier, JavaScript):
    1. Go to https://emailjs.com — set up a service + template
    2. Update the form's onsubmit handler in the <script> section

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
  REQUIREMENTS
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

  ✓ Any web hosting that serves HTML files
  ✓ Internet connection (loads Google Fonts — Cormorant + Inter)
  ✗ No PHP required
  ✗ No MySQL/database required
  ✗ No Node.js required
  ✗ No build process required

  OFFLINE FONTS (optional):
  If you want the site to work without internet, download the fonts:
  https://fonts.google.com/specimen/Cormorant+Garamond
  https://fonts.google.com/specimen/Inter
  Place them in a fonts/ folder and update the @import in index.html.

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
  © 2025 Zeta International Group · All Rights Reserved
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
