# CryptoCybin landing page

Static cover page for [cryptocybin.xyz](https://cryptocybin.xyz).
No build step: `index.html` plus `assets/` is the whole site.

```
index.html              page (styles and the network animation are inline)
assets/mark.png         mushroom mark, used in the hero, header and icons
assets/logo.png         original logo with wordmark (dark "Crypto" text, for light backgrounds)
assets/og.png           social preview image (1200x630)
assets/icon-*.png       PWA icons; favicon.ico at the root
site.webmanifest, robots.txt, sitemap.xml
CNAME                   custom domain for GitHub Pages branch deploys
.github/workflows/pages.yml   deploys to GitHub Pages on every push to main
```

Preview locally:

```
python3 -m http.server 8000
```

## Free hosting options

All of these serve static files for free with automatic HTTPS.

### 1. GitHub Pages (wired up in this repo)

- Push to `main`. The workflow in `.github/workflows/pages.yml` publishes the repo root.
- In the repo: Settings, Pages, set Source to "GitHub Actions" (done once) and Custom domain to `cryptocybin.xyz`.
- DNS at the registrar for `cryptocybin.xyz`:

  ```
  A     @    185.199.108.153
  A     @    185.199.109.153
  A     @    185.199.110.153
  A     @    185.199.111.153
  AAAA  @    2606:50c0:8000::153
  AAAA  @    2606:50c0:8001::153
  AAAA  @    2606:50c0:8002::153
  AAAA  @    2606:50c0:8003::153
  CNAME www  cryptocybin.github.io
  ```

- Limits: one custom domain per Pages site, 1 GB site, 100 GB/month soft bandwidth cap.

### 2. Cloudflare Pages

- Create a Pages project from this GitHub repo. Framework preset: None. Build command: empty.
  Output directory: `/`.
- Add `cryptocybin.xyz` as a custom domain on the project.
- Unlimited bandwidth, 500 builds/month, free TLS. Domains need to use Cloudflare DNS
  (free plan) or a CNAME to `<project>.pages.dev`.

### 3. Netlify

- New site from Git, publish directory `/`, no build command.
- Add `cryptocybin.xyz` as the site's custom domain.

- Limits: 100 GB/month bandwidth, 300 build minutes/month.

### 4. Vercel

- Import the repo, framework "Other", no build command, output directory `.`.
- Add `cryptocybin.xyz` in project settings.
- Limits: 100 GB/month bandwidth on the Hobby plan, non-commercial use only.

### 5. Others that also work

Render static sites, Firebase Hosting (10 GB/month), Surge.sh. Anything that serves a folder.

## Changing the copy

All text lives in `index.html`: the headline and intro in the hero, the two buttons under it,
the three service blurbs in the "What we do" section, and the domain in the footer.
