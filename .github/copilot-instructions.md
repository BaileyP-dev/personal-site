# EcommerceDude Personal Site
EcommerceDude personal site is an Astro-based static website that serves as a landing page with newsletter signup functionality. The site promotes Shopify tips, tricks, and YouTube content with a ConvertKit newsletter integration.

**ALWAYS reference these instructions first and fallback to search or bash commands only when you encounter unexpected information that does not match the info here.**

## Working Effectively

### Bootstrap and Setup
- **Install dependencies**: `npm install` -- takes ~10-15 seconds
- **NEVER CANCEL**: All build commands complete quickly (under 5 seconds), but set timeout to 30+ seconds to be safe

### Building the Project
- **Development build**: `npm run dev` -- starts in ~350ms at `http://localhost:4321/`
- **Production build**: `npm run build` -- takes 2-3 seconds. NEVER CANCEL. Set timeout to 30+ seconds
- **Preview build**: `npm run preview` -- serves production build, starts in ~15ms at `http://localhost:4322/` (if 4321 is occupied)

### Running the Application
- **Development server**: `npm run dev`
  - Starts Astro dev server at `http://localhost:4321/`
  - Hot reload enabled
  - File watching active
  - Takes ~350ms to start
- **Production preview**: `npm run preview`
  - Serves built files from `./dist/`
  - Requires `npm run build` first

## Validation and Testing

### Manual Validation Scenarios
**ALWAYS run through these scenarios after making changes:**

1. **Homepage loads correctly**:
   - Navigate to `http://localhost:4321/`
   - Verify "ECOMMERCE DUDE" logo displays
   - Verify main headline: "Shopify tips, tricks & YouTube content"
   - Verify newsletter section appears with email input and subscribe button

2. **Newsletter form functionality**:
   - Enter test email in the form field
   - Click "SUBSCRIBE" button
   - Form should attempt to submit to ConvertKit (may be blocked in testing environments)
   - Input field should have placeholder "Your email address"

3. **Visual styling validation**:
   - Verify custom fonts load (Staatliches for headings, IBM Plex Sans for body)
   - Verify color scheme: light gray background (#F1F1F1), black text, purple subscribe button
   - Verify responsive layout works on different screen sizes

### Build Validation
- **Always run**: `npm run build` before committing changes
- **Build output**: Check that `./dist/` directory is created with static files
- **Build should complete**: Under 3 seconds with no errors

## Technology Stack and Configuration

### Core Technologies
- **Astro**: v5.12.3 (Static Site Generator)
- **TailwindCSS**: v4.1.11 (Styling framework)
- **TypeScript**: Configured with strict mode
- **Node.js**: Required for development

### Key Configuration Files
- `astro.config.mjs`: Main Astro configuration with TailwindCSS plugin
- `package.json`: Dependencies and npm scripts
- `tsconfig.json`: TypeScript configuration extending Astro strict preset
- `src/styles/global.css`: Global styles and custom font definitions

### Project Structure
```
/
├── .github/              # GitHub configuration
├── .vscode/              # VS Code settings (Astro extension recommended)
├── public/               # Static assets
│   ├── favicon.svg       # Main favicon
│   ├── favicon-light.svg # Light mode favicon
│   ├── favicon-dark.svg  # Dark mode favicon
│   └── fonts/            # Custom font files
├── src/
│   ├── components/       # Astro components
│   │   └── Welcome.astro # Main homepage component
│   ├── layouts/          # Layout components
│   │   └── Layout.astro  # Base HTML layout
│   ├── pages/            # Page routes
│   │   └── index.astro   # Homepage
│   └── styles/           # Stylesheets
│       └── global.css    # Global styles and fonts
├── astro.config.mjs      # Astro configuration
├── package.json          # Dependencies and scripts
└── tsconfig.json         # TypeScript configuration
```

## Important Code Locations

### Frequently Modified Files
- `src/components/Welcome.astro`: Main homepage content and newsletter form
- `src/layouts/Layout.astro`: HTML head configuration, meta tags, fonts
- `src/styles/global.css`: Custom fonts and global styling
- `package.json`: Dependencies and build scripts

### Newsletter Integration
- Newsletter form integrated with ConvertKit
- Form action: `https://app.kit.com/forms/8396869/subscriptions`
- JavaScript: `https://f.convertkit.com/ckjs/ck.5.js`
- Form includes email validation and loading states

### Custom Fonts
Four custom font families are loaded:
- **Staatliches**: Used for headings and logo
- **IBM Plex Sans**: Used for body text and paragraphs
- **Roboto Condensed**: Used for some headings
- **Nanum Pen Script**: Script font for decorative elements

## Common Development Tasks

### Making Content Changes
- **Homepage content**: Edit `src/components/Welcome.astro`
- **Page metadata**: Edit `src/layouts/Layout.astro`
- **Styling changes**: Edit `src/styles/global.css` or component-level styles

### Adding New Pages
- Create new `.astro` files in `src/pages/`
- Import and use `Layout.astro` for consistent structure
- Pages automatically become routes based on file structure

### Styling Updates
- **TailwindCSS**: Use utility classes directly in Astro components
- **Custom CSS**: Add to `src/styles/global.css` or component `<style>` blocks
- **Fonts**: Font files located in `public/fonts/`, definitions in `global.css`

## Astro CLI Commands
- `npm run astro add <integration>`: Add Astro integrations
- `npm run astro check`: Type checking (requires `@astrojs/check` package)
- `npm run astro --help`: View all available commands

## Limitations and Notes
- **No test suite**: Project does not include automated tests
- **No linting**: No ESLint or Prettier configuration
- **No CI/CD**: No GitHub Actions workflows configured
- **Static site**: Builds to static files, no server-side functionality
- **External dependencies**: Newsletter form depends on ConvertKit service

## Common Issues and Solutions
- **Port conflicts**: Dev server uses port 4321, preview uses 4322 if 4321 is occupied
- **Font loading**: Custom fonts may not load in some environments due to security restrictions
- **ConvertKit form**: Form submissions may be blocked in testing environments
- **Build artifacts**: `./dist/` directory is gitignored and recreated on each build