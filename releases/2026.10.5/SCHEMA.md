# Taxonomy JSON schema 1.2.1

The release file is one JSON object with these top-level fields:

| Field | Type | Meaning |
| --- | --- | --- |
| `schema_version` | string | Dataset schema version. |
| `taxonomy_version` | string | Immutable calendar release version. |
| `generated_at` | RFC 3339 timestamp | Exact dataset generation time. |
| `license` | string | Dataset license (`CC-BY-SA-4.0`). |
| `attribution` | string | Optional maintainer attribution. |
| `changelog` | string[] | Reviewed release changes. |
| `technologies` | object[] | Technology records, ordered by stable `canonical_id`. |
| `relationships` | object[] | Typed edges using `source_id` and `target_id`. |
| `categories` | object[] | Hierarchical categories. `parent_id` points to another category and `domain_id` points to a domain. |
| `domains` | object[] | Top-level classification domains; `parent_id` may express domain hierarchy. |

Each technology has `canonical_id`, `name` and `slug`. Optional
fields include description, aliases, classification IDs, lifecycle, relationships,
official URLs, organizations, licensing, deployment options, reviewed claims and
their public source URLs. Consumers should ignore unknown additive fields and use
stable IDs, not names or array positions, as identity.

## Taxonomy-only projection

`taxonomy-only.json` uses the same schema with only identity and structure:
canonical IDs, names, slugs, aliases, classification kind, lifecycle, replacement
IDs, revision timestamps, external IDs, historical slugs, category/domain IDs,
relationships, and category/domain hierarchy. Descriptions, explanations, evidence,
URLs, product information and descriptive claims are omitted. Release metadata is
preserved. Its separate checksum covers the derived bytes; the full dataset remains
unchanged. This projection is for reuse, not an approval envelope or import artifact.
