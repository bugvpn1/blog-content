# Manifest Schema

Each site folder contains a `manifest.json` file:

```json
{
  "items": []
}
```

`items` is an array of blog summaries. Each manifest entry must contain only these fields:

```json
{
  "slug": "example-slug",
  "title": "Post title",
  "excerpt": "Short public summary",
  "publishedAt": "2026-06-20T12:00:00.000Z",
  "updatedAt": "2026-06-20T12:00:00.000Z"
}
```

Required manifest entry fields:

- `slug`
- `title`
- `excerpt`
- `publishedAt`
- `updatedAt`

Do not include metadata, domain, keywords, competitor data, hash details, provider data, or content HTML in manifest entries.

Generated post files under `sites/<domain>/posts/<slug>.json` must contain only the same five fields plus `contentHtml`:

- `slug`
- `title`
- `excerpt`
- `publishedAt`
- `updatedAt`
- `contentHtml`

The n8n workflow is responsible for appending new manifest entries after creating each GitHub blog file.
