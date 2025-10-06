# 🚀 Deployment Guide: Publishing to krishkapoor.com on Porkbun

## SEO Improvements ✅

I've already optimized your website with:
- **Meta tags** for better search engine visibility
- **Open Graph tags** for social media sharing (Facebook, LinkedIn)
- **Twitter Card tags** for Twitter sharing
- **Structured data (JSON-LD)** to help Google understand your content
- **Updated sitemap.xml** with the current date
- **robots.txt** is already configured properly

---

## Option 1: GitHub Pages (Recommended - Free & Easy)

### Step 1: Create a GitHub Repository
1. Go to [GitHub](https://github.com) and create a new repository
2. Name it `portfolio` or `krishkapoor.com`
3. Make it public
4. Don't initialize with README

### Step 2: Push Your Code to GitHub
Open PowerShell in your project folder and run:

```powershell
git init
git add .
git commit -m "Initial commit"
git branch -M main
git remote add origin https://github.com/YOUR_USERNAME/YOUR_REPO_NAME.git
git push -u origin main
```

### Step 3: Enable GitHub Pages
1. Go to your repository on GitHub
2. Click **Settings** → **Pages**
3. Under "Source", select **main** branch
4. Click **Save**
5. GitHub will give you a URL like `https://YOUR_USERNAME.github.io/YOUR_REPO_NAME/`

### Step 4: Configure Custom Domain on Porkbun

#### In GitHub:
1. In GitHub Pages settings, add `krishkapoor.com` in the "Custom domain" field
2. Check "Enforce HTTPS" (after DNS propagates)

#### In Porkbun:
1. Log in to [Porkbun](https://porkbun.com)
2. Go to your domain `krishkapoor.com`
3. Click **DNS Records**
4. Add these records:

| Type  | Host | Answer/Value              | TTL  |
|-------|------|---------------------------|------|
| A     | @    | 185.199.108.153           | 600  |
| A     | @    | 185.199.109.153           | 600  |
| A     | @    | 185.199.110.153           | 600  |
| A     | @    | 185.199.111.153           | 600  |
| CNAME | www  | YOUR_USERNAME.github.io   | 600  |

5. Save the changes
6. Wait 5-30 minutes for DNS propagation

---

## Option 2: Netlify (Also Free, More Features)

### Step 1: Push to GitHub (same as above)

### Step 2: Deploy on Netlify
1. Go to [Netlify](https://netlify.com) and sign up/login with GitHub
2. Click **"Add new site"** → **"Import an existing project"**
3. Choose GitHub and select your repository
4. Build settings:
   - Build command: (leave empty)
   - Publish directory: `/` (or leave empty)
5. Click **Deploy**

### Step 3: Configure Custom Domain
1. In Netlify, go to **Domain settings**
2. Click **Add custom domain**
3. Enter `krishkapoor.com`
4. Netlify will show you DNS records

#### In Porkbun:
1. Go to DNS Records
2. Add these records (Netlify will provide exact values):

| Type  | Host | Answer/Value                    | TTL  |
|-------|------|---------------------------------|------|
| A     | @    | 75.2.60.5 (Netlify's IP)       | 600  |
| CNAME | www  | YOUR_SITE.netlify.app          | 600  |

3. Save and wait for DNS propagation
4. Enable HTTPS in Netlify (automatic with Let's Encrypt)

---

## Option 3: Vercel (Similar to Netlify)

### Step 1: Push to GitHub (same as above)

### Step 2: Deploy on Vercel
1. Go to [Vercel](https://vercel.com) and sign up with GitHub
2. Click **"Add New Project"**
3. Import your GitHub repository
4. Click **Deploy**

### Step 3: Configure Custom Domain
1. Go to **Settings** → **Domains**
2. Add `krishkapoor.com`
3. Vercel will show DNS instructions

#### In Porkbun:
Add these records:

| Type  | Host | Answer/Value              | TTL  |
|-------|------|---------------------------|------|
| A     | @    | 76.76.19.61 (Vercel IP)  | 600  |
| CNAME | www  | cname.vercel-dns.com     | 600  |

---

## Option 4: Traditional Web Hosting (Porkbun Hosting or cPanel)

If you want to use Porkbun's web hosting or any cPanel hosting:

### Step 1: Get Hosting
- Purchase web hosting from Porkbun or another provider
- They'll give you FTP/SFTP credentials

### Step 2: Upload Files
1. Use an FTP client like [FileZilla](https://filezilla-project.org/)
2. Connect using your hosting credentials
3. Upload all files to the `public_html` or `www` folder:
   - `index.html`
   - `1712653530874 (2).jpeg`
   - `robots.txt`
   - `sitemap.xml`

### Step 3: Configure DNS (if needed)
If your hosting is not with Porkbun, update DNS A records to point to your hosting server's IP.

---

## Post-Deployment: SEO Checklist

After your site is live:

### 1. Submit to Google Search Console
1. Go to [Google Search Console](https://search.google.com/search-console)
2. Add property for `https://krishkapoor.com`
3. Verify ownership (via DNS TXT record or HTML file)
4. Submit your sitemap: `https://krishkapoor.com/sitemap.xml`

### 2. Submit to Bing Webmaster Tools
1. Go to [Bing Webmaster Tools](https://www.bing.com/webmasters)
2. Add and verify your site
3. Submit sitemap

### 3. Test Your Website
- **PageSpeed Insights**: https://pagespeed.web.dev/
- **Mobile-Friendly Test**: https://search.google.com/test/mobile-friendly
- **Rich Results Test**: https://search.google.com/test/rich-results (for structured data)
- **Open Graph Preview**: https://www.opengraph.xyz/

### 4. Create a favicon
Your site references `/favicon.ico` but you don't have one yet:
1. Create a 512x512px or 1024x1024px image
2. Use [Favicon Generator](https://favicon.io/) to create all sizes
3. Add the generated files to your root directory

### 5. Monitor Performance
- Set up Google Analytics (optional)
- Use Google Search Console to monitor:
  - Indexing status
  - Search performance
  - Mobile usability
  - Core Web Vitals

---

## Recommended: GitHub Pages + Netlify/Vercel

**My recommendation**: Use **GitHub Pages** or **Netlify/Vercel** because:
- ✅ **Free** hosting with HTTPS
- ✅ **Automatic deployments** when you push to GitHub
- ✅ **Global CDN** for fast loading worldwide
- ✅ **Built-in SSL** certificates
- ✅ **No server management** needed

---

## Quick Start Commands

If you choose GitHub Pages, here's the complete workflow:

```powershell
# Initialize git (if not already done)
git init

# Add all files
git add .

# Commit
git commit -m "Initial deployment"

# Add your GitHub remote (replace with your repo URL)
git remote add origin https://github.com/YOUR_USERNAME/YOUR_REPO.git

# Push to GitHub
git branch -M main
git push -u origin main
```

Then configure DNS on Porkbun as shown above!

---

## Need Help?

If you run into issues:
1. Check DNS propagation: https://dnschecker.org/
2. Verify GitHub Pages is enabled in your repo settings
3. Make sure the custom domain is added in GitHub Pages settings
4. Wait up to 24-48 hours for DNS changes to fully propagate (usually much faster)

---

**Good luck with your deployment! 🚀**

