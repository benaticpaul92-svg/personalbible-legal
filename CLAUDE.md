# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## What this repository is

This is **not application code**. It is the public-facing legal and support documentation for the **Personal Bible** iOS app (a separate codebase). The repository contains two Markdown files served as static pages:

- `README.md` — the **Privacy Policy** (rendered as the index of the published site).
- `SUPPORT.md` — the **Support page** required by the App Store.

The published URL referenced from inside the app and from `SUPPORT.md` is `https://jebnengineering.com/personalbible-legal/`. Edits land in production by being pushed to the repo's default branch — there is no build, no tests, no lint, and no CI to run locally. Changes are documentation changes.

## Editing conventions to preserve

These conventions exist because the documents are App Store compliance artifacts, not marketing copy. Future edits must keep them intact.

1. **Date stamps are load-bearing.** `README.md` opens with `**Effective <Month Day, Year>**`; `SUPPORT.md` opens with `**Last updated: <Month Day, Year>**`. Update these whenever the substance of the file changes. Don't add a date to a file that doesn't already have one, and don't change the labels (`Effective` vs `Last updated`) — they mean different things legally.

2. **The privacy policy has a version number.** See the "Changes to this policy" section of `README.md`: the in-app version number must be bumped when the policy materially changes, and the document tracks "The current policy version is N". When making material privacy changes, increment that number; don't bump it for typo fixes.

3. **Contact email is canonical.** Every "contact us" / data-rights reference uses `martin@jebnengineering.com`. If this ever changes, update it everywhere in both files — the GDPR/CCPA rights section in `README.md` lists it four times.

4. **Named third parties must stay accurate.** `README.md` discloses the exact processors used (Supabase in AWS `ap-southeast-1`, Firebase Analytics, Firebase Crashlytics, Apple StoreKit). Under GDPR these disclosures are a legal commitment — never add or remove a processor here without an explicit instruction, and never change the AWS region string without confirming the actual backend region.

5. **Pricing and tier names mirror the App Store listing.** `SUPPORT.md` documents three tiers (Pro Monthly $2.99/mo, Pro Annual $24.99/yr, Pro Lifetime $59.99) with a 3-day free trial on the recurring tiers. These must match the StoreKit configuration in the iOS app — don't change prices, trial length, or tier names speculatively.

6. **Cross-links go through the published domain.** `SUPPORT.md` links to the privacy policy as `https://jebnengineering.com/personalbible-legal/`, not as a relative `README.md` link. Keep absolute URLs when linking between these documents, because they're read both on GitHub and on the hosted site.

7. **The closing epigraph in `SUPPORT.md`** (the Isaiah 43:1 quote after the `---`) is intentional voice. Leave it in place.

## What "done" looks like for an edit

Because there is no test or lint step, the bar for a change is:

- The relevant date stamp at the top of the file is updated.
- If the change is material to privacy practice, the policy version number in `README.md` is incremented.
- Internal references (email, processor names, region, pricing) are consistent across both files.
- Commit and push to the branch specified in the task; do not open a PR unless explicitly asked.
