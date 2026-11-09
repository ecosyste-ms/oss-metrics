# References

Most of the arguments in the [README](README.md) come from Andrew Nesbitt's posts, with definitions and supporting data from the other sources listed here.

## Maintenance

- [Weekend at Bernie's](https://nesbitt.io/2026/05/08/weekend-at-bernies.html), 8 May 2026. Classifies repositories behind widely used packages using development and interaction records, with a separate category for repositories where responsiveness had not been tested.
- [Weekend at Bernie's II](https://nesbitt.io/2026/11/06/weekend-at-bernies-ii.html), 6 November 2026. Follows changes in those classifications, including returning maintainers who disclosed AI assistance. Its advisory investigation traces publication delays and fixes missing from package-level records.
- [CHAOSS Metrics in 2026](https://nesbitt.io/2026/05/27/chaoss-metrics-in-2026.html), 27 May 2026. Examines how generated activity affects the interpretation of common measurements, including response times and contributor counts.
- [Weekend at Bernie's analysis code](https://github.com/andrew/weekend-at-bernies). Contains the package selection, collectors and reports, with the classifier rule and signals recorded for each result.
- [A year of AI disclosure in critical packages](https://nesbitt.io/2026/08/06/a-year-of-ai-disclosure-in-critical-packages.html), 6 August 2026. Counts only explicit disclosure markers and compares results across samples and detection rules.
- [Dumb Ways for an Open Source Project to Die](https://nesbitt.io/2026/05/19/dumb-ways-for-an-open-source-project-to-die.html), 19 May 2026. Catalogues how projects end up unmaintained, including causes that produce identical registry and repository records.
- [How Open Source Projects Change Hands](https://nesbitt.io/2026/06/16/how-open-source-projects-change-hands.html), 16 June 2026. Lists the mechanisms for passing on maintainership and who can trigger each one.
- [Contributing.yaml](https://www.tc54.org/contributing-yaml/), Ecma TC54-TG4 with OWASP, in development, with [draft examples](https://github.com/Ecma-TC54/ECMA-xxx-CONTRIBUTING/tree/develop/examples). A machine-readable file for a project's support levels, calls for help and status, with states such as unreachable, done and up for adoption, plus a taxonomy of non-funding support. Under the draft, an ecosystem host can file a status claim as well as the maintainer. Like [CodeMeta](https://codemeta.github.io/) and [publiccode.yml](https://yml.publiccode.tools/), it is useful only once widely adopted, and a self-declared file records the project's state on the day it was last edited; a maintainer who disappears leaves their last claim in the file, so abandonment is recorded only when a third party files a claim.
- [Whale Fall](https://nesbitt.io/2026/02/21/whale-fall.html), 21 February 2026. Follows what happens downstream when the maintainers of a large project stop work: forks, successive recolonisation, and formats and interfaces that other software implements after the project ends.
- [The New Dynamics of Open Source: Relicensing, Forks, & Community Impact](https://arxiv.org/abs/2411.04739), Dawn Foster, November 2024. Compares organisational affiliation in Elasticsearch and OpenSearch, Redis and Valkey, and Terraform and OpenTofu, and finds more organisational diversity in the forks, especially those hosted by a neutral foundation.
- [Open Source Governance Practices: A Path to Improving Sustainability](https://doi.org/10.1109/MC.2026.3667269), Dawn Foster, *IEEE Computer* 59(6), June 2026. Links governance to contributor sustainability through recruitment, retention and maintainer burnout, with practical advice for projects.

## Scores

- [Revisiting the 2015 Open Source Census](https://nesbitt.io/2026/05/06/revisiting-the-2015-open-source-census.html), 6 May 2026. Rereads the Core Infrastructure Initiative's ranked list of 428 projects ten years on: which top-ranked projects went on to have the problems their scores pointed to, why xz came out at row 254, and which projects were excluded from the candidate set before scoring.
- [Core Infrastructure Initiative census](https://github.com/ossf/census). The original 2015 data, scoring formula and reviewer comments.
- [From Data to Action: Building Healthy and Sustainable Open Source Projects](https://doi.org/10.1109/mc.2025.3530556), Dawn Foster, *IEEE Computer* 58(6), June 2025. Advice and resources for using metrics to improve project health and sustainability before problems become a crisis.
- [Practitioner Guide: Assessing Viability](https://www.chaoss.community/practitioner-guide-viability/), CHAOSS, Gary White, Dawn Foster and Matt Germonprez. Written for organisations consuming open source, it covers how to assess the viability and risk of dependencies across compliance and security, governance, community and strategy.
- [The Mismeasure of Open Source](https://nesbitt.io/2026/05/09/the-mismeasure-of-open-source.html), 9 May 2026. Shows how gaps in the data and selection filters lower the scores of projects whose practices the data sources omit.
- [Centrality is not vitality](https://nesbitt.io/2026/05/14/centrality-is-not-vitality.html), 14 May 2026. Questions what PageRank on a dependency graph measures and how packaging conventions affect comparisons between registries.
- [How much should you trust your OSS data?](https://nesbitt.io/2026/09/04/how-much-should-you-trust-your-oss-data.html), Sophia Vargas and Andrew Nesbitt, 4 September 2026. Documents changes in GH Archive coverage and their effect on every dataset built on it, and the difficulties of joining sources with inconsistent identifiers.

## Packages

- [The Roles of Packages](https://nesbitt.io/2026/03/29/the-roles-of-packages.html), 29 March 2026. Sorts packages by role (applications, libraries, plugins, wrappers, build tools) across language and system package managers.
- [A Taxonomy for Open Source Software](https://nesbitt.io/2025/11/29/oss-taxonomy.html), 29 November 2025, and the [OSS Taxonomy](https://github.com/ecosyste-ms/oss-taxonomy) repository. A faceted classification for open source projects, so one project can be described along several dimensions at once.
- [Wheels, Bottles and Images](https://nesbitt.io/2026/07/30/wheels-bottles-images.html), 30 July 2026. Compares the three main self-service binary distribution systems, including software repackaged into registries outside its own language.
- [Plumbing Homebrew into the vulnerability ecosystem](https://nesbitt.io/2026/07/17/plumbing-homebrew-into-the-vulnerability-ecosystem.html), 17 July 2026. Describes the data the Homebrew maintainers had to publish so that advisory tooling could match vulnerabilities to Homebrew packages.

## Contributors

- [Open Source is one person](https://opensourcesecurity.io/2025/08-oss-one-person/), Josh Bressers, 28 August 2025. Uses ecosyste.ms data to show how common single-maintainer packages are, even among the most downloaded npm packages.
- [Exploring Unseen Open Source Infrastructure](https://nesbitt.io/2017/02/24/exploring-unseen-open-source-infrastructure.html), 24 February 2017. Identifies widely depended-on libraries with few stars or other signs of GitHub attention.
- [Making 24 Pull Requests more inclusive for 2018](https://nesbitt.io/2018/11/29/making-24-pull-requests-more-inclusive-for-2018.html), 29 November 2018. Documents contributions beyond code and pull requests, such as support, mentoring, event organising and governance work.
- [How I Assess Open Source Libraries](https://nesbitt.io/2025/12/15/how-i-assess-open-source-libraries.html), 15 December 2025. Sets out Andrew's preferences when choosing dependencies, including adoption and test quality, and how quickly maintainers respond.
- [Unfinished Work in Package Security](https://nesbitt.io/2026/09/22/unfinished-work-in-package-security.html), 22 September 2026. Follows the work required to get a security report through to a released repair, including access to publishing credentials and downstream distribution.
- [Respectful Open Source](https://nesbitt.io/2026/02/13/respectful-open-source.html), 13 February 2026. Considers the review and triage work that inbound contributions add for maintainers who are already overloaded.
- [Open Source vs the Invisible Hand](https://nesbitt.io/2026/06/18/open-source-vs-the-invisible-hand.html), 18 June 2026. Sets open source production, with a median producer headcount of one, against standard market assumptions.
- [Taking Roads and Bridges literally](https://nesbitt.io/2026/06/30/taking-roads-and-bridges-literally.html), 30 June 2026. Compares how physical infrastructure is maintained with the critical-infrastructure framing governments now apply to open source.
- [A Toolkit for Measuring the Impacts of Public Funding on Open Source Software Development](https://arxiv.org/abs/2411.06027), Cailean Osborne, Paul Sharratt, Dawn Foster and Mirko Boehm, November 2024. A method for evaluating public funding programmes using CHAOSS health metrics, with a taxonomy of social, economic and technological impacts.

## Definitions

- [Package Manager Glossary](https://nesbitt.io/2026/01/13/package-manager-glossary.html), 13 January 2026. Defines common package management terms and notes where their meaning differs between ecosystems; an ecosystem is defined by its package format, so the Maven ecosystem includes Java, Kotlin, Scala and Clojure.
- [What does Open Source mean?](https://nesbitt.io/2026/04/04/what-does-open-source-mean.html), 4 April 2026. Separates the meanings people attach to "open source", which often differ between participants in the same discussion.
- [Documenting Package Manager Data](https://nesbitt.io/2025/11/30/documenting-package-manager-data.html), 30 November 2025. Describes documentation of 70+ registries and clients with the CHAOSS Package Metadata Working Group and Alpha-Omega.
- [Software Heritage Identifiers](https://nesbitt.io/2026/10/01/software-heritage-identifiers.html), 1 October 2026. Covers tools connecting package identities to preserved source and their use in archiving research software.
- [Software Heritage glossary](https://docs.softwareheritage.org/devel/glossary.html). Glossary entries for intrinsic and extrinsic metadata and for content-derived identifiers.
- [CHAOSS Time to First Response](https://www.chaoss.community/kb/metric-time-to-first-response/). Defines the timing measure, with automated responses excluded from measurements of human interaction.
- [CHAOSS Bot Activity](https://www.chaoss.community/kb/metric-bot-activity/). Defines a measure of automated activity, with filters for examining it.
