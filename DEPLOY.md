# Deployment Guide - GitHub Pages

## Quick Setup (One-Time)

### 1. Create GitHub Repository

1. Go to [github.com](https://github.com) and sign in
2. Click the "+" icon → "New repository"
3. Name it: `lyrics-figure` (or any name you like)
4. **Don't** check "Initialize with README" (we already have files)
5. Click "Create repository"

### 2. Connect and Push

Run these commands in your project folder:

```bash
# Set your GitHub username (replace YOUR_USERNAME)
git remote add origin https://github.com/YOUR_USERNAME/lyrics-figure.git

# Push your code
git branch -M main
git push -u origin main
```

### 3. Enable GitHub Pages

1. Go to your repository on GitHub
2. Click **Settings** (top menu)
3. Scroll down to **Pages** (left sidebar)
4. Under **Source**, select:
   - Branch: `main`
   - Folder: `/ (root)`
5. Click **Save**
6. Wait 1-2 minutes, then visit: `https://YOUR_USERNAME.github.io/lyrics-figure/`

## Updating the Live Version

When you want to publish your local changes:

```bash
# Stage all changes
git add .

# Commit with a message
git commit -m "Description of your changes"

# Push to GitHub
git push
```

GitHub Pages will automatically update within 1-2 minutes!

## Working Locally

- Edit files locally as normal
- Test by opening `index.html` in your browser
- Only push when you want to update the live version
- Your local changes won't affect the live site until you push

## Troubleshooting

**Can't push?**
- Make sure you've set up the remote: `git remote -v`
- If missing, add it: `git remote add origin https://github.com/YOUR_USERNAME/lyrics-figure.git`

**Pages not updating?**
- Check GitHub Actions tab for build errors
- Make sure you pushed to the `main` branch
- Wait 2-3 minutes for GitHub to rebuild

**Need to change repository name?**
- Go to Settings → General → Repository name
- Update the name, then update your remote URL
