---
ID: 7767
post_title: Installing Bedrock
author: Ben Word
post_excerpt: ""
layout: doc
permalink: >
  https://roots.io/bedrock/docs/installing-bedrock/
published: true
post_date: 2015-10-15 12:29:33
---
## Requirements

* PHP >= 5.6
* Composer - [Install](https://getcomposer.org/doc/00-intro.md#installation-linux-unix-osx)

## Installation

1. Create a new project - `composer create-project roots/bedrock`
2. Copy `.env.example` to `.env` and update environment variables:
  * `DB_NAME` - Database name
  * `DB_USER` - Database user
  * `DB_PASSWORD` - Database password
  * `DB_HOST` - Database host
  * `WP_ENV` - Set to environment (`development`, `staging`, `production`)
  * `WP_HOME` - Full URL to WordPress home (http://example.com)
  * `WP_SITEURL` - Full URL to WordPress including subdirectory (http://example.com/wp)
  * `AUTH_KEY`, `SECURE_AUTH_KEY`, `LOGGED_IN_KEY`, `NONCE_KEY`, `AUTH_SALT`, `SECURE_AUTH_SALT`, `LOGGED_IN_SALT`, `NONCE_SALT` - Generate with [wp-cli-dotenv-command](https://github.com/aaemnnosttv/wp-cli-dotenv-command) or from the [Roots WordPress Salt Generator](https://roots.io/salts.html)
3. Add theme(s) in `web/app/themes` as you would for a normal WordPress site.
4. Set your site vhost document root to `/path/to/site/web/` (`/path/to/site/current/web/` if using deploys)
5. Access WP admin at `http://example.com/wp/wp-admin`

### Multisite

Bedrock is multisite network compatible, but needs the [multisite-url-fixer](https://github.com/roots/multisite-url-fixer) mu-plugin on subdomain installs to make sure admin URLs function properly. This plugin is not _needed_ on subdirectory installs, but will work well with them. 

Run `composer require roots/multisite-url-fixer` to install the package. It will automatically install as an mu-plugin thanks to the [mu-plugins autoloader](https://roots.io/bedrock/docs/mu-plugins-autoloader/).