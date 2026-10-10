# GitHub Runner Drive ADC — OAuth Branding Site

A minimal public informational website for a personal, operator-managed Google Drive integration. It is intentionally kept **separate** from the private `chatgpt-context` repository.

## Files
- `index.html` — homepage
- `privacy.html` — privacy policy
- `terms.html` — terms of service
- `assets/style.css` — responsive styling

There are **no external scripts, authorization flows, credentials, or internal configuration** in these pages.

## Before publishing

Review the wording of every public page, especially claims about processing, retention, sharing, and contact. Confirm the displayed OAuth app name matches the Google Auth Platform Branding configuration. The operator's support email is referred to through the Google consent screen rather than printed on this website.

## Deploy to a dedicated public repository

1. Create a **new public repository**, e.g. `github-runner-drive-adc-site`, under the appropriate GitHub user account. Do not make the private context repository public.
2. Upload the contents of this folder to the **repository root** on `main`, preserving file names and the `assets/` directory.
3. In repository **Settings → Pages**, choose **Deploy from a branch**, branch **main**, folder **/(root)**, and Save.
4. Wait for deployment, then open the actual Pages URL in a signed-out/private browser and verify home, privacy, and terms work; links must return HTTPS pages without login or cross-domain redirects.
5. Connect an owned **custom domain** through **Settings → Pages → Custom domain**, and configure the recommended DNS record with your domain provider. Enable HTTPS after GitHub has issued its certificate. The default github.io URL is not a guarantee of acceptance for Google OAuth verified-domain requirements.
6. Using a Google account that owns/edits the intended GCP project, verify the **custom root domain** in Google Search Console as a **Domain property via DNS TXT record**. The same domain must be listed under OAuth **Authorized domains**. Confirm verification before submitting branding.
7. Set the final publicly reachable HTTPS homepage URL, privacy-policy URL, and (if used) terms URL in Google Auth Platform Branding. Ensure the homepage links to the exact privacy policy URL. For a custom domain with this site at root: `https://YOUR-DOMAIN/`, `https://YOUR-DOMAIN/privacy.html`, `https://YOUR-DOMAIN/terms.html`.
8. Complete any Google-specific app verification requirements, then transition to In production. Changing publishing status does **not** revalidate an expired refresh token. Reauthorize only via the maintained bootstrap described in the *private* repository's `docs/artifact-runtime.md`, within the appropriate operator maintenance boundary.

## Hard stops

- Never put the Google Desktop OAuth client JSON, user OAuth credential, refresh token, host credential paths, or transcript/source data here.
- Never put private repository content in this public site.
- Do not claim Google verified or accepted the app until Console confirms it.
- Do not use the site's GitHub Pages URL as an OAuth redirect URI; the maintained Desktop OAuth helper uses its own loopback flow.
- Keep OAuth `drive.file` and OIDC/WIF control access distinct.

Google requirements: https://support.google.com/cloud/answer/13464321 and https://support.google.com/cloud/answer/13804266. GitHub Pages domain configuration: https://docs.github.com/en/pages/configuring-a-custom-domain-for-your-github-pages-site/managing-a-custom-domain-for-your-github-pages-site
