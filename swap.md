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

_Pending Claude._
