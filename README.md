# Technology Taxonomy

**A free, reusable reference for software technologies.** Find consistent identities for languages, databases, frameworks, products, platforms, tools, standards, and more. Browse the relationships between them, resolve different names to stable IDs, or use the data in your own application, research, or AI agent.

The catalog is grounded in observed demand from European IT job advertisements and maintained through human review. It is a technology reference, not a ranking of market share or a claim to list every technology in existence. [Explore the public catalog](https://technologies.quea.st/technologies/) or [read the methodology](https://technologies.quea.st/methodology/).

[Browse the site](https://technologies.quea.st/) · [HTTP API](https://technologies.quea.st/api/) · [MCP for agents](https://technologies.quea.st/mcp/) · [JSON releases](https://technologies.quea.st/releases/) · [Contribution guidelines](https://technologies.quea.st/contribute/)

## What you can do with it

- **Match technologies across systems.** Search names and aliases, then store the immutable `canonical_id` instead of relying on a spelling or display name.
- **Explore context.** Use domains, categories, lifecycle status, and typed relationships to understand where a technology fits and how it connects to others.
- **Build on reviewed data.** Use a versioned, checksummed JSON snapshot for reproducible analysis, or query the selected public release through the free, rate-limited API and MCP interface.
- **Trace what you found.** Records include review dates and source links when available. Keep the release version and canonical ID with any result you cite or reuse.

Release **[2026.10.3](releases/2026.10.3/)** contains 1,556 technologies, 114 categories, 21 domains, and 1,127 typed relationships. These counts describe that release; later releases may differ.

## Get the data

| Access | Best for |
| --- | --- |
| [Website](https://technologies.quea.st/) | Browsing records, hierarchy, sources, and methodology. |
| [Versioned JSON](releases/2026.10.3/) | Local processing, reproducible datasets, and bulk integration. |
| [HTTP API](https://technologies.quea.st/api/) | Searching, resolving identities, and retrieving records or classifications on demand. Anonymous reads do not require an account. |
| [MCP](https://technologies.quea.st/mcp/) | Giving an agent structured access to the same published taxonomy through `POST /mcp`. |

Try a search through the public API:

```sh
curl --fail-with-body 'https://technologies.quea.st/api/v1/technologies?q=PostgreSQL&limit=25'
```

The [API guide](https://technologies.quea.st/api/) documents filters, pagination, domain and category endpoints, authentication, and current rate limits. The [MCP guide](https://technologies.quea.st/mcp/) covers connection setup and available tools. Both serve the site's selected public release, which may differ from the latest version in this repository; pin a JSON version when your work needs fixed dataset bytes.

### Download a release

Each version offers two views of the same identities. Choose [`taxonomy.json`](releases/2026.10.3/taxonomy.json) for the full approved dataset, including reviewed descriptions and available public metadata. Choose [`taxonomy-only.json`](releases/2026.10.3/taxonomy-only.json) for identities and structure without editorial prose. You do not need to combine them. Each has its own SHA-256 checksum.

```sh
curl -LO https://raw.githubusercontent.com/east-interactive/technology-taxonomy/v2026.10.3/releases/2026.10.3/taxonomy.json
curl -LO https://raw.githubusercontent.com/east-interactive/technology-taxonomy/v2026.10.3/releases/2026.10.3/taxonomy.json.sha256
shasum -a 256 -c taxonomy.json.sha256
```

Use the matching filenames to verify the taxonomy-only export. See the release's [schema](releases/2026.10.3/SCHEMA.md), [changes](releases/2026.10.3/CHANGELOG.md), and [GitHub tag](https://github.com/east-interactive/technology-taxonomy/releases/tag/v2026.10.3). Published versions and their checksums remain fixed; corrections appear in a later release.

## How the classification works

**Domains** are broad areas. **Categories** are narrower groupings within a domain and may have a parent category. A technology can reference domain IDs and category IDs; these are classification links, while typed technology relationships describe connections between records.

For example, release 2026.10.3 places **JavaScript** in the **Programming languages** category within the **Programming and development** domain:

```text
Programming and development (domain)
  └─ Programming languages (category)
       └─ JavaScript (technology)
```

Use `domain_ids` and `category_ids` on technology records, then join them to the top-level `domains` and `categories` collections by ID. A category's `domain_id` identifies its domain; `parent_id`, when present, identifies a parent category. The API also exposes [domains](https://technologies.quea.st/api/v1/domains) and [categories](https://technologies.quea.st/api/v1/categories) as complete lists. Filter `GET /api/v1/technologies` with `domain` or `category` IDs, not names or slugs. The separate `classification_kind` field describes the kind of record, such as a database or library.

Names and slugs may change; `canonical_id` is the stable technology identity. Preserve IDs and the dataset version in stored references. Consumers should tolerate unknown additive fields. See the [schema guide](releases/2026.10.3/SCHEMA.md) for more detail.

## Evidence, review, and contributions

New candidates must have at least **two distinct European IT job advertisements in the preceding 12 months**, found by searching names and aliases in ad titles and descriptions. Maintainers check relevance, identity, and supporting sources before adding a record. Corrections to existing records do not require two new advertisements. This demand evidence guides inclusion; it does not measure adoption or validate every product claim. The site's [methodology](https://technologies.quea.st/methodology/) explains inclusion, retention, source review, and the limits of job-ad coverage.

To suggest a new technology or correction, check the [contribution page](https://technologies.quea.st/contribute/) for the current intake status and submission route. Prepare the technology name, a concise reason, official or other relevant source links, and dated job-ad references when proposing a new entry. Public intake is being prepared; proposals enter human review when submissions are available and never publish directly.

Job-ad popularity and per-technology demand on the site are **separate live enrichment**, with their own coverage and freshness. They are not part of the immutable taxonomy release and should not be presented as general adoption or market share.

## License and stewardship

Release 2026.10.3 is licensed under [CC BY-SA 4.0](LICENSE). Follow its attribution and ShareAlike terms when sharing or adapting the data; the JSON records the release-specific license and attribution. Historical releases retain the terms recorded in their own artifacts.

The taxonomy is [maintained by Queast](https://quea.st/), but its public catalog, API, MCP interface, and dataset downloads are intended for anyone who needs a consistent software technology reference.
