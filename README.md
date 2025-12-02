# Nahuel Fefer Personal Website

Complete setup guide for deploying your professional website to nahuelfefer.com

## 📁 Website Structure

Your website now has the following pages:
- `index.html` - Home/Landing page with hero image
- `about.html` - About page with bio and credentials  
- `work.html` - Professional experience and accomplishments
- `media.html` - Photo gallery and media coverage
- `blog.html` - Blog listing page
- `services.html` - Legal & consulting services
- `posts/` - Individual blog posts folder
  - `stl-tax-incentive-reform.html` - Sample blog post with comments
- `images/` - All your photos
- `styles.css` - Shared stylesheet for all pages

## 🚀 Setup Instructions

### Step 1: Create GitHub Account & Repository

1. Go to https://github.com and create a free account (if you don't have one)
2. Click the "+" icon in the top right → "New repository"
3. Name your repository: `YOUR-USERNAME.github.io` 
   - Replace YOUR-USERNAME with your actual GitHub username
   - For example: `nahuelfefer.github.io`
4. Make it **Public** (required for free GitHub Pages)
5. DO NOT initialize with README, .gitignore, or license
6. Click "Create repository"

### Step 2: Upload Your Website Files

**IMPORTANT:** You need to upload ALL of these files and folders:
- index.html
- about.html
- work.html
- media.html
- blog.html
- services.html
- styles.css
- images/ folder (with all 6 photos inside)
- posts/ folder (with blog post inside)

**Option A: Using GitHub Web Interface (Easiest)**

1. In your new repository, click "uploading an existing file"
2. Drag and drop ALL files and folders listed above
3. Wait for all files to upload (especially the images folder)
4. Scroll down, add commit message: "Initial website upload"
5. Click "Commit changes"

**Option B: Using Git Command Line**

```bash
# Navigate to the folder with your website files
cd /path/to/your/website/files

# Initialize git
git init

# Add all files
git add .

# Commit
git commit -m "Initial website upload"

# Add your GitHub repository as remote
git remote add origin https://github.com/YOUR-USERNAME/YOUR-USERNAME.github.io.git

# Push to GitHub
git branch -M main
git push -u origin main
```

### Step 3: Enable GitHub Pages

1. In your repository, go to **Settings** (top menu)
2. Scroll down to **Pages** (in left sidebar under "Code and automation")
3. Under "Source", select **main** branch
4. Leave folder as **/ (root)**
5. Click **Save**
6. Wait 2-5 minutes - your site will be live at `https://YOUR-USERNAME.github.io`

### Step 4: Connect Your Custom Domain (nahuelfefer.com)

#### Part A: Configure GitHub

1. In your repository Settings → Pages
2. Under "Custom domain", enter: `nahuelfefer.com`
3. Click **Save**
4. Wait a few minutes, then check the box for **Enforce HTTPS** (it will appear after DNS is configured)

#### Part B: Configure Your Domain Registrar

You need to add DNS records where you bought nahuelfefer.com. Follow the instructions for your provider:

**DNS Records to Add:**

Add these **A Records** (all pointing to @):
```
Type: A | Host: @ | Value: 185.199.108.153
Type: A | Host: @ | Value: 185.199.109.153
Type: A | Host: @ | Value: 185.199.110.153
Type: A | Host: @ | Value: 185.199.111.153
```

Add this **CNAME Record**:
```
Type: CNAME | Host: www | Value: YOUR-USERNAME.github.io
```

**If you bought from Namecheap:**
1. Log in to Namecheap → Domain List → Manage
2. Go to "Advanced DNS"
3. Add the A and CNAME records listed above
4. TTL can be "Automatic" or "1 hour"

**If you bought from Google Domains:**
1. Go to Google Domains → DNS
2. Add Custom Records
3. Add the A and CNAME records listed above

**If you bought from Cloudflare:**
1. Go to Cloudflare → Select your domain → DNS
2. Add the A and CNAME records listed above
3. **Important**: Turn OFF the orange cloud (set to "DNS only") for GitHub Pages to work

### Step 5: Set Up Blog Comments (Utterances)

1. Go to https://github.com/apps/utterances
2. Click "Install"
3. Select your repository (YOUR-USERNAME.github.io)
4. Click "Install"
5. Open `posts/stl-tax-incentive-reform.html` in your repository
6. Find line with: `repo="YOUR-GITHUB-USERNAME/YOUR-REPO-NAME"`
7. Replace with your actual info, for example: `repo="nahuelfefer/nahuelfefer.github.io"`
8. Commit the change

### Step 6: Wait for DNS Propagation

- DNS changes can take 24-48 hours to fully propagate
- Usually works within 1-2 hours
- Check if it's working: go to https://nahuelfefer.com
- If you see your website, you're done! 🎉

## ✍️ How to Add New Blog Posts

1. Copy `posts/stl-tax-incentive-reform.html` to a new file
2. Rename it (e.g., `posts/my-new-post.html`)
3. Edit the content:
   - Change the `<title>` tag
   - Update the page header `<h1>` and date
   - Write your new content in the article section
4. Open `blog.html`
5. Add a new blog card with your post info (copy the existing one as a template)
6. Upload/commit both files to GitHub

## 📸 Managing Photos

All photos are in the `images/` folder. Your current photos are:
- `community-playground.jpg` - CDA playground event (used on homepage hero)
- `press-conference.jpg` - Press conference (used on About page)
- `planning-meeting.jpg` - Planning meeting (in Media gallery)
- `presentation.jpg` - Presentation (in Media gallery)
- `office-work.jpg` - Office work (in Media gallery)
- `site-visit.jpg` - Site visit (in Media gallery)

To add new photos:
1. Add them to the `images/` folder
2. Reference them in your HTML: `<img src="images/your-photo.jpg">`

## 📄 Adding PDFs/Documents

To add reports or documents:

**Option 1: Host on GitHub**
1. Create a `documents/` folder
2. Upload your PDFs there
3. Link to them: `<a href="documents/report.pdf">View Report</a>`

**Option 2: Link to external hosting**
- Use Google Drive, Dropbox, or another service
- Get the shareable link
- Add to your pages: `<a href="YOUR-LINK">View Report</a>`

## 🐛 Troubleshooting

**Website not showing after 5 minutes?**
- Check Settings → Pages is enabled with main branch selected
- Make sure files are in root directory, not a subfolder
- Clear your browser cache

**Domain not working after 24 hours?**
- Double-check DNS records match exactly
- Verify you entered domain correctly in GitHub Settings
- Try both www.nahuelfefer.com and nahuelfefer.com
- Check domain registrar's DNS settings are saved

**Images not loading?**
- Make sure images folder uploaded correctly
- Check file names match exactly (case-sensitive)
- Verify image paths in HTML are correct

**Comments not appearing?**
- Ensure Utterances GitHub App is installed
- Check repo name in script is correct format
- Commenters need GitHub accounts to post

## 🎨 Customization Tips

**Change Colors:**
Edit the `:root` section in `styles.css`:
```css
:root {
    --primary: #1a4d7a;  /* Main blue */
    --secondary: #2c6fa3; /* Light blue */
    --accent: #e8b44a;    /* Gold */
}
```

**Update Content:**
- All text can be edited directly in the HTML files
- Use any text editor (Notepad, VS Code, etc.)
- Upload changes to GitHub

**Add New Pages:**
- Copy an existing page as a template
- Update navigation links in all pages
- Upload to GitHub

## 📧 Need Help?

- GitHub Pages Documentation: https://docs.github.com/pages
- GitHub Support: https://support.github.com
- Utterances Setup: https://utteranc.es

## ✅ Launch Checklist

Before going live, make sure:
- [ ] All files uploaded to GitHub
- [ ] GitHub Pages enabled
- [ ] Custom domain added in Settings
- [ ] DNS records configured at domain registrar
- [ ] Photos loading correctly
- [ ] All navigation links work
- [ ] Utterances comments script updated with your repo name
- [ ] Test on mobile and desktop
- [ ] Share your new website!

Good luck! Your professional website will be live at nahuelfefer.com soon! 🚀
