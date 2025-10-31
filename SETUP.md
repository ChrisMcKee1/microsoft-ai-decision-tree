# GitHub Pages Setup Guide

## What Was Configured

Your repository is now ready for **GitHub Pages** with the **Just the Docs** theme. This will give you a professional, searchable documentation site.

## Repository Structure

```
microsoft-ai-decision-tree/
├── README.md              # Main documentation (homepage)
├── images/                # Visual assets (AI Gateway GIF)
├── docs/                  # Auxiliary documentation
├── _config.yml            # GitHub Pages configuration
├── Gemfile                # Ruby dependencies for local preview
└── .gitignore            # Git ignore rules
```

## Next Steps

### 1. Push to GitHub

```powershell
# Create a new repository on GitHub (don't initialize with README)
# Then run:
git remote add origin https://github.com/YOUR_USERNAME/microsoft-ai-decision-tree.git
git branch -M main
git push -u origin main
```

### 2. Enable GitHub Pages

1. Go to your repository on GitHub
2. Click **Settings** → **Pages** (left sidebar)
3. Under **Source**, select:
   - Branch: `main`
   - Folder: `/ (root)`
4. Click **Save**

GitHub will automatically build your site. It takes 1-2 minutes.

### 3. Access Your Site

Your documentation will be available at:
```
https://YOUR_USERNAME.github.io/microsoft-ai-decision-tree/
```

## Features Enabled

✅ **Professional Theme** - Clean Microsoft Learn-style appearance  
✅ **Search** - Full-text search across all content  
✅ **Mermaid Diagrams** - Your decision tree flowcharts will render  
✅ **Mobile Responsive** - Works on all devices  
✅ **Dark Mode** - Built-in light/dark theme toggle  
✅ **Navigation** - Automatic sidebar from headings  

## Customization Options

### Update Site Title/Description

Edit `_config.yml`:
```yaml
title: Your Company Name - AI Decision Tree
description: Your custom description
```

### Add Your Logo

1. Add logo file to `/images/logo.png`
2. Uncomment in `_config.yml`:
```yaml
logo: "/images/logo.png"
```

### Update GitHub Link

Edit `_config.yml`:
```yaml
aux_links:
  "View on GitHub":
    - "//github.com/YOUR_USERNAME/microsoft-ai-decision-tree"
```

Also update in `README.md` (line 8):
```markdown
[View on GitHub](https://github.com/YOUR_USERNAME/microsoft-ai-decision-tree)
```

### Custom Domain (Optional)

If you want to use your own domain (e.g., `docs.yourcompany.com`):

1. Add a `CNAME` file to the root with your domain:
```
docs.yourcompany.com
```

2. Configure DNS with your domain provider:
   - Add a CNAME record pointing to: `YOUR_USERNAME.github.io`

3. Enable HTTPS in GitHub Pages settings

## Local Development (Optional)

To preview the site locally before pushing:

```powershell
# Install Ruby (if not already installed)
# Download from: https://rubyinstaller.org/

# Install dependencies
bundle install

# Serve locally
bundle exec jekyll serve

# Open browser to http://localhost:4000
```

## Image Handling

The AI Gateway image is already configured correctly:
- Located at: `/images/ai-gateway-flow.gif`
- Referenced in README: `![AI Gateway Flow](images/ai-gateway-flow.gif)`
- Will render properly in GitHub Pages

## Troubleshooting

### Site Not Building?

Check the **Actions** tab in your GitHub repository for build errors.

### Images Not Loading?

Verify image paths use relative URLs without leading slash:
- ✅ Correct: `images/filename.gif`
- ❌ Wrong: `/images/filename.gif`

### Mermaid Diagrams Not Rendering?

GitHub Pages may take a few minutes to build after first push. If they still don't show:
1. Check the **Actions** tab for build completion
2. Clear your browser cache
3. Wait 2-3 minutes and refresh

## Analytics (Optional)

To add Google Analytics:

1. Get your GA4 tracking ID
2. Add to `_config.yml`:
```yaml
google_analytics: G-XXXXXXXXXX
```

## Need Help?

- [Just the Docs Documentation](https://just-the-docs.com/)
- [GitHub Pages Documentation](https://docs.github.com/en/pages)
- [Jekyll Documentation](https://jekyllrb.com/docs/)

---

**You're all set!** Just push to GitHub and enable Pages in settings.
