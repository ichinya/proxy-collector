# Proxy Collector

Extensible system for collecting, normalizing, enriching, and exporting proxy endpoints.

## Overview

Proxy Collector isolates each external source in a plugin, converts observations to the shared proxy contract, deduplicates them, and writes them through a storage adapter.
Status: foundation planning. Archived proxy_producer issues are being migrated into focused v2 source, file-import, enrichment, and export work.

## Architecture

~~~text
Source plugins
      |
      v
Normalizer -> deduplication -> optional enrichment
      |
      v
Storage adapter / export adapters
~~~

The shared message and API shapes are owned by [proxy-contracts](https://github.com/ichinya/proxy-contracts).

## Features

Planned capabilities:

- One source site per plugin module
- Canonical host, port, and protocol normalization
- PostgreSQL storage adapter
- Deterministic deduplication
- Country, ASN, and provider enrichment
- TXT, JSON, and CSV exports
- File-system import for operator-supplied proxy lists

## Installation

No runnable release is available yet. Clone the repository to review the specifications and follow the v0.1 issues for the initial implementation.

~~~shell
git clone https://github.com/ichinya/proxy-collector.git
cd proxy-collector
~~~

## Docker

A production container image is planned for v0.1 where applicable. Until an image and digest are published, there is no supported container invocation.

## Configuration

Source plugins and refresh intervals will use a versioned configuration file. Credentials, if a source requires them, must be injected as secrets and never committed.

## Environment variables

| Variable | Purpose |
| --- | --- |
| `DATABASE_URL` | PostgreSQL connection string |
| `SOURCE_CONFIG_PATH` | Path to source-plugin configuration |
| `EXPORT_DIR` | Directory for generated exports |
| `ENRICHMENT_ENABLED` | Enable optional enrichment |
| `LOG_LEVEL` | Structured log level |

Names and defaults are proposed and may change before v0.1. Never commit production secrets.

## Development

Target runtime: Python.

1. Choose an open roadmap issue and confirm its acceptance criteria.
2. Keep contracts and examples versioned; coordinate cross-repository changes explicitly.
3. Add tests for behavior changes and update documentation in the same pull request.
4. Run the repository-specific checks documented by the implementation once they exist.

See [CONTRIBUTING.md](CONTRIBUTING.md) for the common workflow and [SECURITY.md](SECURITY.md) for private vulnerability reporting.

## Roadmap

- **v0.1 Foundation:** repository structure, documentation, Docker/CI foundations, and base contracts.
- **v0.2 MVP:** collector -> scheduler -> MQ -> checker -> judge -> database -> site working cycle.
- **v1.0 Production:** multi-region judges, scoring, API, billing, monitoring, and high availability.

Track delivery in the [repository milestones](https://github.com/ichinya/proxy-collector/milestones) and [issues](https://github.com/ichinya/proxy-collector/issues).

## Related projects

- [proxy-contracts](https://github.com/ichinya/proxy-contracts)
- [proxy-scheduler](https://github.com/ichinya/proxy-scheduler)
- [proxy-stack](https://github.com/ichinya/proxy-stack)

## License

MIT License
