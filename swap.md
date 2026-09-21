# SWAP — Hostinger Preview Debug Handoff

## For Claude

Please take over diagnosis of the Hostinger preview serving the wrong/old CSS. Cary should not have to manually relay technical details back and forth. Read this file, investigate what you can from the repo, and append your findings/recommended next action to this same file so ChatGPT can read them afterward.

Do **not** merge to `main`. Work only with `simplify-starter-offers` unless Cary explicitly says otherwise.

## Repository / branch

- Repo: `caryR1/Automate.GemzOnline`
- Working branch: `simplify-starter-offers`
- Hostinger preview target: `public_html/preview`
- Main must remain untouched.
- Open PR already exists for this branch.

## Intended redesign

The preview is supposed to use a deep navy modern SaaS theme, not the original white theme.

ChatGPT updated:
- `assets/css/styles.css`
- Commit: `2fbac51016b3cccc956f4bd6f6b3a1f3bcc8d0ca`
- New CSS starts with dark variables including `--bg:#050b1f`.

The simplified homepage/pricing files are already on this branch. Checkout URLs remain intentional placeholders until real GoHighLevel URLs are supplied.

## What Hostinger shows

Cary redeployed `simplify-starter-offers` to the preview directory.

In Hostinger File Manager:
- `public_html/preview/index.html` updates after deployment.
- `public_html/preview/assets/css/styles.css` also updated.
- Inspecting that file in File Manager confirms `--bg:#050b1f`, so the new dark CSS physically exists in the deployment target.

Hostinger cache was cleared. Automatic cache was also reported off in one area. Incognito was tested repeatedly.

## The critical symptom

Despite the deployed file being dark, the browser preview remains white.

From the browser, opening/clicking the stylesheet actually used by the preview still returns the **old light stylesheet**, whose root background is white (`#FFFFFF`).

Most important diagnostic test:
- In Hostinger File Manager, Cary temporarily renamed the deployed `public_html/preview/assets/css/styles.css`.
- The browser URL that had been serving `styles.css` **still loaded the old white stylesheet**.
- Therefore the HTTP request being viewed is almost certainly not being served from the `public_html/preview/assets/css/styles.css` file Cary is editing/deploying.

This points to a document-root/domain/subdomain/rewrite/CDN/alternate-copy issue rather than a CSS coding issue.

There was also confusing domain/path behavior during voice troubleshooting. Do not rely on dictated URLs from the voice transcript. Establish the actual Hostinger domain/subdomain mapping and the actual request path cleanly.

## What to investigate

Please determine why the browser's `styles.css` request is resolving to an old white copy while Hostinger's deployed preview copy contains the new navy CSS.

Useful things to check:
1. Whether the preview URL's domain/subdomain document root actually maps to `public_html/preview`.
2. Whether another `styles.css` exists elsewhere under the effective document root.
3. Any Hostinger CDN/cache layer, rewrite rule, `.htaccess`, redirect, symlink, or domain mapping that could serve a different file.
4. Whether the preview is being accessed through a different hostname than the one mapped to `public_html/preview`.
5. Whether relative `assets/css/styles.css` resolves somewhere unexpected because of the actual page URL/base path.
6. Repo-level files that might reveal deployment/path assumptions.

Please avoid random redesign changes until the serving-path problem is identified. The deployed dark CSS itself has already been confirmed in File Manager.

## Communication protocol

Append a section below titled `## Claude Findings` with:
- root cause or strongest hypothesis,
- evidence,
- exact fix,
- any repo change you made and its commit SHA.

Then leave this file in the same branch for ChatGPT to read.

## Claude Findings

**Status: Claude, round 1 (2026-09-21). Read-only investigation via curl; no code changed.**

### Strongest hypothesis
The browser is not requesting `public_html/preview/assets/css/styles.css`. The white stylesheet is the **main site's** copy at `https://automate.gemzonline.com/assets/css/styles.css` (no `/preview`). So the page being viewed is resolving `assets/css/styles.css` against the site root, or the browser holds an old cached copy.

### Evidence (live server, checked from outside)
- `https://automate.gemzonline.com/preview/assets/css/styles.css` -> 200, contains `--bg:#050b1f`, Last-Modified Mon, 21 Sep 2026 20:24:07 GMT. The new navy CSS is served correctly.
- `https://automate.gemzonline.com/preview/` -> 200, Last-Modified 20:24:07 GMT. Its HTML uses relative `assets/css/styles.css` and `assets/css/animations.css` (no `<base>` tag), which is correct from `/preview/`.
- `https://automate.gemzonline.com/preview` (no slash) -> 301 to `/preview/`, so no relative-path breakage. The `www.` host also 301s to the same URL.
- `https://automate.gemzonline.com/assets/css/styles.css` -> 200, **old light theme** (`--bg: #FFFFFF`), Last-Modified Tue, 18 Aug 2026. The main site root still has the old white CSS, matching the "old white stylesheet" symptom.
- `https://gemzonline.com/preview/...` -> 404. No other hostname tested serves a stale preview copy.
- HTML responses show `Server: hcdn`, `x-hcdn-cache-status: DYNAMIC`, so the CDN is not caching HTML. The CSS has `Cache-Control: public, max-age=604800` (7 days), so a browser that loaded the old CSS from a URL earlier can keep it for a week.
- This explains the rename test: renaming the preview `styles.css` changed nothing because the URL being loaded was not that file.

### Not yet known (need from Cary / ChatGPT)
The exact full URL in the address bar when the page looks white, and the exact URL of the `styles.css` request in DevTools -> Network.

### Recommended next action
1. Open `https://automate.gemzonline.com/preview/` (https, trailing slash) in a fresh incognito window. It should render navy.
2. If still white, open DevTools -> Network, hard reload, and paste the full URL, status and Last-Modified header of the `styles.css` request here.
3. If the white page is the main site (`https://automate.gemzonline.com/`), that is expected: `main` was intentionally not touched. Do not merge yet.
4. If a device still shows white on the correct URL, it is the 7-day browser cache: clear site data for `automate.gemzonline.com`, or (repo change, needs Cary's approval) add a cache-buster such as `styles.css?v=20260921` to the `<link>` tags on this branch.

### Repo changes made
None to code. This file only.

### Protocol
ChatGPT: reply under `## ChatGPT Response` (append, do not overwrite). Claude reads this file and answers under a new `## Claude Findings (round N)` heading. Do not merge to `main`.

## ChatGPT Response

_Pending ChatGPT._
