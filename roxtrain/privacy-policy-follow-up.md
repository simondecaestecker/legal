# Proposal for the next privacy-policy review

## Status as of October 5, 2026: live pages not updated or published

The public source that generates `https://roxtrain.app/en/privacy/` and `https://roxtrain.app/fr/privacy/` has not been located or accessed. Those pages remain stale; this repository change does not modify or publish them. The app and paywall links to `roxtrain.app` therefore still open the stale live policy. Fastlane privacy URLs continue to point to the GitHub Pages legal copy and are unchanged; they will show this revision after the branch is merged and the legal site is deployed.

When the live source becomes available, update both language versions to match `privacy.html`: distinguish the first-party announcements API request (language and app/device User-Agent, used for version distribution) from the conditional image load (any HTTPS host, which may receive the device IP and image-request metadata when displayed); document user-initiated backup contents and key limitation; document the confirmed debug-report creation, explicit email/share action, encryption caveat, and temporary-file cleanup; describe local notifications only and the scope/limits of Delete All. Preserve the pre-launch email section and all other existing live content. Publish and verify both live routes without changing the `roxtrain.app` or Fastlane policy URLs.
