# SEO Slug Rules

Public blog URLs use the post `slug` field. The slug must also match the post
JSON filename basename.

Example:

```text
sites/onsuvpn.com/posts/vpn-download.json
```

```json
{
  "slug": "vpn-download"
}
```

## Canonical Rules

1. Put the primary keyword at the beginning of the slug whenever possible.
2. Use lowercase letters only.
3. Separate words with hyphens only.
4. Remove low-value stop words unless they are required for meaning.
5. Keep slugs short, usually 2 to 5 words.
6. Do not include years, dates, list counts, timestamps, or random hashes.
7. Use URL-safe ASCII characters only: `a-z`, `0-9`, and `-`.

## Stop Word Guidance

Remove words that make the URL longer without improving search intent:

```text
a, an, the, in, on, at, to, for, and, but, or
```

Keep a word if removing it harms the keyword phrase or makes the slug awkward.
For example, `free-vpn-vs-paid-vpn` is acceptable because `vs` clarifies the
comparison intent.

## Migration Policy

Existing public slugs were migrated away from timestamped internal identifiers.
For old generated slugs:

1. Remove a leading 14-digit timestamp and hyphen.
2. Remove a trailing six-character hex hash.
3. Apply only clear stop-word cleanup.
4. Rename the post file to `<new-slug>.json`.
5. Update the matching `slug` in both the post file and `manifest.json`.

Examples:

```text
20260606031500-vpn-download-a8f3c2 -> vpn-download
20260606041000-free-vpn-beginner-guide-2c7e18 -> free-vpn-beginner-guide
20260606043000-vpn-latency-for-gaming-voice -> vpn-latency-gaming-voice
20260606045000-free-vpn-for-light-work -> free-vpn-light-work
```

## Validation Checklist

Before finishing a content update:

- The filename basename equals the post `slug`.
- The same `slug` appears in the site's `manifest.json`.
- The slug is lowercase ASCII and hyphen-separated.
- The slug has no timestamp prefix.
- The slug has no trailing random hash.
- The slug is short enough to read cleanly in search results.
