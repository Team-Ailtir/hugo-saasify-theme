# How to Use Hugo Saasify Theme

## Overview

Hugo Saasify Theme is a production-ready Hugo theme for building SaaS marketing websites with TailwindCSS. It includes 21 pre-built shortcodes, multiple page layouts, blog system, and comprehensive customization options.

---

## 🚀 Quick Start (5 Steps)

### 1. Create Your Hugo Site

```bash
# Create new Hugo site
hugo new site my-saas-website
cd my-saas-website

# Initialize git
git init
```

### 2. Add Theme as Submodule

```bash
# Add theme
git submodule add https://github.com/chaoming/hugo-saasify-theme.git themes/hugo-saasify-theme

# Update submodule
git submodule update --init --recursive
```

### 3. Copy Example Site (Recommended)

This gives you a working starting point with all features demonstrated:

```bash
# Copy everything from example site
cp -r themes/hugo-saasify-theme/exampleSite/* .
```

This includes:
- Complete content structure (homepage, blog, features, pricing, company pages)
- Fully configured `hugo.toml`
- Sample images and assets
- Working navigation menus

### 4. Install Dependencies

```bash
# Copy necessary config files (if not using example site)
cp themes/hugo-saasify-theme/package.json .
cp themes/hugo-saasify-theme/postcss.config.js .
cp themes/hugo-saasify-theme/tailwind.config.copy.js ./tailwind.config.js

# Install npm packages
npm install
```

### 5. Start Development Server

```bash
# Start dev server with hot reload
npm run start
```

Visit `http://localhost:1313` - your site is live!

---

## 📁 Project Structure

After setup, your structure looks like:

```
my-saas-website/
├── content/              # Your content (markdown files)
│   ├── _index.md        # Homepage
│   ├── blog/            # Blog posts
│   ├── features/        # Feature pages
│   ├── pricing.md       # Pricing page
│   ├── company.md       # Company page
│   └── careers.md       # Careers page
├── static/              # Static assets (images, fonts, etc.)
│   ├── images/
│   └── css/
├── layouts/             # Custom layout overrides (optional)
├── hugo.toml           # Main configuration file
├── tailwind.config.js  # TailwindCSS customization
└── themes/
    └── hugo-saasify-theme/  # The theme (submodule)
```

---

## ⚙️ Configuration

Your `hugo.toml` is the central configuration. Key sections:

### Basic Settings

```toml
baseURL = "https://yoursite.com/"
title = "Your SaaS Name"
theme = "hugo-saasify-theme"
defaultContentLanguage = "en"
```

### Header Configuration

Controls logo, buttons, and navigation styling:

```toml
[params.header]
  background = "bg-white/80 backdrop-blur-sm"
  border = "border-b border-gray-100"

  [params.header.logo]
    src = "/images/logo.svg"

  [params.header.buttons.signIn]
    text = "Sign in"
    url = "/signin"

  [params.header.buttons.getStarted]
    text = "Get Started"
    url = "/get-started"
```

### Global CTA (Call-to-Action)

Appears at bottom of pages:

```toml
[params.cta]
  enable = true
  title = "Ready to Get Started?"
  description = "Join companies using our platform"
  [params.cta.primary_button]
    text = "Get Started Free"
    url = "/get-started"
```

### Navigation Menu

Create dropdown menus with submenus:

```toml
[[menu.main]]
  name = "Features"
  weight = 1
  [menu.main.params]
    has_submenu = true
    submenu = [
      { name = "Performance", url = "/features/performance/" },
      { name = "Design System", url = "/features/design-system/" }
    ]
```

See `exampleSite/hugo.toml:192-220` for complete menu examples.

---

## 📝 Creating Content

### Homepage (`content/_index.md`)

Uses shortcodes to build sections:

```markdown
---
title: Home
---

{{< hero
    headline="Build Your SaaS Website"
    sub_headline="Create stunning, responsive websites"
    primary_button_text="Get Started Free"
    primary_button_url="/signup"
    hero_image="/images/hero-dashboard.svg"
>}}

{{< feature
    title="Lightning-Fast Performance"
    description="Leverage Hugo's blazing-fast build times"
    image="/images/feature-1.svg"
    imagePosition="right"
>}}

{{< cta >}}
```

### Blog Posts (`content/blog/my-post.md`)

```bash
# Create new blog post
hugo new blog/my-first-post.md
```

Front matter example:

```markdown
---
title: "My First Blog Post"
date: 2025-10-30
draft: false
categories: ["Tutorial"]
tags: ["hugo", "web development"]
author: "Your Name"
description: "A great post about Hugo"
---

Your content here...
```

### Feature Pages (`content/features/`)

Create feature pages with rich layouts using shortcodes:

```markdown
---
title: "Performance"
---

{{< features-list
    title="Performance Features"
    items="Sub-second page loads,Optimized assets,CDN-ready output"
>}}
```

### Other Page Types

- **Pricing**: Use `pricing-table-1` or `pricing-table-2` shortcodes
- **Company**: Use `team-member` and `value-card` shortcodes
- **Careers**: Use `jobs` content type with `careers.md` listing page

---

## 🎨 Using Shortcodes (21 Available)

Shortcodes are reusable components. Key ones:

### Hero Section

```markdown
{{< hero
    headline="Your Headline"
    sub_headline="Subheadline text"
    primary_button_text="Get Started"
    primary_button_url="/signup"
    hero_image="/images/hero.svg"
>}}
```

### Features

```markdown
{{< features-section
    title="Modern Features"
    description="What we offer"
>}}
  {{< feature
      title="Feature Name"
      description="Feature description"
      image="/images/feature.svg"
      imagePosition="right"
  >}}
{{< /features-section >}}
```

### Testimonials

```markdown
{{< testimonials
    title="What Customers Say"
    animate="true"
>}}
```

(Testimonials data comes from page front matter - see `content/_index.md:14-26`)

### Pricing Tables

```markdown
{{< pricing-table-1
    title="Simple Pricing"
    plans=[...]
>}}
```

### More Shortcodes

- `client-logos` - Animated logo carousel
- `faq` - FAQ accordion
- `team-member` - Team profiles
- `stat` - Statistics display
- `benefits-grid` - Benefit cards
- `case-study-card` - Case studies

Full documentation: [SHORTCODES.md][]

---

## 🎨 Customization

### Colors

Edit `tailwind.config.js`:

```js
colors: {
  primary: {
    50: '#f0f9ff',
    // ... your primary color scale
    900: '#0c4a6e',
  },
  secondary: {
    // ... your secondary colors
  }
}
```

### Typography

Change fonts in `tailwind.config.js`:

```js
fontFamily: {
  sans: ['Inter', 'system-ui', 'sans-serif'],
  heading: ['Plus Jakarta Sans', 'sans-serif'],
}
```

### Custom Styles

Add custom CSS to `assets/css/main.css` or override theme styles.

---

## 🚢 Building for Production

```bash
# Build optimized site
npm run build
```

This creates a `public/` directory with your production-ready site.

---

## 📚 Key Documentation Files

For comprehensive information, refer to:

1. **[SHORTCODES.md][]** - Master all 21 shortcodes for page building
2. **[CONFIGURATION.md][]** - Complete config reference
3. **[CONTENT-CREATION.md][]** - Content organization and SEO
4. **[STYLING.md][]** - Deep customization
5. **[DEPLOYMENT.md][]** - Deploy to Netlify, Vercel, GitHub Pages, etc.

---

## 🎯 Common Workflows

### Add a New Page

```bash
hugo new about.md
# Edit content/about.md
```

### Add Blog Post with Images

1. Create post: `hugo new blog/my-post.md`
2. Add image to `static/images/blog/my-image.jpg`
3. Reference in markdown: `![Alt text](/images/blog/my-image.jpg)`

### Add Analytics

Edit `hugo.toml`:

```toml
[params]
  googleAnalytics = "G-XXXXXXXXXX"
  googleTagManager = "GTM-XXXXXXX"
```

### Add Custom Tracking Scripts

Create `layouts/partials/custom-head.html`:

```html
<!-- Your custom scripts here -->
<script>
  // Hotjar, Mixpanel, etc.
</script>
```

---

## 🔧 Development Tips

1. **Hot Reload**: `npm run start` watches for changes
2. **Draft Posts**: Add `draft: true` in front matter, view with `hugo server -D`
3. **Example Site**: Reference `exampleSite/` for working examples
4. **Live Demo**: Check [demo site][] for inspiration

---

## 📖 Next Steps

1. **Customize branding**: Update logo, colors, fonts
2. **Create content**: Add your pages and blog posts
3. **Configure analytics**: Set up tracking
4. **Deploy**: Push to production (see [DEPLOYMENT.md][])

---

This theme is designed to be intuitive for intermediate users. The example site provides working examples of every feature, so you can learn by examining and modifying the existing content. Start with the homepage (`content/_index.md`) and work your way through the different page types!

[SHORTCODES.md]: docs/SHORTCODES.md
[CONFIGURATION.md]: docs/CONFIGURATION.md
[CONTENT-CREATION.md]: docs/CONTENT-CREATION.md
[STYLING.md]: docs/STYLING.md
[DEPLOYMENT.md]: docs/DEPLOYMENT.md
[demo site]: https://saasify-demo.chaoming.li
