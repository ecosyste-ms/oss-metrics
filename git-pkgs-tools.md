# git-pkgs tools

[git-pkgs](https://git-pkgs.dev/) is a set of command-line tools and Go libraries that read evidence from Git repositories, manifests, lockfiles and package archives. Most of them run locally against a checkout, so they work the same way on any forge and make no API calls that count against rate limits. They mostly produce intrinsic metadata: what a repository or artifact contains at a given commit, and when that changed. The released tools, checked on 9 November 2026, are listed here; the [GitHub organisation](https://github.com/git-pkgs) also contains experiments that are left out.

## Dependency history

The [`git-pkgs`](https://github.com/git-pkgs/git-pkgs) subcommand indexes manifests and lockfiles across a repository's history into a database inside `.git`, and one history can include many ecosystems. Lockfiles produce the most complete results, since they record transitive dependencies and the versions actually installed. Full documentation is in the [command reference](https://git-pkgs.dev/docs/reference/).

| Command | Output | Use in analysis |
| --- | --- | --- |
| `list`, `tree`, `where`, `why` | Current dependencies, the dependency tree, the file and line where a package is declared, and the commit and message that added it. | The dependency set of one application at a given commit. |
| `history`, `log`, `blame`, `diff` | When each dependency was added, changed or removed, by whom, and the differences between two commits. | Adoption and removal of packages over time within a project. |
| `stale`, `stats` | Lockfile dependencies ordered by time since last change; aggregate counts of dependencies and changes. | How often a project's dependency versions change. |
| `integrity` | Lockfile integrity hashes, with drift where one version has different hashes across manifests. | Consistency of resolved artifacts across a repository. |

These commands read Git history only and run offline, while the commands in this table fetch external data for the dependencies found:

| Command | Source | Output |
| --- | --- | --- |
| `vulns` | [OSV](https://osv.dev) | Known vulnerabilities in current dependencies, with subcommands for exposure time since the vulnerable version was added, the commits that introduced or fixed each one, and a package's vulnerability history across commits. |
| `outdated`, `freshness` | ecosyste.ms | Dependencies with newer releases, and how many days installed versions lag behind the latest. |
| `maintainers`, `funding`, `licenses` | ecosyste.ms | Maintainer counts, funding links and declared licences for each dependency. |
| `health` | ecosyste.ms | A maintenance score per dependency, starting at 100 and reduced for small or missing maintainer records, few or missing dependents, and missing download data, with the contributing signals listed. |
| `deprecated`, `provenance` | Package registries | Deprecation flags, and registry provenance and trusted-publishing metadata. |
| `changelog` | Upstream repositories | Changelog entries between two versions of a dependency. |

A history index covers one repository, so running it across many repositories gives a sample of how those projects use their dependencies, limited to the repositories someone chose to clone.

## Repository history scanners

| Tool | Output | Use in analysis |
| --- | --- | --- |
| [signals](https://github.com/git-pkgs/signals) | Security-relevant evidence stored in Git, such as security policies, CI configuration, pinned or unpinned actions, workflow token permissions, update bot configuration, licensing coverage and commit signing, with the commit and path for each change. With date bounds, it reports the state before and after an event such as a grant. | A timeline of repository-contained practices. It covers many OpenSSF Scorecard checks using the local clone alone. |
| [git-spdx](https://github.com/git-pkgs/git-spdx) | Detected licence expressions and `SPDX-License-Identifier` declarations across history, with the commit and path behind each change. | When a project's licensing changed, for relicensing studies or compliance history. |
| [secrets](https://github.com/git-pkgs/secrets) | Leaked credentials across history, using the Betterleaks rule corpus, attributed to commits and paths. | Whether and when credentials entered and left a repository. |

Git stores deleted configuration and earlier licensing, along with the commit that introduced or removed each file-backed practice. Branch protection, webhooks and issue activity are stored on the hosting service, as are CI results and release assets, so these scanners need to be paired with forge or registry data for those. Review patterns in commit metadata are a proxy and can differ from what happened in a pull request.

## Metadata files and identities

| Tool | Output | Use in analysis |
| --- | --- | --- |
| [codemeta](https://github.com/git-pkgs/codemeta) | Parsed and validated `codemeta.json` software metadata. | Self-declared authorship, funding and related metadata, common in research software. |
| [citation](https://github.com/git-pkgs/citation) | Parsed and validated `CITATION.cff` files. | The citation format recorded in a project, and its listed authors. |
| [bibtex](https://github.com/git-pkgs/bibtex) | BibTeX entries from `.bib` files and from READMEs, with author lists split by BibTeX's name rules. | Citation metadata in projects that use `.bib` files or README entries in place of a `CITATION.cff`. |
| [mailmap](https://github.com/git-pkgs/mailmap) | Canonical author identities resolved through Git `.mailmap` files. | Merging duplicate identities before counting contributors. |
| [provides](https://github.com/git-pkgs/provides) | Mappings from a package identity to the module, package or namespace names found for it in source code, with the evidence behind each mapping. | Matching imports in code to the packages that supply them, where the names differ. |
| [purl2swhid](https://github.com/git-pkgs/purl2swhid) | A Software Heritage identifier computed from a package archive's unpacked contents, with optional checks for whether it is archived and requests to preserve it. | Linking package releases to preserved source. |

The parsers return a file's contents as of its last edit, so the file's commit date is part of the observation.

## Repository description

| Tool | Output | Use in analysis |
| --- | --- | --- |
| [brief](https://github.com/git-pkgs/brief) | A structured report of a project's languages, package managers and build tools, plus its test runners, linters and formatters, with no score attached. | Grouping projects by toolchain, or checking which practices a cohort has in place. |
| [roles](https://github.com/git-pkgs/roles) | Paths classified from their names alone as source, tests, fixtures, vendored code, generated files and other roles. | Excluding vendored and generated code before counting or scanning. |
| [languages](https://github.com/git-pkgs/languages) | Candidate languages for a file from its name and contents, with confidence and conflicting evidence. | Language breakdowns based on file contents as well as file extensions. |

## Libraries

The [Go modules](https://git-pkgs.dev/docs/modules/) behind the CLI, listed here, can be imported on their own to build other tools:

| Module | Purpose |
| --- | --- |
| [manifests](https://github.com/git-pkgs/manifests) | Parses manifest and lockfile formats to extract dependency information. |
| [resolve](https://github.com/git-pkgs/resolve) | Parses package manager CLI output (such as `npm ls --json` or `go mod graph`) into dependency trees with PURLs. |
| [managers](https://github.com/git-pkgs/managers) | Wraps package manager CLIs behind a common interface. |
| [sbom](https://github.com/git-pkgs/sbom) | Reads and writes CycloneDX and SPDX documents. |
| [registries](https://github.com/git-pkgs/registries) | Fetches package metadata from registry APIs. |
| [enrichment](https://github.com/git-pkgs/enrichment) | Combines registry and ecosyste.ms lookups in one interface. |
| [vulns](https://github.com/git-pkgs/vulns) | Queries OSV, NVD and GitHub Advisories with PURL-based lookups. |
| [forge](https://github.com/git-pkgs/forge) | Fetches repository metadata from GitHub, GitLab, Gitea and Forgejo, and Bitbucket Cloud. |
| [licenses](https://github.com/git-pkgs/licenses) | Matches licence text and scans repositories against ScanCode's rule corpus. |
| [reuse](https://github.com/git-pkgs/reuse) | Extracts licence and copyright information from REUSE-compliant projects. |
| [spdx](https://github.com/git-pkgs/spdx) | Parses, normalises and validates SPDX licence expressions. |
| [changelog](https://github.com/git-pkgs/changelog) | Parses changelog files into structured entries. |
| [purl](https://github.com/git-pkgs/purl) | Parses and generates Package URLs. |
| [vers](https://github.com/git-pkgs/vers) | Parses and compares version ranges across ecosystem syntaxes. |
| [platforms](https://github.com/git-pkgs/platforms) | Translates platform identifiers between package ecosystems. |
| [pom](https://github.com/git-pkgs/pom) | Resolves effective Maven POMs in pure Go, with no JVM. |
| [archives](https://github.com/git-pkgs/archives) | Reads archive files and lists their contents in memory. |
| [attestation](https://github.com/git-pkgs/attestation) and [sigstore](https://github.com/git-pkgs/sigstore) | Parse SLSA provenance and verify Sigstore bundles. |
| [cooldown](https://github.com/git-pkgs/cooldown) | Filters package versions by publish age. |

A dependency tree from `resolve` depends on the environment where the package manager ran, and lockfile parsing in `manifests` is limited to its supported formats. Both can miss packages pulled in by build scripts, as well as vendored copies and system libraries.
