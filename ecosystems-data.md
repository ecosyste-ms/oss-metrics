# ecosyste.ms data

ecosyste.ms publishes package and repository records, activity and funding indexes, and tools that parse supplied artifacts. The [main site](https://ecosyste.ms/) and [documentation](https://docs.ecosyste.ms/) list 25 services and applications, checked on 9 November 2026.

## Packages

| Service | Available data | Use in analysis |
| --- | --- | --- |
| [Packages](https://packages.ecosyste.ms/) | Registries, packages, versions, dependency declarations, dependent counts, downloads where supplied, maintainer records and source links. | Distribution and declared use across registries; release histories and membership in the Critical Open Source Packages collection. |
| [Repositories](https://repos.ecosyste.ms/) | Hosts, repository and owner metadata, archive status, activity timestamps, languages, stars, tags, manifests and dependency records. | Links packages to their source repositories and to the repositories that depend on them. |
| [Docker](https://docker.ecosyste.ms/) | Public image and version records, extracted packages, distributions, dependencies and SBOMs. | Evidence of components distributed together, including relationships across language and operating-system packages. |
| [Advisories](https://advisories.ecosyste.ms/) | Published vulnerability records and package associations; affected ranges and patched-version information where supplied. | Connects reported vulnerabilities to packages and versions. Advisory publication dates can differ from index dates and from the date a fix ships. |

Registry maintainer records list the accounts with publishing permission under each registry's model, and those accounts can differ from the commit authors and issue participants. The [Weekend at Bernie's](https://github.com/andrew/weekend-at-bernies) pipeline stores committers and publishers as separate roles because publishing a fix requires registry access in addition to commit rights, and some registries publish limited details about that access. It joins these services with the contribution and advisory records, and its reports include the classification signals and each source's sync date.

Several package records can link to the same repository, and container images can include copies distributed through other channels. Counts of those records include overlap; estimating distinct installations or people would require deduplication and evidence about deployment.

The [Critical Open Source Packages](https://packages.ecosyste.ms/critical) collection selects packages accounting for 80% of downloads or dependent repositories within their ecosystems. Its selection is based on concentration of use; security posture and maintainer availability come from the other services.

## Contributions

| Service | Available data | Use in analysis |
| --- | --- | --- |
| [Commits](https://commits.ecosyste.ms/) | Commit and committer metadata, totals, rolling activity, bot splits and contribution-distribution measures. | Records of development work and its distribution among identities. |
| [Issues](https://issues.ecosyste.ms/) | Issues and pull requests across supported forges; counts, closes, merges, timing, bot activity and maintainer-interaction summaries. | Counts and timing of demand and interaction, including work in addition to commits. |
| [Timeline](https://timeline.ecosyste.ms/) | Historical public GitHub events collected from GH Archive. | Event sequences and historical context, subject to the source's coverage gaps. |
| [Dependabot](https://dependabot.ecosyste.ms/) | Dependency-update pull requests, affected packages and merge outcomes. | Lists automated update proposals and records their outcomes. |

A rolling year of activity runs back from the source's observation date, which can differ from the analysis date. Coverage and refresh schedules vary between indexes. Known-bot filters remove declared bots, so the indexes count automation running under ordinary accounts as human activity and can count automated closes as maintainer responses.

## Funding

| Service | Available data | Use in analysis |
| --- | --- | --- |
| [Sponsors](https://sponsors.ecosyste.ms/) | Public GitHub Sponsors maintainers, funders and sponsorship relationships. | Sponsorship recorded through GitHub Sponsors, one public channel. |
| [Open Collective](https://docs.ecosyste.ms/docs/services/indexes/open-collective/) | Open Collective grants, donations and sponsorship data. | Public financial support recorded through Open Collective, with different coverage from GitHub Sponsors. |
| [Papers](https://papers.ecosyste.ms/) | Software mentions in scientific papers associated with package records. | Evidence of software appearing in research, separate from repository participation. |
| [Science](https://docs.ecosyste.ms/docs/services/experiments/science/) | Research-software projects, citation metadata, Software Heritage identifiers and archival observations. | Connects research references to software and preserved source. |
| [Awesome](https://awesome.ecosyste.ms/) | Curated lists and the projects referenced by them. | Discovery through list membership, chosen by each list's curators. |
| [Open Sustainable Technology](https://ost.ecosyste.ms/) | A curated collection of software for climate and environmental work, with categories and project metadata. | Groups projects by their use in climate and environmental work. |
| [Ruby](https://ruby.ecosyste.ms/) | Ruby projects and associated metadata. | Ruby project records in one index. |

The public funding records often omit salaries, consulting income and private grants, so the amount recorded through sponsorship services can be much smaller than the resources available to a project. Paper mentions are name matches and list entries are curator choices; establishing current deployment requires other evidence.

Science's artifact identifiers and archival work are written up in [Software Heritage Identifiers](https://nesbitt.io/2026/10/01/software-heritage-identifiers.html). Science and other experimental views also include classifications and rankings, and their selection rules set which projects appear.

## Tools

| Service | Output |
| --- | --- |
| [Dependency Parser](https://parser.ecosyste.ms/) | Dependency metadata extracted from supported manifest and lockfile formats. |
| [Dependency Resolver](https://resolve.ecosyste.ms/) | Resolved package dependency trees for supported ecosystems. |
| [SBOM Parser](https://sbom.ecosyste.ms/) | Parsed and converted SPDX and CycloneDX documents. |
| [License Parser](https://licenses.ecosyste.ms/) | Licence metadata matched in supplied software contents. |
| [Archives](https://archives.ecosyste.ms/) | Archive file listings and extracted file contents. |
| [Digest](https://digest.ecosyste.ms/) | Digests of supplied package artifacts. |
| [Diff](https://diff.ecosyste.ms/) | Differences between package releases. |
| [Summary](https://docs.ecosyste.ms/docs/services/tools/summary/) | An assembled overview of a supplied list of projects. |

Parser and inspection services process supplied files, so their coverage across the package indexes depends on which packages have been run through them. A resolved dependency tree changes with constraints and the target environment. An SBOM lists the components its producer included. Archive file listings can include bundled files that the dependency declarations omit, and identifying their origin requires further analysis. The License Parser returns licence text found in files; ownership and licensing rights may need separate review.

## Applications

[Dashboards](https://docs.ecosyste.ms/docs/services/products/dashboards/) groups project records under productivity, responsiveness, finance, engagement, adoption, dependencies, packages and security. People can create collections from a GitHub organisation, an Open Collective or an SBOM, and each collection is built from the same sources for its own project group.

[Funds](https://funds.ecosyste.ms/) allocates funding to selected projects based on dependency evidence and records contributions to the funds and the amounts distributed.

Service pages and documentation link to their APIs, which differ by dataset, and Issues also publishes bulk exports. The [licensing documentation](https://docs.ecosyste.ms/docs/usage/licences/) covers reuse and attribution, and the [rate limits](https://docs.ecosyste.ms/docs/usage/rate-limits/) page lists request limits for the APIs. The [glossary](https://docs.ecosyste.ms/docs/guides/glossary/) defines terms used across the services, such as ecosystem, registry, dependent package, transitive dependency and maintainer.

These records include a small share of private deployments and indirect end users. API requests include research and enrichment of other organisations' inventories, so a request count is a count of lookups, and some of those lookups are unrelated to adoption.
