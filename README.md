# Link CPR — Broken Link Auto-Healer for WordPress

Link CPR scans your WordPress site for broken links, automatically finds replacements using the **Wayback Machine (archive.org)** or **relevant internal posts**, and lets you fix them from a clean, modern dashboard.

![License](https://img.shields.io/badge/license-GPL--2.0%2B-blue)
![WordPress](https://img.shields.io/badge/WordPress-5.8%2B-21759b)
![PHP](https://img.shields.io/badge/PHP-7.4%2B-777bb4)
![Version](https://img.shields.io/badge/version-1.0.0-brightgreen)

## Features

- 🔍 **Automatic scanning** of posts, pages, and any public custom post type for broken links (and optionally broken images).
- 🩹 **Auto-healing** via:
  - Wayback Machine (archive.org) snapshot lookup
  - Smart internal link suggestions based on link text
  - Manual URL replacement
  - Safe link removal (keeps the anchor text, strips the link)
- ↩️ **Undo** any fix and restore the original URL.
- 📅 **Scheduled scanning** (hourly, twice daily, daily, weekly) via WP-Cron, with batch processing so large sites don't time out.
- ⚡ **Rescan on save** — newly published/updated content is checked automatically.
- 🚫 **Exclude URL patterns** you don't want scanned (e.g. known-slow third-party domains).
- 📊 **Modern dashboard** with live stats, a 7-day activity chart, bulk-fix actions, filters (post type / status code / date), and pagination.
- 📧 **Email reports** and optional **Slack webhook** notifications after each scan.
- 📁 **CSV export** of all scanned links.
- 🔒 Nonce + capability checks on every admin action.

## Requirements

- WordPress 5.8 or newer
- PHP 7.4 or newer
- `DOMDocument` PHP extension (bundled with virtually all PHP installs)

## Installation

### Option A — Upload via WordPress Admin

1. Download the plugin ZIP from this repository.
2. In your WordPress admin, go to **Plugins → Add New → Upload Plugin**.
3. Choose the downloaded ZIP file and click **Install Now**.
4. Click **Activate**.

### Option B — Manual (FTP/SFTP)

1. Download and unzip the plugin.
2. Upload the `link-cpr` folder to `wp-content/plugins/`.
3. In WordPress admin, go to **Plugins** and activate **Link CPR**.

## Getting Started

1. After activation, open **Link CPR → Dashboard** in your WP admin menu.
2. Click **Start New Scan** to queue all posts/pages for checking.
3. Once the scan finishes, go to **Scan Results** to review broken links and fix them individually or in bulk.
4. Visit **Settings** to configure:
   - Which post types to scan
   - Scan frequency
   - Auto-fix rules (archive, internal linking, remove fallback)
   - Email / Slack notifications
   - Batch size, request timeout, and rate-limit delay

## How It Works

- The scanner extracts every `<a href>` (and optionally `<img src>`) from your content and checks its HTTP status.
- Links returning `4xx`/`5xx`/connection errors are marked broken; unresolved `3xx` redirect chains are flagged separately.
- For each broken link, Link CPR looks up the nearest working snapshot on the Wayback Machine and searches your own site for a relevant internal post, so you can pick the best replacement with one click.
- Fixes rewrite the URL directly in the post content and are logged, with the ability to undo.

## Frequently Asked Questions

**Does this slow down my site for visitors?**
No — all scanning happens in the admin area via WP-Cron/AJAX, never on the front end.

**Will it modify my content without asking?**
No. Link CPR only proposes fixes; nothing is changed until you click a fix button (or a bulk-fix action you triggered).

**Can I exclude certain domains from scanning?**
Yes, under Settings → Exclude URL Patterns, one pattern per line.

## License

GPL-2.0+. See LICENSE for details.
