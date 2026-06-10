# Deployment Guide

This guide walks you through deploying your portfolio website to make it live on the internet.

## Option 1: GitHub Pages (Recommended - Free)

### Prerequisites
- A GitHub account (free at github.com)
- Git installed on your computer (git-scm.com)

### Step 1: Create a GitHub Repository

1. Go to **github.com**
2. Sign in or create an account
3. Click the **+** icon → **New repository**
4. Repository name: `portfolio` (or your preferred name)
5. Add description: "Semantic HTML5 portfolio website with accessibility and SEO"
6. Choose **Public** (so others can access it)
7. Click **Create repository**

### Step 2: Push Your Code to GitHub

#### Option A: Using Command Line (Recommended)

1. Open Terminal/PowerShell in your project folder
2. Run these commands:

```bash
# Initialize git repository
git init

# Add all files
git add .

# Create initial commit
git commit -m "Initial commit: Semantic HTML5 portfolio with accessibility"

# Add GitHub as remote (replace USERNAME/REPO with yours)
git remote add origin https://github.com/USERNAME/portfolio.git

# Push to GitHub
git branch -M main
git push -u origin main
```

3. If prompted for credentials:
   - Use your GitHub username
   - Use a Personal Access Token as password (github.com/settings/tokens)

#### Option B: Using GitHub Desktop (GUI)

1. Download GitHub Desktop (desktop.github.com)
2. Sign in with your GitHub account
3. Click **File** → **Clone Repository**
4. Select your newly created repository
5. Click **Create a branch**
6. Make changes to your files
7. Write a commit message
8. Click **Commit to main**
9. Click **Publish branch**

#### Option C: Upload via GitHub Web Interface

1. Open your repository on GitHub
2. Click **Add file** → **Upload files**
3. Drag and drop your portfolio files
4. Write commit message
5. Click **Commit changes**

### Step 3: Enable GitHub Pages

1. Go to your repository on GitHub
2. Click **Settings** (top right)
3. Click **Pages** (left sidebar)
4. Under "Source" section:
   - Select **Branch**: main
   - Select folder: root (/)
   - Click **Save**
5. GitHub will show your site URL (usually `https://username.github.io/portfolio`)

### Step 4: Update Canonical URLs

After getting your GitHub Pages URL, update the `<link rel="canonical">` tags:

In each HTML file, update:
```html
<!-- Before -->
<link rel="canonical" href="https://vijayportfolio.com/">

<!-- After -->
<link rel="canonical" href="https://username.github.io/portfolio/">
```

Also update in meta tags:
```html
<!-- Update og:url -->
<meta property="og:url" content="https://username.github.io/portfolio/">

<!-- Update twitter:url -->
<meta name="twitter:url" content="https://username.github.io/portfolio/">
```

### Step 5: Verify Your Site

1. Wait 2-3 minutes for GitHub to process
2. Visit your GitHub Pages URL in browser
3. Verify all pages load correctly
4. Test keyboard navigation
5. Check that all links work

### Updating Your Site

After making changes to your files:

```bash
# See what changed
git status

# Add changes
git add .

# Commit changes
git commit -m "Update: Description of changes"

# Push to GitHub
git push origin main
```

GitHub Pages will automatically update within 1-2 minutes.

## Option 2: Netlify (Alternative - Free)

### Step 1: Create Netlify Account

1. Go to **netlify.com**
2. Click **Sign up**
3. Choose "Sign up with GitHub" (easiest)
4. Authorize Netlify to access GitHub

### Step 2: Create New Site

1. Click **Add new site** → **Import an existing project**
2. Select **GitHub**
3. Find your portfolio repository
4. Click on it to import

### Step 3: Configure Build Settings

- **Base directory**: (leave empty)
- **Build command**: (leave empty)
- **Publish directory**: `.` (current directory)
- Click **Deploy site**

### Step 4: Get Your Netlify URL

Netlify provides a URL like: `https://your-site-name.netlify.app`

You can customize the subdomain or connect a custom domain.

### Step 5: Update Canonical URLs

Update canonical and social meta tags with your Netlify URL (same as Step 4 in GitHub Pages section)

## Option 3: Custom Domain

### Purchase a Domain

Popular registrars:
- GoDaddy (godaddy.com)
- Namecheap (namecheap.com)
- Google Domains (domains.google.com)
- Bluehost (bluehost.com)

Cost: Typically $5-15/year

### Connect to GitHub Pages

1. **Buy your domain** (e.g., `myportfolio.com`)
2. **Go to domain registrar's settings**
3. **Find "DNS settings" or "Nameservers"**
4. **Add these DNS records**:

```
Type: A
Name: @
Value: 185.199.108.153

Type: A
Name: @
Value: 185.199.109.153

Type: A
Name: @
Value: 185.199.110.153

Type: A
Name: @
Value: 185.199.111.153

Type: CNAME
Name: www
Value: username.github.io
```

5. **Go to your GitHub repo → Settings → Pages**
6. **Under "Custom domain"** enter: `myportfolio.com`
7. **Check "Enforce HTTPS"** (wait 1-2 minutes)
8. **Wait 24 hours for DNS to fully propagate**

### Connect to Netlify

1. **Buy your domain** 
2. **In Netlify dashboard:**
   - Click your site
   - Go to **Site settings** → **Domain management**
   - Click **Add custom domain**
   - Enter your domain name
   - Point nameservers to Netlify (instructions provided)

## Submission Requirements

### For Assignment Submission

Prepare these links:

1. **GitHub Repository**: `https://github.com/USERNAME/portfolio`
2. **Live Demo**: `https://username.github.io/portfolio`

Example submission format:
```
GitHub Repository: https://github.com/vijay-kumar/portfolio
Live Demo: https://vijay-kumar.github.io/portfolio

Key Features Implemented:
✅ Semantic HTML5 structure
✅ WCAG 2.1 AA accessibility compliance
✅ ARIA labels and roles
✅ SEO-friendly meta tags
✅ JSON-LD structured data
✅ Accessible contact form
✅ Keyboard navigation support
✅ Screen reader compatible
✅ Responsive design
✅ Dark mode support
```

### Submission Platforms

Common submission options:

1. **GitHub Link**: Share repository link
2. **Google Drive**: Upload folder with files + README
3. **Netlify**: Share live demo link
4. **Drive/OneDrive**: Upload all files with links
5. **Canvas/LMS**: Upload files directly

## Verification Checklist

After deploying, verify everything:

- [ ] Website loads without errors
- [ ] All pages accessible via navigation
- [ ] Links to other pages work
- [ ] Contact form appears (may not be functional without backend)
- [ ] Images load correctly
- [ ] Responsive on mobile (test with DevTools)
- [ ] Lighthouse Accessibility = 100
- [ ] Lighthouse SEO = 100
- [ ] Custom domain working (if used)
- [ ] HTTPS enabled
- [ ] Keyboard navigation works
- [ ] Skip link appears on Tab

## Troubleshooting

### GitHub Pages Not Working

**Problem**: Site not loading
- Solution: Wait 2-3 minutes for GitHub to process
- Solution: Check repository is public
- Solution: Verify Settings → Pages is configured correctly

**Problem**: Old version showing
- Solution: Hard refresh browser (Ctrl+Shift+R)
- Solution: Clear browser cache
- Solution: Wait 5 minutes for CDN to update

### 404 Errors on Pages

**Problem**: Clicking links shows 404
- Solution: Verify file names are correct (index.html, about.html, etc.)
- Solution: Check case sensitivity (file.html vs File.html)
- Solution: Verify files pushed to GitHub

### Images Not Loading

**Problem**: Images show broken icon
- Solution: Check image paths are relative (images/profile.svg)
- Solution: Verify images folder pushed to GitHub
- Solution: Check file extensions are correct

### Styling Not Applied

**Problem**: Page looks unstyled
- Solution: Hard refresh (Ctrl+Shift+R)
- Solution: Check css/style.css path is correct
- Solution: Verify CSS file pushed to GitHub

## Testing Your Live Site

### Lighthouse Audit

1. Visit your live site in Chrome
2. Press F12 to open DevTools
3. Click **Lighthouse** tab
4. Click **Analyze page load**
5. Target scores:
   - Accessibility: 100
   - SEO: 100
   - Performance: 90+
   - Best Practices: 95+

### WAVE Accessibility

1. Go to wave.webaim.org
2. Enter your live site URL
3. Check for errors (red):
   - All should be 0
4. Review warnings (yellow)

### Page Speed Test

1. Go to pagespeed.web.dev
2. Enter your site URL
3. Check metrics
4. Optimize if needed

## Advanced: Setup Automatic Updates

### GitHub Actions for Continuous Deployment

Create `.github/workflows/deploy.yml`:

```yaml
name: Deploy

on:
  push:
    branches: [ main ]

jobs:
  build:
    runs-on: ubuntu-latest
    
    steps:
    - uses: actions/checkout@v2
    
    - name: Deploy to GitHub Pages
      run: |
        git config user.name "GitHub Actions"
        git config user.email "actions@github.com"
        git push origin main
```

This automatically deploys changes when you push to GitHub.

## Performance Optimization

### Optimize Images

1. Use tools like:
   - TinyPNG (tinypng.com)
   - ImageOptim (imageoptim.com)
   - Squoosh (squoosh.app)

2. Convert to WebP format for better compression

3. Update img tags:
   ```html
   <picture>
     <source srcset="image.webp" type="image/webp">
     <img src="image.png" alt="...">
   </picture>
   ```

### Minify CSS/JS

```bash
# Using online tools or CLI
npm install -g cssnano
cssnano style.css > style.min.css
```

### Enable Gzip Compression

GitHub Pages has gzip enabled automatically.

## Security Considerations

- ✅ GitHub Pages uses HTTPS automatically
- ✅ No sensitive data stored in client-side code
- ✅ Contact form requires backend for security
- ✅ No database needed for static site

## Next Steps After Deployment

1. **Share your portfolio**:
   - LinkedIn
   - Twitter
   - GitHub profile
   - Job applications

2. **Keep it updated**:
   - Add new projects
   - Update skills
   - Keep content fresh

3. **Monitor performance**:
   - Check Lighthouse scores monthly
   - Monitor accessibility
   - Get feedback from users

4. **Improve over time**:
   - Add more features
   - Optimize performance
   - Enhance design
   - Add interactivity

---

**Need Help?**
- GitHub Pages Help: pages.github.com
- Netlify Support: docs.netlify.com
- WCAG Guidelines: w3.org/WAI/WCAG21/quickref/
