# HashLordz

A web application for mining on the Abstract network. This repository contains the production build of the HashLordz mining interface.

## Overview

HashLordz is a React-based application that provides a user interface for mining operations on the Abstract blockchain network. The application enables users to interact with mining contracts and manage their mining activities through a modern web interface.

## Project Structure

This directory contains the production build output of the HashLordz application. The structure includes:

```
hashlordz_miner_build/
├── index.html              # Main HTML entry point
├── manifest.json           # Web app manifest
├── asset-manifest.json     # Asset mapping for build files
├── robots.txt              # Search engine directives
├── favicon.ico             # Application icon
├── logo192.png             # Application logo (192x192)
├── static/
│   ├── css/                # Compiled CSS files
│   ├── js/                 # Compiled JavaScript bundles
│   └── media/              # Static assets (fonts, images, SVGs)
├── whitepaper.pdf          # Project whitepaper
├── whitepaper_v1.2.pdf     # Whitepaper version 1.2
└── whitepaper-base.pdf     # Base whitepaper document
```

## Technology Stack

Based on the build artifacts, this application uses:

- **React 18.3.1** - UI framework
- **React Router v6.30.0** - Client-side routing
- **Viem** - Ethereum/blockchain interaction library
- **TypeScript** - Type-safe development (source code)
- **Webpack** - Module bundler (inferred from build structure)

## Deployment

### Prerequisites

- A web server (Apache, Nginx, or any static file server)
- Modern web browser with JavaScript enabled

### Static File Server

This is a static build that can be served by any web server. Deploy all files in this directory to your web server's document root.

#### Using a Simple HTTP Server

For local testing or development:

```bash
# Using Python 3
python -m http.server 8000

# Using Node.js (http-server)
npx http-server -p 8000

# Using PHP
php -S localhost:8000
```

Then access the application at `http://localhost:8000`

#### Production Deployment

1. Upload all files to your web server's document root
2. Ensure your web server is configured to:
   - Serve `index.html` for all routes (for React Router)
   - Enable gzip compression for JavaScript and CSS files
   - Set appropriate cache headers for static assets

### Nginx Configuration Example

```nginx
server {
    listen 80;
    server_name your-domain.com;
    root /path/to/hashlordz_miner_build;
    index index.html;

    location / {
        try_files $uri $uri/ /index.html;
    }

    location /static {
        expires 1y;
        add_header Cache-Control "public, immutable";
    }
}
```

### Apache Configuration Example

Add to your `.htaccess` file:

```apache
<IfModule mod_rewrite.c>
  RewriteEngine On
  RewriteBase /
  RewriteRule ^index\.html$ - [L]
  RewriteCond %{REQUEST_FILENAME} !-f
  RewriteCond %{REQUEST_FILENAME} !-d
  RewriteRule . /index.html [L]
</IfModule>
```

## Features

- Web-based mining interface for Abstract network
- Wallet integration for blockchain interactions
- Real-time mining statistics and monitoring
- Responsive design for desktop and mobile devices
- Progressive Web App (PWA) support via manifest.json

## Browser Support

The application requires a modern browser with JavaScript enabled. Recommended browsers:

- Chrome (latest)
- Firefox (latest)
- Safari (latest)
- Edge (latest)

## Security Considerations

- Ensure HTTPS is enabled for production deployments
- Validate all blockchain transactions on the client side
- Never expose private keys or sensitive credentials
- Review and configure Content Security Policy (CSP) headers appropriately

## Documentation

Additional project documentation is available in the whitepaper PDFs included in this directory:

- `whitepaper.pdf` - Main project whitepaper
- `whitepaper_v1.2.pdf` - Updated whitepaper version
- `whitepaper-base.pdf` - Base whitepaper document

## License

Please refer to the source code repository for license information. This build directory contains compiled assets from the original source code.

## Support

For issues, questions, or contributions, please refer to the main project repository or contact the development team.

## Notes

- This is a production build directory. Source code modifications should be made in the original repository and rebuilt.
- The application requires network connectivity to interact with the Abstract blockchain.
- Ensure your web server properly handles client-side routing for React Router.

