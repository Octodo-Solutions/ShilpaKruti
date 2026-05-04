# GitHub Pages deployment and custom domain DNS

**This repository:** [Octodo-Solutions/ShilpaKruti](https://github.com/Octodo-Solutions/ShilpaKruti)

- Default Pages URL (after Actions deploy succeeds): **https://Octodo-Solutions.github.io/ShilpaKruti/**
- Custom-domain CNAME target (always this hostname, no repo name in the value): **`Octodo-Solutions.github.io`**

## 1. Push this repository to GitHub

If you already cloned from GitHub, push your branch:

```bash
git push origin main
```

Otherwise create the repo on GitHub and add `origin`, then push.

## 2. Enable GitHub Pages (use GitHub Actions)

1. On GitHub, open **Octodo-Solutions/ShilpaKruti** → **Settings** → **Pages**.
2. Under **Build and deployment** → **Source**, choose **GitHub Actions** (not “Deploy from a branch”).
3. The workflow **Deploy GitHub Pages** runs on push to `main` or `master`. Open the **Actions** tab if the first run needs approval.

After a successful run, the site is at **https://Octodo-Solutions.github.io/ShilpaKruti/**

## 3. Map your own domain (DNS)

In **Settings** → **Pages** → **Custom domain**, enter your hostname (for example `www.yourdomain.com` or `yourdomain.com`), then add these records at your DNS provider. DNS can take up to 24 hours.

**Important:** CNAME records must point to **`Octodo-Solutions.github.io`** only (no `https://`, no `/ShilpaKruti` in the DNS value).

### Apex domain (`yourdomain.com`)

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

If your DNS provider supports **ALIAS** or **ANAME** on `@`, you may point `@` to **`Octodo-Solutions.github.io`** instead of the A/AAAA list (see GitHub’s docs).

### `www` subdomain (`www.yourdomain.com`)

| Type  | Name / Host | Value                         |
|-------|-------------|--------------------------------|
| CNAME | `www`       | `Octodo-Solutions.github.io`   |

### Another subdomain (e.g. `app.yourdomain.com`)

| Type  | Name / Host | Value                         |
|-------|-------------|--------------------------------|
| CNAME | `app`       | `Octodo-Solutions.github.io`   |

After DNS resolves, in **Pages** settings enable **Enforce HTTPS** when GitHub offers it.

Official reference: [Managing a custom domain for your GitHub Pages site](https://docs.github.com/en/pages/configuring-a-custom-domain-for-your-github-pages-site/managing-a-custom-domain-for-your-github-pages-site).
