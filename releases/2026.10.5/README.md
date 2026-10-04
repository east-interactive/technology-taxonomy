# Technology taxonomy 2026.10.5

This directory contains the immutable Queast Technology Taxonomy dataset release 2026.10.5.

- Full dataset: [taxonomy.json](taxonomy.json)
- Taxonomy only, without descriptions or editorial prose: [taxonomy-only.json](taxonomy-only.json)
- Taxonomy-only SHA-256: [taxonomy-only.json.sha256](taxonomy-only.json.sha256)
- SHA-256: [taxonomy.json.sha256](taxonomy.json.sha256) (`5a1fbe57fc872f9dd0eed37d647d5e7eab0bf18b3fdfbd9f15841591a741d89f`)
- Schema: [SCHEMA.md](SCHEMA.md) (1.2.1)
- Changes: [CHANGELOG.md](CHANGELOG.md)
- License: CC-BY-SA-4.0

Download the dataset and verify it before use:

```sh
curl -LO https://raw.githubusercontent.com/east-interactive/technology-taxonomy/v2026.10.5/releases/2026.10.5/taxonomy.json
curl -LO https://raw.githubusercontent.com/east-interactive/technology-taxonomy/v2026.10.5/releases/2026.10.5/taxonomy.json.sha256
shasum -a 256 -c taxonomy.json.sha256
```

Technology records use stable `canonical_id` values. Categories and domains are
separate hierarchical collections referenced by their stable IDs.
