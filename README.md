# VroJAuchzenD - Hugo Static Site

This is a Hugo static site converted from the WordPress site at https://vrojauchzend.de/

## Project Structure

```
vrojauchzend/
├── .github/
│   └── workflows/
│       └── hugo.yml              # GitHub Actions deployment workflow
├── content/
│   └── _index.md                 # Homepage content
├── static/
│   └── images/                   # Site images (you need to add these)
│       ├── IMG_2947.jpg
│       ├── Blick-zum-ueberdachten-Sitz.jpg
│       ├── Teich-mit-Springbrunnen.jpg
│       ├── Grillstelle.jpg
│       └── Teich.jpg
├── themes/
│   └── vrojauchzend-theme/
│       ├── layouts/
│       │   └── index.html        # Homepage template
│       ├── static/
│       │   └── css/
│       │       └── style.css     # Site styles
│       └── theme.toml            # Theme configuration
├── config.yaml                   # Hugo configuration
└── README.md                     # This file
```

## Setup Instructions

### 1. Install Hugo

Download and install Hugo Extended from: https://gohugo.io/installation/

### 2. Clone or Create Repository

```bash
# Create a new directory
mkdir vrojauchzend
cd vrojauchzend

# Initialize git
git init
```

### 3. Add Files

Create the following directory structure and add all the files:

```bash
# Create directories
mkdir -p .github/workflows
mkdir -p content
mkdir -p static/images
mkdir -p themes/vrojauchzend-theme/layouts
mkdir -p themes/vrojauchzend-theme/static/css

# Add all the files shown in the artifacts
```

### 4. Download Images

You need to download the images from the WordPress site and place them in `static/images/`:

1. **IMG_2947.jpg** - Hero image
2. **Blick-zum-ueberdachten-Sitz.jpg** - Covered seating area
3. **Teich-mit-Springbrunnen.jpg** - Pond with fountain
4. **Grillstelle.jpg** - Grill area
5. **Teich.jpg** - Pond

You can download these from:
- https://vrojauchzend.de/wp-content/uploads/2024/12/IMG_2947.jpg
- https://vrojauchzend.de/wp-content/uploads/2024/12/Blick-zum-ueberdachten-Sitz-1024x768.jpg
- https://vrojauchzend.de/wp-content/uploads/2024/12/Teich-mit-Springbrunnen-1024x768.jpg
- https://vrojauchzend.de/wp-content/uploads/2024/12/Grillstelle-1024x768.jpg
- https://vrojauchzend.de/wp-content/uploads/2024/12/Teich-1024x768.jpg

Rename them appropriately (remove the dimension suffixes).

### 5. Test Locally

```bash
# Run Hugo development server
hugo server -D

# Open http://localhost:1313 in your browser
```

### 6. GitHub Pages Deployment

#### Step 1: Create GitHub Repository

1. Go to GitHub and create a new repository named `vrojauchzend`
2. Make it public or private (public for free GitHub Pages)

#### Step 2: Update Configuration

1. Edit `config.yaml` and update:
   ```yaml
   baseURL: 'https://YOUR-USERNAME.github.io/vrojauchzend/'
   ```
   Replace `YOUR-USERNAME` with your GitHub username

2. If you want to use a custom domain, update to:
   ```yaml
   baseURL: 'https://vrojauchzend.de/'
   ```

#### Step 3: Push to GitHub

```bash
git add .
git commit -m "Initial commit: Hugo site"
git branch -M main
git remote add origin https://github.com/YOUR-USERNAME/vrojauchzend.git
git push -u origin main
```

#### Step 4: Enable GitHub Pages

1. Go to your repository on GitHub
2. Click **Settings** → **Pages**
3. Under **Source**, select **GitHub Actions**
4. The workflow will automatically run and deploy your site

#### Step 5: Access Your Site

Your site will be available at:
- `https://YOUR-USERNAME.github.io/vrojauchzend/` (if using GitHub subdomain)
- `https://vrojauchzend.de/` (if using custom domain - requires DNS configuration)

### Custom Domain Setup (Optional)

If you want to use `vrojauchzend.de`:

1. Add a `static/CNAME` file with content:
   ```
   vrojauchzend.de
   ```

2. Configure DNS at your domain registrar:
   - Add an A record pointing to GitHub Pages IPs:
     ```
     185.199.108.153
     185.199.109.153
     185.199.110.153
     185.199.111.153
     ```
   - Or add a CNAME record pointing to `YOUR-USERNAME.github.io`

3. In GitHub repository Settings → Pages, enter your custom domain

## Updating Content

### Edit Homepage Content

Edit `content/_index.md` to update the event information.

### Update Styles

Edit `themes/vrojauchzend-theme/static/css/style.css` to change colors, fonts, or layout.

### Change Layout

Edit `themes/vrojauchzend-theme/layouts/index.html` to modify the HTML structure.

### Deploy Changes

```bash
git add .
git commit -m "Update content"
git push
```

The GitHub Action will automatically rebuild and deploy your site.

## Development Tips

### Build for Production

```bash
hugo --minify
```

Output will be in the `public/` directory.

### Clean Build

```bash
rm -rf public/
hugo --minify
```

## Troubleshooting

### Images Not Showing

- Make sure images are in `static/images/`
- Check file names match exactly (case-sensitive)
- Verify images were pushed to GitHub

### GitHub Actions Failing

- Check `.github/workflows/hugo.yml` is present
- Verify GitHub Pages is enabled in repository settings
- Check Actions tab in GitHub for error logs

### Custom Domain Not Working

- Wait up to 24 hours for DNS propagation
- Verify DNS records are correct
- Check GitHub Pages settings shows your domain

## License

MIT License - Feel free to use and modify as needed.

## Support

For questions about the event, contact: vrojauchzend@posteo.de