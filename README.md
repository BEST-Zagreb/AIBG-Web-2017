# AIBG v3.0 website, autumn 2017 (archived edition)

Static archive of the AI Battleground v3.0 site: WordPress 4.9 with the Moesia theme, 10 pages and 11 news posts published between 2017-09-30 and 2017-12-09, plus the tag, category, author and date archives the posts link to. It was rebuilt from the backup a former maintainer left on the server in July 2018 (a MySQL data directory and the web root, found during the 2026 server retirement), not from a live site, and it is complete: every page the database listed as published is here. Every page is plain HTML; there is no database, no PHP and nothing to keep patched.

Home: **https://2017.aibg.best.hr/** (the site ran at **best.hr/aibg**)

- 21 published pages, 336 files, 11.7 MB
- Verified: every page and asset requested over HTTP, 295 URLs, **0 failures**, at the root and under a sub-path
- Verified: every page rendered in a browser, **0 broken images**
- Verified: after the deliberate changes below, the visible text and image list of every page match the 2018 install running in a container

## Looking at it locally

    python3 -m http.server 8000

Then open <http://127.0.0.1:8000/>. Any static file server works.

## How it was made

The 2018 database was started in a MySQL 5.7 container and the 2018 web root in a WordPress 4.9 container with PHP 7.2, the site's address rewritten to the container. The page list came from the database, not from what a crawler happened to find; the site was mirrored with `wget`, every page refetched raw, relinked to relative paths, and compared page by page with the container. Everything that would ask a server for something was stripped: feed, oEmbed, REST, RSD, shortlink and manifest links, the embed and comment-reply scripts, the comment forms. Google Analytics, Google Fonts, YouTube embeds and the other third-party loads the original pages made are kept. The tooling and the logs live in the migration notes alongside this archive.

## What deliberately differs from the 2018 pages

### Personal contact details

3 occurrences of the main organiser's e-mail address were replaced with **aibg@best.hr** and 3 occurrences of a mobile number were removed (contact page and its description). `wordpress@example.com` in the social menu is a theme placeholder and stays. This archive is public and outlives the students named in it.

### Repairs and limits

The database held 950 comments, none of them approved, and 97 application-form submissions; none of that is rendered on any page and none of it is in this repository. The Ninja Forms contact form on `kontakt/` renders as it did but cannot submit, since there is no server behind it. The apple-touch-icon links, which the 2018 install had mangled into a wrong path, point at the icon again.

## Editions

AIBG editions on the web: v3.0 of 2017 (this repository), the current site at [aibg.best.hr](https://aibg.best.hr/) ([AIBG-Web](https://github.com/BEST-Zagreb/AIBG-Web)); the AIBG Final 2023 in Zagreb at [aibgfinal.best.hr](https://aibgfinal.best.hr/). AIBG started in November 2015 as the successor of BEST Code Challenge (2010 to 2014).

## Hosting

Live at <https://2017.aibg.best.hr/>, served by Cloudflare Workers as static files straight from this repository. Every push to `main` is deployed by Workers Builds within a minute or two. Every page carries an archive notice and a `noindex` header, added at the edge by `banner.js`, so search engines keep sending people to the current site; the archived files themselves are untouched.

## Wayback Machine

This edition ran at <http://best.hr/aibg/>; the Internet Archive's calendar for it is <https://web.archive.org/web/*/best.hr/aibg*>, with captures from the period of this edition where the crawler reached them. This repository is the complete copy; the archive is a partial, independent second copy.

## Licence

The content, images and copy belong to BEST Zagreb. Third-party theme and plugin assets under `wp-content/` remain under their own licences and are included only because the pages need them to render as they originally did.
