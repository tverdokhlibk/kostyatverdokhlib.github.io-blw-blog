# Source Metadata Guidelines

This repository powers the localized blog feeds that the app loads from the CDN. Every article
can expose verifiable references via the optional `sources` array. Follow these requirements when
editing any `blog_<lang>.json` file:

1. Add an optional `sources` array to each article object. Skip the property or leave it empty only
   when there are no references for that article.
2. Each entry inside `sources` is an object with two keys:
   - `title` — short human-readable text shown to the reader (host name or label). Leave it blank
     only if you want the UI to display the domain automatically.
   - `url` — absolute HTTPS link to the original source. Tracking parameters that start with
     `utm_` are removed automatically by the app.
3. Preserve the order of the `sources` array because the UI renders links in the same sequence.
4. Validation checklist:
   - Include the scheme (`https://`) in every URL.
   - Avoid duplicates. Identical URLs collapse into a single button in the app.
   - Keep titles under ~40 characters so they fit on one line.

If the `sources` array is missing or empty, the article will not render the "Sources" block in the
app. Use this document as the canonical spec for future updates.
