# Sources Metadata Guidelines

To support article references within the localized blog feeds (`blog_<lang>.json`), follow these rules when editing or reviewing JSON entries. The app will display sources at the bottom of each article when provided.

1. **Optional `sources` array** – Add a `sources` array to an article only when references exist. Omit the property or leave it empty if there are no sources.
2. **Source object format** – Each entry inside `sources` must include:
   - `title`: Short, user-facing text (host name or descriptive label). Leave it empty only when the app should automatically use the domain name.
   - `url`: Absolute HTTPS link. Tracking parameters prefixed with `utm_` will be stripped by the app, so the original link is acceptable.
3. **Ordering** – Preserve the desired button order by arranging the objects within the array accordingly.
4. **Validation checklist**:
   - Ensure `https://` is present in every URL.
   - Avoid duplicate URLs; identical values collapse into a single button in the UI.
   - Prefer titles under 40 characters so they fit on a single line.
5. **Rendering behavior** – Articles without a `sources` array (or with an empty one) will not show the "Sources" block.

### Example snippet

```json
{
  "id": "botulism_basics",
  "title": "Чому мед лише після 12 місяців",
  "teaser": "Як розпізнати ризики ботулізму",
  "cover": { "url": "https://example.com/cover.jpg" },
  "blocks": [ ... ],
  "sources": [
    {
      "title": "CDC guidance",
      "url": "https://www.cdc.gov/infant-toddler-nutrition/foods-and-drinks/foods-to-avoid-or-limit.html"
    },
    {
      "title": "NHS: Foods to avoid",
      "url": "https://www.nhs.uk/baby/weaning-and-feeding/foods-to-avoid-giving-babies-and-young-children/"
    }
  ]
}
```
