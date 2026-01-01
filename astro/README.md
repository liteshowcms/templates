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

**Custom Domains:** You can configure a custom domain in your project's Deployment settings.

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
