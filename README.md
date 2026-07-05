# HOST Pay API Documentation

This directory contains the Mintlify documentation for the HOST Pay API.

## Setup

### Prerequisites

- Node.js 18+ and npm
- Mintlify CLI

### Installation

1. Install Mintlify CLI:

```bash
npm i -g mintlify
```

2. Navigate to the docs directory:

```bash
cd docs
```

3. Start the development server:

```bash
mintlify dev
```

The documentation will be available at `http://localhost:3000`.

## Project Structure

```
docs/
├── mint.json                 # Main configuration file
├── introduction.mdx          # Homepage
├── quickstart.mdx           # Getting started guide
├── authentication.mdx       # Authentication guide
├── environments.mdx         # Test vs Live modes
├── api-reference/           # API endpoint documentation
│   ├── introduction.mdx
│   ├── users/
│   ├── wallets/
│   ├── transactions/
│   └── applications/
├── guides/                  # Integration guides
│   ├── deposits.mdx
│   ├── transfers.mdx
│   ├── payouts.mdx
│   └── testing.mdx
├── webhooks/               # Webhook documentation
│   ├── overview.mdx
│   ├── events.mdx
│   ├── security.mdx
│   └── testing.mdx
└── changelog/              # Version history
    └── overview.mdx
```

## Configuration

The `mint.json` file contains:

- Navigation structure
- Color scheme
- Logo and favicon paths
- API base URL
- Tab configuration

### Customization

#### Update Branding

1. Add your logo files to `/logo/` directory:

   - `light.svg` - Logo for light mode
   - `dark.svg` - Logo for dark mode

2. Add favicon to root:
   - `favicon.svg`

#### Update Colors

Edit `mint.json`:

```json
{
  "colors": {
    "primary": "#8B5CF6",
    "light": "#A78BFA",
    "dark": "#7C3AED"
  }
}
```

#### Update Links

Update social links and external URLs in `mint.json`:

```json
{
  "topbarLinks": [...],
  "anchors": [...],
  "footerSocials": {...}
}
```

## Writing Documentation

### Page Structure

Each documentation page is a `.mdx` file with frontmatter:

```mdx
---
title: "Page Title"
description: "Page description for SEO"
---

# Content goes here
```

### Components

Mintlify provides built-in components:

#### Cards

```mdx
<Card title="Title" icon="icon-name" href="/link">
  Description text
</Card>
```

#### Card Groups

```mdx
<CardGroup cols={2}>
  <Card title="Card 1" icon="check">
    ...
  </Card>
  <Card title="Card 2" icon="star">
    ...
  </Card>
</CardGroup>
```

#### Code Blocks

````mdx
<CodeGroup>

\```python Python

# Python code

\```

\```javascript JavaScript
// JavaScript code
\```

</CodeGroup>
````

#### Accordions

```mdx
<AccordionGroup>
  <Accordion title="Title">Content</Accordion>
</AccordionGroup>
```

#### API Parameters

```mdx
<ParamField body="name" type="string" required>
  Description
</ParamField>
```

#### Response Fields

```mdx
<ResponseField name="id" type="string">
  Description
</ResponseField>
```

### API Documentation

API endpoints use special frontmatter:

````mdx
---
title: "Create User"
api: "POST /api/v1/users/"
description: "Create a new user"
---

<ParamField body="name" type="string" required>
  User's full name
</ParamField>

<RequestExample>\```bash cURL curl --request POST ... \```</RequestExample>

<ResponseExample>
\```json 200
{
  "id": "user_123"
}
\```
</ResponseExample>
````

## Deployment

### Deploy to Mintlify

1. Sign up at [mintlify.com](https://mintlify.com)

2. Connect your GitHub repository

3. Configure build settings:

   - Build command: (none needed)
   - Output directory: `docs`

4. Deploy

Your documentation will be available at your custom domain or `yourapp.mintlify.app`.

### Deploy to Vercel/Netlify

Mintlify docs can also be deployed to:

- Vercel
- Netlify
- Any static hosting service

## Testing

Before deploying, test locally:

```bash
# Start dev server
mintlify dev

# Check for broken links
mintlify broken-links

# Build for production
mintlify build
```

## Contributing

When adding new documentation:

1. Create the `.mdx` file in the appropriate directory
2. Add the page to navigation in `mint.json`
3. Test locally with `mintlify dev`
4. Submit a pull request

### Style Guide

- Use clear, concise language
- Include code examples in multiple languages
- Add visual elements (cards, accordions) for better UX
- Keep API reference consistent
- Update changelog for API changes

## Troubleshooting

### Common Issues

**Port already in use:**

```bash
# Kill process on port 3000
lsof -ti:3000 | xargs kill -9

# Or use a different port
mintlify dev --port 3001
```

**Navigation not updating:**

- Check `mint.json` syntax
- Ensure file paths are correct
- Restart the dev server

**Images not loading:**

- Place images in `/images/` directory
- Use relative paths: `/images/filename.png`
- Ensure file extensions are lowercase

## Resources

- [Mintlify Documentation](https://mintlify.com/docs)
- [Mintlify Components](https://mintlify.com/docs/components)
- [OpenAPI Support](https://mintlify.com/docs/api-playground/openapi)
- [Mintlify Community](https://discord.gg/mintlify)

## Support

For questions about:

- **HOST Pay API**: support@hostpay.com
- **Mintlify Platform**: support@mintlify.com
- **Documentation Issues**: Create an issue in this repository

## License

© 2025 HOST Pay. All rights reserved.
