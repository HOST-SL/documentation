# HOST Pay Mintlify Documentation - Setup Instructions

## 🚀 Quick Start

Get your documentation running locally in 3 minutes!

### 1. Install Mintlify CLI

```bash
npm install -g mintlify
```

### 2. Navigate to Docs Directory

```bash
cd /home/augie/Desktop/host-pay/docs
```

### 3. Start Development Server

```bash
mintlify dev
```

Your documentation will be available at: **http://localhost:3000**

## 📁 What's Been Created

```
docs/
├── mint.json                    ✅ Main configuration
├── README.md                    ✅ Documentation guide
├── introduction.mdx             ✅ Homepage
├── quickstart.mdx              ✅ Getting started
├── authentication.mdx           ✅ Auth guide
├── environments.mdx             ✅ Test vs Live
│
├── api-reference/
│   ├── introduction.mdx         ✅ API overview
│   └── users/
│       └── create.mdx           ✅ Create user endpoint
│
├── guides/
│   └── testing.mdx              ✅ Testing guide
│
├── webhooks/
│   └── overview.mdx             ✅ Webhooks overview
│
└── changelog/
    └── overview.mdx             ✅ Version history
```

## 🎨 Customization Needed

### 1. Add Your Branding

Create these files:

```bash
# Create logo directory
mkdir -p docs/logo

# Add your logo files
docs/logo/light.svg  # Logo for light mode
docs/logo/dark.svg   # Logo for dark mode
docs/favicon.svg     # Browser favicon
```

**Logo Requirements:**

- SVG format recommended
- Light mode: Dark logo on transparent background
- Dark mode: Light logo on transparent background
- Favicon: Simple icon, 32x32px or 64x64px

### 2. Update Contact Information

Edit `docs/mint.json`:

```json
{
  "topbarLinks": [
    {
      "name": "Support",
      "url": "mailto:your-support@email.com" // ← Update this
    }
  ],
  "topbarCtaButton": {
    "name": "Dashboard",
    "url": "https://your-dashboard-url.com" // ← Update this
  }
}
```

### 3. Update Social Links

Edit `docs/mint.json`:

```json
{
  "footerSocials": {
    "twitter": "https://twitter.com/your-handle", // ← Update
    "github": "https://github.com/your-org", // ← Update
    "linkedin": "https://linkedin.com/company/your" // ← Update
  }
}
```

### 4. Update API Base URL

Edit `docs/mint.json`:

```json
{
  "api": {
    "baseUrl": "https://your-api-url.com", // ← Update this
    "auth": {
      "method": "key",
      "name": "api-key"
    }
  }
}
```

## 📝 Adding More Documentation

### Create a New Page

1. Create a new `.mdx` file:

```bash
touch docs/guides/deposits.mdx
```

2. Add frontmatter:

```mdx
---
title: "Deposit Guide"
description: "Learn how to process deposits"
---

# Content here
```

3. Add to navigation in `mint.json`:

```json
{
  "navigation": [
    {
      "group": "Guides",
      "pages": [
        "guides/testing",
        "guides/deposits" // ← Add here
      ]
    }
  ]
}
```

### Create API Reference Pages

For endpoint documentation, use this template:

````mdx
---
title: "Get User"
api: "GET /api/v1/users/{user_id}"
description: "Retrieve user details"
---

## Headers

<ParamField header="api-key" type="string" required>
  Your API key
</ParamField>

## Path Parameters

<ParamField path="user_id" type="string" required>
  The user ID
</ParamField>

## Response

<ResponseField name="id" type="string">
  User ID
</ResponseField>

<RequestExample>
  \```bash cURL curl --request GET \ --url
  https://hpay-api.host-sl.com/api/v1/users/user_123 \ --header 'api-key:
  YOUR_API_KEY' \```
</RequestExample>

<ResponseExample>
\```json 200
{
  "id": "user_123",
  "name": "John Doe"
}
\```
</ResponseExample>
````

## 🌐 Deployment Options

### Option 1: Deploy to Mintlify (Recommended)

1. **Sign Up**: Go to [mintlify.com](https://mintlify.com) and create an account

2. **Connect GitHub**: Link your repository

3. **Configure**:

   - Build directory: `docs`
   - Auto-deploy on push: ✅

4. **Deploy**: Your docs will be live at `yourapp.mintlify.app`

5. **Custom Domain** (Optional):
   - Add CNAME record: `docs.yourdomain.com → cname.mintlify.dev`
   - Configure in Mintlify dashboard

### Option 2: Deploy to Vercel

```bash
# Install Vercel CLI
npm i -g vercel

# Deploy
cd docs
vercel

# Follow prompts to deploy
```

### Option 3: Self-Host

```bash
# Build static site
cd docs
mintlify build

# Output in .mintlify directory
# Serve with any static hosting (nginx, Apache, etc.)
```

## 🔧 Development Tips

### Test Locally Before Deploying

```bash
# Start dev server
mintlify dev

# Check for broken links
mintlify broken-links

# Build to verify no errors
mintlify build
```

### Hot Reload

The dev server supports hot reload. Any changes to `.mdx` files or `mint.json` will automatically refresh the browser.

### Preview Specific Pages

```bash
mintlify dev --path /api-reference/users/create
```

## 📚 Next Steps

### 1. Complete API Reference

Create documentation for all endpoints:

- `docs/api-reference/users/list.mdx`
- `docs/api-reference/users/get.mdx`
- `docs/api-reference/users/update.mdx`
- `docs/api-reference/wallets/create.mdx`
- `docs/api-reference/wallets/get.mdx`
- `docs/api-reference/transactions/*`

### 2. Add More Guides

- `docs/guides/deposits.mdx` - How to process deposits
- `docs/guides/transfers.mdx` - Wallet-to-wallet transfers
- `docs/guides/payouts.mdx` - Withdrawals and payouts
- `docs/guides/wallets.mdx` - Wallet management

### 3. Enhance Webhook Documentation

- `docs/webhooks/events.mdx` - All webhook events
- `docs/webhooks/security.mdx` - Security best practices
- `docs/webhooks/testing.mdx` - Testing webhooks

### 4. Add Code Examples

For each endpoint, provide examples in:

- cURL
- Python
- JavaScript/Node.js
- PHP
- Ruby
- Go

### 5. Add Images and Diagrams

```bash
# Create images directory
mkdir -p docs/images

# Add screenshots, diagrams, etc.
docs/images/dashboard-screenshot.png
docs/images/flow-diagram.svg
```

Use in documentation:

```mdx
![Dashboard](./images/dashboard-screenshot.png)
```

## 🐛 Troubleshooting

### Port Already in Use

```bash
# Kill process on port 3000
lsof -ti:3000 | xargs kill -9

# Or use different port
mintlify dev --port 3001
```

### Changes Not Showing

1. Hard refresh browser (Cmd+Shift+R or Ctrl+Shift+R)
2. Restart dev server
3. Clear browser cache

### Navigation Not Updating

1. Check `mint.json` for syntax errors
2. Ensure file paths are correct (no leading `/`)
3. Restart dev server

### Images Not Loading

1. Place images in `docs/images/` directory
2. Use relative paths: `/images/filename.png`
3. Ensure correct file extension case

## 📞 Support

- **Mintlify Docs**: https://mintlify.com/docs
- **Mintlify Discord**: https://discord.gg/mintlify
- **HOST Pay Support**: support@hostpay.com

## ✨ Features to Explore

Mintlify provides many advanced features:

- **API Playground**: Interactive API testing
- **OpenAPI Integration**: Auto-generate docs from OpenAPI spec
- **Search**: Built-in search functionality
- **Analytics**: Track documentation usage
- **Versioning**: Multiple documentation versions
- **Custom Components**: Build React components for docs

Check the [Mintlify documentation](https://mintlify.com/docs) to learn more!

## 🎉 You're All Set!

Your documentation foundation is ready. Now:

1. Start the dev server: `mintlify dev`
2. Add your branding (logos, colors)
3. Complete the API reference
4. Add more guides
5. Deploy to Mintlify or your hosting platform

Happy documenting! 📖✨
