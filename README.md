# blog-content

This repository stores generated blog content for a fleet of VPN-related
websites. Each website lives in its own domain-named folder under `sites/`.
The content here is intended to be consumed by external website update
workflows, so filenames, manifests, and post metadata should stay consistent.

## Folder Structure

```text
sites/
  example-domain.com/
    manifest.json
    posts/
      seo-slug.json
docs/
  SEO_SLUG_RULES.md
  NEXT_STEPS.md
```

The authoritative domain list currently lives outside this repository at:

```text
D:\Coding\vpn\site_creator\vpn_domain_list.json
```

Use each object's `domain` field to create or verify folders under `sites/`.
Do not copy the `source` field into site manifests unless future tooling
explicitly needs it.

## Site Data Model

Each site folder must contain:

- `manifest.json`, with an `items` array for post listing metadata.
- `posts/`, containing one JSON file per blog post.

New sites start with:

```json
{
  "items": []
}
```

Each post JSON file uses the public SEO slug as the filename:

```text
sites/<domain>/posts/<slug>.json
```

Each post object should include:

- `slug`: public URL slug and filename basename.
- `title`: post title.
- `excerpt`: short summary for listings.
- `publishedAt`: ISO timestamp.
- `updatedAt`: ISO timestamp.
- `contentHtml`: rendered post body HTML.

Whenever a post is added or changed, update both the post JSON file and the
site's `manifest.json` entry.

## Slugs

The `slug` field is the public URL slug. Keep it lowercase, ASCII-only,
hyphen-separated, short, and keyword-focused. Do not include timestamp prefixes,
random hashes, years, or punctuation in public slugs.

See `docs/SEO_SLUG_RULES.md` for the canonical rules.

## Workflow Notes

See `docs/NEXT_STEPS.md` before adding domains or generating new posts. The
short version:

1. Sync domains from the source domain list.
2. Generate post JSON files in the correct site folder.
3. Use the clean SEO slug as both `slug` and filename.
4. Add the matching manifest item.
5. Validate every JSON file and slug before handing off.
