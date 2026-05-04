# GitHub Pages deployment and custom domain DNS

## 1. Push this repository to GitHub

Create a new repository on GitHub (for example `ShilpaKruti`), then:

```bash
git remote add origin https://github.com/YOUR_USERNAME/ShilpaKruti.git
git branch -M main
git push -u origin main
```

Replace `YOUR_USERNAME` and the repo URL with yours.

## 2. Enable GitHub Pages (use GitHub Actions)

1. On GitHub, open the repository → **Settings** → **Pages**.
2. Under **Build and deployment** → **Source**, choose **GitHub Actions** (not “Deploy from a branch”).
3. The workflow **Deploy GitHub Pages** runs on push to `main` or `master`. Open the **Actions** tab if the first run needs approval.

After a successful run, the site is available at:

- `https://YOUR_USERNAME.github.io/REPOSITORY_NAME/`

Replace `YOUR_USERNAME` and `REPOSITORY_NAME` with your GitHub username and repository name.

## 3. Map your own domain (DNS)

Add your domain in **Settings** → **Pages** → **Custom domain**, then create the DNS records below at your DNS provider (registrar, Cloudflare, etc.). DNS can take up to 24 hours.

**Important:** The CNAME target is always `YOUR_USERNAME.github.io` (no `https://`, no repository name in the CNAME value).

### Apex domain (`example.com`)

| Type  | Name / Host | Value                 |
|-------|-------------|------------------------|
| A     | `@`         | `185.199.108.153`      |
| A     | `@`         | `185.199.109.153`      |
| A     | `@`         | `185.199.110.153`      |
| A     | `@`         | `185.199.111.153`      |

Optional IPv6:

| Type | Name / Host | Value                    |
|------|-------------|---------------------------|
| AAAA | `@`         | `2606:50c0:8000::153`     |
| AAAA | `@`         | `2606:50c0:8001::153`     |
| AAAA | `@`         | `2606:50c0:8002::153`     |
| AAAA | `@`         | `2606:50c0:8003::153`     |

If your DNS provider supports **ALIAS** or **ANAME** on `@`, you may point `@` to `YOUR_USERNAME.github.io` instead of the A/AAAA list (see GitHub’s docs).

### `www` subdomain (`www.example.com`)

| Type  | Name / Host | Value                      |
|-------|-------------|----------------------------|
| CNAME | `www`       | `YOUR_USERNAME.github.io`  |

### Another subdomain (e.g. `app.example.com`)

| Type  | Name / Host | Value                      |
|-------|-------------|----------------------------|
| CNAME | `app`       | `YOUR_USERNAME.github.io`  |

After DNS resolves, in **Pages** settings enable **Enforce HTTPS** when GitHub offers it.

Official reference: [Managing a custom domain for your GitHub Pages site](https://docs.github.com/en/pages/configuring-a-custom-domain-for-your-github-pages-site/managing-a-custom-domain-for-your-github-pages-site).
