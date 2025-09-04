# GitHub Pages + MkDocs Deployment Guide

This guide explains how to deploy the OpenFaaS Platform Research documentation to GitHub Pages using MkDocs.

## Prerequisites

- Python 3.7+ installed
- Git repository with the openfaas-research directory
- GitHub account with repository access

## Local Setup

### 1. Install MkDocs and Dependencies

```bash
# Install MkDocs and Material theme
pip install mkdocs mkdocs-material

# Install additional plugins (optional)
pip install mkdocs-git-revision-date-localized-plugin
pip install mkdocs-mermaid2-plugin
```

### 2. Test Locally

```bash
# Navigate to the openfaas-research directory
cd openfaas-research

# Start local development server
mkdocs serve

# Open http://127.0.0.1:8000 in your browser
```

## GitHub Pages Deployment

### Option 1: GitHub Actions (Recommended)

1. **Create GitHub Actions workflow**

Create `.github/workflows/docs.yml`:

```yaml
name: Deploy Documentation

on:
  push:
    branches: [ main ]
  pull_request:
    branches: [ main ]

jobs:
  deploy:
    runs-on: ubuntu-latest
    steps:
    - uses: actions/checkout@v3
    
    - name: Set up Python
      uses: actions/setup-python@v4
      with:
        python-version: '3.9'
    
    - name: Install dependencies
      run: |
        python -m pip install --upgrade pip
        pip install mkdocs mkdocs-material mkdocs-git-revision-date-localized-plugin mkdocs-mermaid2-plugin
    
    - name: Build documentation
      run: mkdocs build
    
    - name: Deploy to GitHub Pages
      if: github.ref == 'refs/heads/main'
      uses: peaceiris/actions-gh-pages@v3
      with:
        github_token: ${{ secrets.GITHUB_TOKEN }}
        publish_dir: ./site
```

2. **Enable GitHub Pages**
   - Go to repository Settings → Pages
   - Source: Deploy from a branch
   - Branch: gh-pages
   - Folder: / (root)

### Option 2: Manual Deployment

```bash
# Build the documentation
mkdocs build

# Deploy to GitHub Pages (requires gh-pages branch)
mkdocs gh-deploy
```

## Configuration Updates

### Update mkdocs.yml

Before deploying, update the following in `mkdocs.yml`:

```yaml
# Replace with your actual GitHub username
site_url: https://furiatona.github.io/openfaas-research/
repo_name: furiatona/openfaas-research
repo_url: https://github.com/furiatona/openfaas-research
edit_uri: edit/main/
```
```

### Custom Domain (Optional)

If you have a custom domain:

1. Add `CNAME` file to the `docs/` directory:
```
your-domain.com
```

2. Update `mkdocs.yml`:
```yaml
site_url: https://your-domain.com
```

## Features Included

### Material Theme Features
- **Dark/Light mode toggle**
- **Search functionality**
- **Navigation tabs and sections**
- **Code highlighting**
- **Admonitions and callouts**
- **Mermaid diagram support**

### Plugins
- **Search**: Full-text search across all pages
- **Git revision dates**: Shows last modified dates
- **Versioning**: Support for multiple versions (with mike)

## Customization

### Adding Custom CSS

Create `docs/stylesheets/extra.css`:

```css
/* Custom styles */
.md-header {
    background-color: #1976d2;
}

.md-nav__title {
    color: #1976d2;
}
```

Update `mkdocs.yml`:

```yaml
extra_css:
  - stylesheets/extra.css
```

### Adding Custom JavaScript

Create `docs/javascripts/extra.js`:

```javascript
// Custom JavaScript
console.log('OpenFaaS Platform Research loaded');
```

Update `mkdocs.yml`:

```yaml
extra_javascript:
  - javascripts/extra.js
```

## Troubleshooting

### Common Issues

1. **Build fails**: Check Python version and dependencies
2. **Missing pages**: Verify file paths in `nav` section
3. **Styling issues**: Check CSS/JS file paths
4. **Deployment fails**: Verify GitHub Actions workflow

### Debug Commands

```bash
# Check MkDocs version
mkdocs --version

# Validate configuration
mkdocs build --strict

# Check for broken links
mkdocs build --strict --verbose
```

## Maintenance

### Regular Updates

1. **Update dependencies**:
```bash
pip install --upgrade mkdocs mkdocs-material
```

2. **Check for broken links**:
```bash
mkdocs build --strict
```

3. **Test locally** before deploying:
```bash
mkdocs serve
```

### Version Management

For multiple versions:

```bash
# Install mike
pip install mike

# Deploy version
mike deploy 1.0 main

# Set default version
mike set-default 1.0
```

## Resources

- [MkDocs Documentation](https://www.mkdocs.org/)
- [Material for MkDocs](https://squidfunk.github.io/mkdocs-material/)
- [GitHub Pages Documentation](https://pages.github.com/)
- [GitHub Actions Documentation](https://docs.github.com/en/actions)
