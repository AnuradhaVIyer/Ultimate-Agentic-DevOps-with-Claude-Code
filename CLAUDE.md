# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

Static HTML/CSS portfolio website deployed to AWS using S3 and CloudFront, provisioned with Terraform, and automated via GitHub Actions.

## Development

No build step, package manager, or tests. Serve locally with any static file server:

```bash
python -m http.server 8080
# or
npx serve .
```

## Deployment (Nginx on Ubuntu)

```bash
sudo cp -r ./* /var/www/html/
sudo systemctl restart nginx
```
## Commands
```bash
terraform init
terraform plan
terraform apply
```
## Conventions 
- All infrastructure changes go through Terraform — never modify AWS resources manually
- No JavaScript in this project
- CSS uses mobile-first approach with breakpoints at 900px, 768px, and 600px

## Safety
Never put secrets in this file. No API keys, passwords, or AWS credentials.

## Architecture

Pure HTML5 and CSS3. No JavaScript. No build step. No framework.

- `index.html` — single-page site with sections: navbar, hero, about, services, courses, books, community, contact, footer
- `style.css` — all styles; responsive via media queries; navbar is fixed-position with mobile hamburger menu
- `privacy.html`, `terms.html` — standalone pages with self-contained inline styles (do not share `style.css`)
- `images/` — static assets (logos, book covers, profile photos)
- External dependency: Font Awesome 6.5 via CDN (loaded in `index.html` only)

## DMI Ownership Requirement

Before deployment, students must edit the footer in `index.html` (the `.footer-bottom` div) to add their name, cohort, group, and date as proof of deployment ownership.
