# Cohorts

Cohorts are groups of projects selected for comparison, proposed here for analysis across a whole ecosystem or several ecosystems, where the question is which shared infrastructure maintainers and funders should look at first across many applications. Assessing one application's dependencies is a separate task, described under Stakeholders in the [README](README.md). Members of each cohort have similar roles, distribution and development practices, so differences inside the group are more likely to come from the projects, with the measurement method roughly constant across members. The reasoning is in the README, and some ways to collect the evidence are in the [ecosyste.ms data map](ecosystems-data.md) and [git-pkgs tools](git-pkgs-tools.md); several cohorts here require additional sources.

A cohort definition should include its selection rule, its observation window, which registries and distribution channels were collected, and, for each member, which inputs are unknown and which were measured as zero. A project can belong to several cohorts, and membership is a description of the project. The cohorts overlap and select along five dimensions: package role, distribution channel, the people involved, lifecycle stage and evidence of use. Panels are a study design and are included separately.

## Critical packages

Most ecosystem-wide studies start from a list of critical packages: the [ecosyste.ms critical list](https://packages.ecosyste.ms/critical) contains the packages accounting for 80% of downloads or dependent repositories within each ecosystem, and the 2015 census authors started from Debian's popularity contest. A per-ecosystem threshold puts smaller ecosystems on the list, where a single global threshold would fill it mostly with packages from the largest registries.

Packages are added to these lists by observed usage, so any package missing from the usage records is also missing from the lists. Build tooling with few runtime dependents, native libraries used through distributions and wrappers, and research software with few dependents tend to fall below the threshold or are counted under a wrapper's name. Repackaged and multi-package projects appear several times: the May 2026 Weekend at Bernie's set had 8,606 packages from 5,874 repositories. Grouping the list by repository and checking it against the build tooling, native library and package manager infrastructure cohorts produces a list of projects that fall below a usage threshold.

A critical list taken on one date can be used as a panel if its membership is held fixed. For Weekend at Bernie's II the list was reselected in November, with 6,106 repositories against May's 5,874, so its membership changed between the two studies.

## Build tooling

This cohort contains compilers, transpilers, bundlers, minifiers, code generators, build backends, test frameworks, linters, formatters, CI actions and build plugins: sbt and Maven plugins, Babel and webpack plugins, Python build backends such as setuptools, hatchling and flit-core, and GitHub Actions. Usage counts for this cohort are low because development dependencies are mostly absent from downstream records. npm `devDependencies`, Maven `test` scope and Cargo `dev-dependencies` are skipped when another package depends on the library whose manifest lists them, so they are absent from consumers' lockfiles, resolved dependency graphs, most SBOMs and the dependent counts built on those. Their downloads come largely from CI and are hard to separate from mirrors and caches. A test framework can have a modest dependent count while running in the test suites of most packages in its ecosystem.

A compiler or bundler transforms the code in every artifact it produces, and a build plugin or CI action runs with access to source, caches and often publishing credentials. The xz backdoor was inserted through build scripts in release tarballs, and in March 2025 the compromised `tj-actions/changed-files` action ([CVE-2025-30066](https://www.cisa.gov/news-events/alerts/2025/03/18/supply-chain-compromise-third-party-github-action-cve-2025-30066)), used by over 23,000 repositories, printed CI secrets into public workflow logs. Measuring this cohort means counting the projects that declare a tool in their own development dependencies, build files and workflow `uses:` lines, then weighting by the reach of those projects' published packages. CI actions are described in more detail in [GitHub Actions is the weakest link](https://nesbitt.io/2026/04/28/github-actions-is-the-weakest-link.html).

## Leaf utilities

This cohort contains small packages with few dependencies of their own that appear deep in many dependency trees: argument parsing, terminal colours, string and path helpers, small date and format parsers. Josh Bressers found about half of npm packages above a million monthly downloads had one recorded maintainer, and many of them belong to this group. Since a sole maintainer is the normal case here, the useful comparisons are transitive reach, time since the last release, and whether a second account holds publishing rights.

## Native libraries

This cohort contains C and C++ libraries that users reach through system packages, vendored copies and language wrappers: zlib, libxml2, OpenSSL, curl, SQLite, libyaml. Registry download counters record a small share of their use (see the curl example in the README), and the dependents are recorded against their wrappers (nokogiri for libxml2, pg for libpq). In this cohort each library is grouped with its wrappers, the vendored copies found in package archives and its packages in Linux distributions, and the combined reach is attributed to the upstream project. The 2015 census sample was drawn from this population, and the census's highest-ranked rows proved the most accurate.

## Runtimes

This cohort contains language runtimes, their standard libraries and the C libraries beneath them: CPython, OpenJDK, Node.js, Ruby, the Go toolchain, glibc and musl. Nearly every package in an ecosystem runs on its runtime, and few declare it beyond a version constraint such as `requires-python` or an `engines` field. Runtimes are distributed to users through installers, version managers, container base images and operating-system packages, and many have foundation or company staff working alongside volunteers, so their staffing differs from most other cohorts. A vulnerability in a standard library module ships in every installation of the affected runtime versions, and fixing it requires users to upgrade the runtime itself.

## Vendored code

Copies of upstream code shipped inside other artifacts: shaded JARs in Java and Scala builds, bundled and minified JavaScript, statically linked Go and Rust binaries, C sources copied into a project tree, and libraries compiled into firmware. The copies are absent from both registry dependency graphs, which record the package containing the copy, and advisory databases, which list the upstream package. Finding them takes artifact inspection: file hashes, symbol tables, embedded version strings, licence headers, Go and Rust build metadata, and SBOMs generated from the built artifact. Grouping each upstream project with its known copies gives a count of the places a fix has to reach, and comparing the version embedded in each copy with upstream releases measures how far the copy lags.

## Repackaged projects

One project distributed through several registries or channels: Scala and Java libraries from Maven Central bundled into PyPI wheels or npm packages, Go and Rust binaries packaged as Python wheels, and libraries rebuilt for Homebrew, Nix, conda-forge and Debian. Counting each registry entry separately multiplies the maintainers and splits the usage, so entries in this cohort are grouped by source repository, or by the Software Heritage identifier of the released contents, into one entry per project. Usage is recorded per channel alongside any total, since each channel's download counter records a different event and the same installation can be recorded twice. A repository can hold more than one project, so grouping by repository needs checking against each package's own metadata. The same grouping produces a list of every channel where a fixed release has to be published after an advisory, since advisory authors often list the original package and leave out the repackaged ones.

## Maintainer portfolios

This cohort contains every package a person or account can publish, across registries. Package-level metrics count one maintainer with publishing rights to two hundred packages as two hundred separate single-maintainer projects, although one burnout, account compromise or departure affects all of them. Identity resolution across registries and forges (mailmap files, linked accounts, shared email addresses) is the main difficulty. The results are personal data, so aggregate figures are safer to publish than named lists.

## Multi-package projects

Monorepos and projects that publish many packages from one repository, such as Babel, the AWS SDKs and ZIO. Package-level counting records each of these projects many times, and their graph centrality varies with how finely their maintainers split them into packages. Grouping packages by repository and governance before comparison counts a project with 150 packages as one project.

## Formats and protocols

This cohort contains implementations of shared formats and protocols across ecosystems: YAML, XML, TOML, protobuf, HTTP/2, image and compression formats. Most ecosystems have their own implementation of each, and a vulnerability class or specification change can affect all of them at once. A comparison of implementations of one format across ecosystems puts single-maintainer parsers of untrusted input in one group and implementations with fuzzing and several maintainers in another. [Whale Fall](https://nesbitt.io/2026/02/21/whale-fall.html) describes formats still in use after their original projects were archived or abandoned, so this cohort also includes implementations whose original project has ended.

## Package manager infrastructure

This cohort contains clients, resolvers, registry software, lockfile parsers, index formats, and signing and mirroring tools. Every package in an ecosystem passes through them, so a failure in one affects installs across the whole ecosystem, but few packages declare them as dependencies, because people run them as tools. Their maintainers are often a small group of volunteers or one company's staff.

## Deployed software

This cohort contains applications and services that people run as programs: PostgreSQL, Redis, nginx, Kubernetes and operating-system utilities. Few packages declare a database server or web server as a dependency, so dependency graphs contain few records of them. Evidence of use comes from distribution packages and popularity contests such as Debian's, container image pulls and base-image contents, Helm charts and infrastructure configuration that reference them, and opt-in telemetry where a project collects it. Redis, Elasticsearch and Terraform changed licence between 2021 and 2024, so this cohort overlaps with succession and forks.

## Host extensions

This cohort contains plugins and extensions distributed to users through a host application: WordPress plugins, browser extensions, editor extensions on the VS Code Marketplace and Open VSX, and Jenkins plugins. These run inside an application on users' machines or servers, so build plugins are in the build tooling cohort instead. Their reach depends on the host's install base and the permissions the host's API gives them, often access to every page a user visits or every file in a workspace. The host's marketplace publishes install counts, and the marketplace operator sets its review, signing and takedown rules. When one person sells an extension they maintain, the new owner can push an update to every installation, as happened with The Great Suspender, sold in June 2020 with over two million installs and removed from the Chrome Web Store as malware in February 2021.

## Finished projects

This cohort contains projects whose maintainers consider them done, or whose rate of change has dropped because the problem is solved: small algorithms, parsers for frozen specifications, mature utilities. Their activity scores are similar to those of abandoned projects; TeX and bzip2 are the examples in [The Mismeasure of Open Source](https://nesbitt.io/2026/05/09/the-mismeasure-of-open-source.html) of software whose maintainers deliberately change it little because its format is stable. Splitting them by observed responsiveness when issues do arrive (the method behind the `active`, `dormant` and `unknown` categories in [Weekend at Bernie's](https://nesbitt.io/2026/05/08/weekend-at-bernies.html)) and by any declared status such as Contributing.yaml's `done` puts low-activity projects whose maintainers still answer issues in the maintained group.

Membership is based on one of three kinds of evidence, recorded separately: a maintainer's declaration that the project is complete, observed stability where issues still get answers and reports still lead to releases, or low change where responsiveness is untested. The first two support calling a project finished, and the third belongs with `unknown`.

## Succession and forks

Projects that were archived, transferred, renamed, forked or replaced, grouped with their successors. In Weekend at Bernie's II, apparently unpatched advisories were traced to fixes published under successor package names, so researchers who followed only the original package would record those vulnerabilities as open when fixes existed. Relicensing forks are part of this cohort: Dawn Foster compared OpenSearch, Valkey and OpenTofu with the projects they forked from and found more organisational diversity in the forks. Linking each package to its predecessor and successor, through deprecation notices, registry redirects, README notes and forge transfer records, allows researchers to track maintenance work across renames, transfers and forks. The mechanisms are listed in [How Open Source Projects Change Hands](https://nesbitt.io/2026/06/16/how-open-source-projects-change-hands.html), and the downstream effects are described in [Whale Fall](https://nesbitt.io/2026/02/21/whale-fall.html).

## Research software

This cohort contains software cited in papers, often published through general registries, with few dependents, and used in published results. Use outside dependency graphs is recorded in citations and paper mentions, and research software often depends on scientific libraries maintained by academics on fixed-term grants. Members of this cohort are selected from OpenAlex and Software Heritage records and joined to package records through identifiers cited in the paper or the software's metadata, such as a DOI, a SWHID or a repository URL; a matching name alone is weak evidence that a package is the software a paper used.

## Panels

A panel is a fixed list of projects followed over time, such as the 2015 census list or the May 2026 Weekend at Bernie's set. With a panel, the outcome for specific projects can be counted: how many were funded, forked, handed over or archived. In a rolling selection such as the current top 1% by downloads, measured changes combine project changes with turnover in membership. When panel membership is published, later researchers can measure the same projects.

## Intersections

Membership in several cohorts at once is evidence of specific risks: build tooling maintained by one person whose output ships in most of an ecosystem's artifacts is in the build tooling, leaf utilities and maintainer portfolio cohorts at once. libxml2 and nokogiri were in this position before libxml2's maintainer stepped down in 2025: libxml2 was in both the native libraries and formats cohorts, had a widely used wrapper in nokogiri, and had one upstream maintainer.
