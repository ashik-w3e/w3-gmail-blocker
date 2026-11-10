GitHub Pages upload package for ashik-w3e

Account: ashik-w3e
Repository name (exact): w3-gmail-blocker
Visibility: Public
Branch: main
Pages source: Deploy from a branch -> main -> / (root)

1. Sign into GitHub with the ashik-w3e account.
2. Create a PUBLIC repository named w3-gmail-blocker.
   If it already exists, inspect its contents before adding these files.
3. Extract this ZIP. Upload the CONTENTS of this directory into the repository
   root, not the ZIP itself and not a nested github-pages-upload folder.
   Files: gmail-login-blocker.crx, updates.xml, index.html, README.txt,
   SHA256SUMS, and .nojekyll if visible. The visible files also work with
   the default Jekyll build; .nojekyll explicitly disables that build step.
4. Commit to main. In Settings -> Pages select Deploy from a branch,
   main, / (root), Save. Enable Enforce HTTPS when available.
5. Wait for the Pages deployment to succeed. Verify these URLs:
   https://ashik-w3e.github.io/w3-gmail-blocker/updates.xml
   https://ashik-w3e.github.io/w3-gmail-blocker/gmail-login-blocker.crx
   The first must show an XML document, not a GitHub preview or 404 page.
   The second must download the original CRX, not an HTML page.

The proposed URL is NOT automatically published by creating this package.
Repository/Pages creation and live deployment have not been performed here.

Google Admin console
- Confirm the intended browser is enrolled in OU w3.
- Chrome browser -> Apps & extensions -> Users & browsers -> intended OU.
- + -> Add Chrome app or extension by ID.
- ID: oohmhidcoechagkkpocjiadkdnialfkk
- From a custom URL -> https://ashik-w3e.github.io/w3-gmail-blocker/updates.xml
- Save, then set Installation policy to Force install and Save.
- If offered an update URL override control, enable it for this same URL.
  The packaged manifest has no remote update_url, so ensure the effective
  cloud ExtensionSettings uses override_update_url=true for future updates.
- Scope the first test to the intended test browser/OU; root-OU policies can
  affect all browsers/users beneath that OU.

A standalone ExtensionSettings ENTRY for reference (merge into existing policy;
this is not extension-specific managed configuration JSON):
{"oohmhidcoechagkkpocjiadkdnialfkk":{"installation_mode":"force_installed","update_url":"https://ashik-w3e.github.io/w3-gmail-blocker/updates.xml","override_update_url":true}}
Do not paste this into the extension's own managed-configuration field.

Employee Windows browser
- Keep the previously blocked local policy uninstalled. Do not rerun the
  local Registry installer on this cloud-only PC.
- Open chrome://policy -> Reload policies. Check the effective cloud
  ExtensionSettings/ExtensionInstallForcelist entry is accepted.
- Open chrome://extensions. Confirm display name Google, version 0.2.6,
  installed by enterprise policy and UI removal/disabling unavailable.
- Allow the first-install Google logout tab to complete. Company accounts
  sign out too; sign back in with the full @w3engineers.com address.
- Test real company/personal login flows. This remains a best-effort Google
  login-page guard, not complete account-access enforcement.

Release checks
- CRX is byte-identical to the supplied original Chrome ZIP.
- ID derived from its public key matches the update manifest.
- XML version matches the CRX manifest; XML parses successfully.
- No signing key, credentials, enrollment tokens or employee data included.
- Live HTTPS availability, cloud-policy acceptance and Windows browser
  installation have not been tested for this hosting package.
- Future CRX releases require the original administrator's private signing key
  and a higher extension version. Do not repack using a new key.

References
https://docs.github.com/en/pages/getting-started-with-github-pages/creating-a-github-pages-site
https://support.google.com/chrome/a/answer/6177447?hl=en
