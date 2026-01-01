# {{PROJECT_NAME}}

Built with [Liteshow](https://liteshow.io) - AI-first, SEO-optimized, Git-powered CMS

## Deploy Your Site

This is a static Astro site that works on **any hosting platform**. Choose your preferred platform below.

### 🚀 GitHub Pages (Recommended)

**Natively supported by Liteshow with 1-click deployment!**

Your site is already configured for GitHub Pages deployment via GitHub Actions. Simply:

1. Go to your Liteshow project dashboard
2. Navigate to the **Deployment** tab
3. Click **Deploy Now**

Liteshow will automatically:
- ✅ Enable GitHub Pages for your repository
- ✅ Trigger the deployment workflow
- ✅ Build and publish your site
- ✅ Provide you with a live URL

**Your site will be live at:** `https://<username>.github.io/<repo-name>/`

**Custom Domains:** You can configure a custom domain in your project's Deployment settings. See the [Custom Domain Setup](#-custom-domain-setup) section below for detailed instructions.

---

### ⚡ Vercel

[![Deploy with Vercel](https://vercel.com/button)](https://vercel.com/new/clone)

1. Click the deploy button above OR go to [Vercel](https://vercel.com/new)
2. Import this repository from GitHub
3. Vercel will auto-detect settings:
   - **Framework:** Astro
   - **Build command:** `npm install && npm run build`
   - **Output directory:** `dist`
4. Add environment variables (see below)
5. Click **Deploy**

### 📦 Netlify

[![Deploy to Netlify](https://www.netlify.com/img/deploy/button.svg)](https://app.netlify.com/start)

1. Click the deploy button above OR go to [Netlify](https://app.netlify.com/start)
2. Import this repository from GitHub
3. Netlify will auto-detect settings:
   - **Build command:** `npm install && npm run build`
   - **Publish directory:** `dist`
4. Add environment variables (see below)
5. Click **Deploy site**

### 🌐 Other Platforms

This static site also works on:
- **Cloudflare Pages** - Auto-detects Astro
- **AWS S3 + CloudFront** - Upload `dist/` folder
- **Any static host** - Just upload the `dist/` folder

## 🌐 Custom Domain Setup

Use your own domain (e.g., `www.yourdomain.com`) instead of the default GitHub Pages URL.

### How It Works

When you configure a custom domain in Liteshow:

1. **Liteshow updates your project** - Sets `BASE_PATH` to `/` (instead of `/repo-name/`)
2. **You configure DNS** - Point your domain to GitHub Pages servers
3. **You configure GitHub Pages** - Add CNAME file or use GitHub UI
4. **GitHub handles SSL** - Automatic HTTPS certificate via Let's Encrypt
5. **Your site is live** - Accessible at your custom domain

### Step 1: Configure Domain in Liteshow

1. Go to your project in the Liteshow dashboard
2. Navigate to **Deployment** → **Settings**
3. Enter your custom domain (e.g., `www.yourdomain.com` or `blog.yourdomain.com`)
4. Save settings
5. Deploy your site (Liteshow will automatically configure `BASE_PATH` for custom domain)

### Step 2: Configure DNS Records

Add DNS records with your domain registrar (GoDaddy, Namecheap, Cloudflare, etc.):

**For subdomain (recommended): `www.yourdomain.com` or `blog.yourdomain.com`**

| Type  | Name  | Value                     | TTL  |
|-------|-------|---------------------------|------|
| CNAME | www   | `<username>.github.io`    | 3600 |

**For apex/root domain: `yourdomain.com`**

| Type  | Name | Value           | TTL  |
|-------|------|-----------------|------|
| A     | @    | 185.199.108.153 | 3600 |
| A     | @    | 185.199.109.153 | 3600 |
| A     | @    | 185.199.110.153 | 3600 |
| A     | @    | 185.199.111.153 | 3600 |

**For both apex and www (best practice):**

Set up both records above, then also add:

| Type  | Name | Value                  | TTL  |
|-------|------|------------------------|------|
| CNAME | www  | `yourdomain.com`       | 3600 |

> **Note:** DNS propagation can take 24-48 hours, but usually completes within a few hours.

### Step 3: Configure GitHub Pages

**Option A: Via GitHub UI (Easier)**

1. Go to your repository on GitHub
2. Click **Settings** → **Pages**
3. Under "Custom domain", enter your domain: `www.yourdomain.com`
4. Click **Save**
5. Wait for DNS check to complete (green checkmark)
6. Enable **Enforce HTTPS** (recommended)

**Option B: Via CNAME File (Alternative)**

1. Create a file named `CNAME` (no extension) in the `public/` folder of your repository
2. Add a single line with your domain:
   ```
   www.yourdomain.com
   ```
3. Commit and push to GitHub
4. The next deployment will use your custom domain

### Step 4: Verify & Enable HTTPS

1. Wait for DNS propagation (check with `nslookup www.yourdomain.com`)
2. GitHub will automatically provision an SSL certificate (takes a few minutes)
3. Your site will be accessible via HTTPS at your custom domain

### Technical Details

**Path Handling:**
- Default GitHub Pages: `BASE_PATH=/repo-name/` → All URLs are prefixed (e.g., `/repo-name/about`)
- Custom Domain: `BASE_PATH=/` → Clean URLs (e.g., `/about`)

Liteshow automatically configures this when you set a custom domain.

**SSL/HTTPS:**
- GitHub Pages provides free SSL certificates via Let's Encrypt
- Automatic renewal
- Enforced HTTPS redirect (when enabled)

**DNS Records Explained:**
- **CNAME** - Alias pointing to another domain (subdomain only)
- **A Record** - Direct IP address mapping (apex/root domain)
- GitHub's A record IPs are static and maintained by GitHub

### Troubleshooting

**DNS not propagating:**
- Check DNS with: `nslookup www.yourdomain.com`
- Wait 24-48 hours for full propagation
- Try flushing DNS cache: `ipconfig /flushdns` (Windows) or `sudo dscacheutil -flushcache` (macOS)

**"Domain's DNS record could not be retrieved" error:**
- Verify DNS records are correct
- Wait for DNS propagation
- Check with: `dig www.yourdomain.com` or `nslookup www.yourdomain.com`

**Site not loading on custom domain:**
- Verify CNAME file exists (Option B) or GitHub Pages setting is correct (Option A)
- Check that you deployed after configuring the custom domain in Liteshow
- Ensure DNS records point to correct GitHub Pages servers

**SSL certificate not provisioning:**
- Can take up to 24 hours after DNS propagation
- Ensure DNS is fully propagated first
- Check GitHub Pages settings show "HTTPS available"

**404 errors on custom domain:**
- Ensure you redeployed after setting custom domain in Liteshow
- Verify `BASE_PATH` is set to `/` (check GitHub Actions secrets: `BASE_PATH`)
- Check that pages are published in Liteshow dashboard

### Resources

- [GitHub Pages Custom Domain Docs](https://docs.github.com/en/pages/configuring-a-custom-domain-for-your-github-pages-site)
- [GitHub Pages A Records](https://docs.github.com/en/pages/configuring-a-custom-domain-for-your-github-pages-site/managing-a-custom-domain-for-your-github-pages-site#configuring-an-apex-domain)

## Environment Variables

**For GitHub Pages:** Environment variables are automatically configured by Liteshow. No manual setup needed!

**For other platforms:** Add these in your deployment platform's dashboard:

| Variable | Value | Description |
|----------|-------|-------------|
| `PUBLIC_API_URL` | Your Liteshow API URL | Contact Liteshow support for your API URL |

## Local Development

```bash
# Install dependencies
npm install

# Start dev server
npm run dev
```

Visit http://localhost:4321

**Note:** When running locally, the site fetches content from your Liteshow project's API. Make sure your content is published in the Liteshow dashboard.

## How It Works

This Astro site fetches your published content from the Liteshow API at build time. The workflow is simple:

1. **Create/edit content** in Liteshow dashboard
2. **Publish** your pages when ready
3. **Deploy** from the Deployment tab (GitHub Pages) or push to your main branch
4. **Live!** Your site is rebuilt with the latest content

Content is fetched securely from your project's database via the Liteshow API.

## Project Structure

```
/
├── .github/
│   └── workflows/
│       └── deploy.yml      # GitHub Pages deployment
├── src/
│   ├── components/
│   │   └── blocks/         # Content block components
│   ├── layouts/
│   │   └── BaseLayout.astro
│   ├── lib/
│   │   └── content-api.ts  # Liteshow API client
│   └── pages/
│       ├── index.astro     # Home page
│       ├── [slug].astro    # Dynamic pages
│       └── 404.astro       # Not found page
├── astro.config.mjs
└── package.json
```

## Support

Need help? Visit [liteshow.io/docs](https://liteshow.io/docs) or contact support at support@liteshow.io
