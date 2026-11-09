# Open source metrics

Open source metrics are most reusable as shared observations, each recorded with its source, collection date and coverage, and with missing data marked as unknown. Classifications, scores and rankings built on those observations depend on who is asking and why, so each stakeholder can apply their own criteria to the same records. Three layers are kept apart here: measurements, what was observed; interpretations, what those observations are taken to mean; and decisions, how a particular stakeholder acts on them. Tests, contributor counts and download totals measure different parts of a project: a library can be in use for years with few code changes, while users can file more requests in a busy issue tracker than its maintainers have hours to answer.

The main sources are the two *Weekend at Bernie's* studies, *CHAOSS Metrics in 2026* and a reading of the 2015 Core Infrastructure Initiative census. The other files in this repository are:

- [cohorts.md](cohorts.md), proposed groupings of projects for ecosystem-wide analysis
- [references.md](references.md), the supporting posts, papers and definitions
- [ecosystems-data.md](ecosystems-data.md), the data available from ecosyste.ms, one of several sources for this kind of analysis
- [git-pkgs-tools.md](git-pkgs-tools.md), git-pkgs tools for extracting evidence from repositories and artifacts

## Stakeholders

Each group judging open source projects brings its own rubric for sorting and grouping them. A team assessing its application's dependencies cares about the few hundred packages in its lockfile: which have open advisories, whose maintainers respond, and how hard each would be to replace. For the Scala Center, taking a broad view of the Scala ecosystem, the unit is every Scala library on Maven Central and beyond, with questions about where shared infrastructure is thin and where funding or engineering time would help most. Alpha-Omega, working to improve the security of open source as a whole, looks for the projects where a single intervention reaches the most downstream users. The same package can rank highly under one rubric and fall outside another's selection entirely. All three can use the same shared records if each applies its own grouping and weighting.

## Subjects

Code inspection can establish which dependencies a release contains or whether a test covers a known failure, and governance and publishing records list who can make changes or ship a release. A maintainer's capacity to respond depends on the time they can provide, often unpaid; response time alone is weak evidence of code quality or the care taken over a review.

Publishing rights and source access often belong to different people: Debian, Fedora, Homebrew and other distributions patch and ship projects through packagers outside the upstream committer list, so a fix can reach users through a distribution before upstream has one, and a distribution's patches can diverge from upstream for years. Registry accounts tied to an email address on an expired domain can be taken over by whoever re-registers the domain and resets the password, and handing a dormant package to a new owner, as happened with event-stream in 2018, changes who can publish to every downstream user.

People who call a project "healthy" may be expecting somebody to answer support requests. An organisation requiring incident response places a different demand on a maintainer from a person using a stable utility occasionally. The support available needs to be agreed with the people providing it. [How I Assess Open Source Libraries](https://nesbitt.io/2025/12/15/how-i-assess-open-source-libraries.html) covers commit frequency and responsiveness as separate measures, while [Unfinished Work in Package Security](https://nesbitt.io/2026/09/22/unfinished-work-in-package-security.html) describes the work and funding needed to turn reports into released fixes.

In [Open Source is one person](https://opensourcesecurity.io/2025/08-oss-one-person/), Josh Bressers reported about seven million packages with one recorded maintainer in an ecosyste.ms dataset of 11.8 million, with counts unknown for roughly four million. About half of the roughly 13,000 npm packages exceeding one million monthly downloads also had one recorded maintainer, so single maintainers are common among widely used dependencies. Large paid teams are a distinct group, especially when the comparison includes small libraries further down a dependency tree. Registry counts record accounts, so employment and available hours need other sources.

## Community

Contributors do work on a project, including documentation, translation, support and organisation as well as code, and the community is everyone using it, directly or through other software. Many users interact with a project only by installing it, and many see their indirect dependencies only as entries in a lockfile.

Repository activity covers visible contributions and dependency declarations cover use by other software; downloads count distribution activity, including automated traffic, on registries that publish a counter. A project-health dashboard in 2026 listed curl at 10,467 downloads for the year, an accurate count of the instrumented channels for software shipped with every Linux distribution and vendored widely. These records cover different populations: a desktop application's users may leave few traces in the places used to measure a library. [Exploring Unseen Open Source Infrastructure](https://nesbitt.io/2017/02/24/exploring-unseen-open-source-infrastructure.html) describes widely depended-on libraries with little GitHub attention. Contribution counters also exclude work done away from pull requests, as [Making 24 Pull Requests more inclusive for 2018](https://nesbitt.io/2018/11/29/making-24-pull-requests-more-inclusive-for-2018.html) documents. A sole maintainer can support software used by a very large population, and growth in that population increases support requests against the same number of maintainer hours.

## Metadata

Intrinsic metadata ships with a particular source revision or artifact (a manifest's dependency declarations, a licence file, or citation information committed with the source), whereas registry download counts, issue discussions, sponsorship records, advisory publications and references in papers are extrinsic and collected from other sources. This follows the distinction in the [Software Heritage glossary](https://docs.softwareheritage.org/devel/glossary.html).

The same field may appear in both places, such as a description in a manifest and one returned by a registry API, and either copy can be wrong. Retaining the source and observation date helps explain disagreements between them.

Proposed self-declared files such as [Contributing.yaml](https://www.tc54.org/contributing-yaml/), [CodeMeta](https://codemeta.github.io/) and [publiccode.yml](https://yml.publiccode.tools/) would add intrinsic statements about support, funding needs and project status. Their value depends on widespread adoption and on maintainers editing them as circumstances change. A maintainer who disappears leaves their last claim in the file, and abandonment is the main case these assessments are used to detect. Observations here come from records that already exist across most projects (releases, commits, issue responses, dependency declarations and registry metadata), and a declared status counts as one more dated observation when a project provides one.

A dependency declaration is intrinsic to the package containing it, but extrinsic to the dependency it refers to; collected across a registry, those declarations map downstream use. [Software Heritage Identifiers](https://nesbitt.io/2026/10/01/software-heritage-identifiers.html) discusses connecting package identities with preserved source content, so observations can refer to a specific artifact even after a repository is renamed or transferred.

## Comparisons

A cohort is a group selected for comparison, such as packages in one registry or the dependencies of a set of applications; [cohorts.md](cohorts.md) proposes groupings for ecosystem-wide analysis. Comparing a volunteer maintaining a small library with a large paid team can turn differences in staffing into an apparent judgement about the software.

Maintainers may publish many packages from one repository, and a project may be distributed through multiple registries. Counting those entries as independent maintainer teams counts the same people once per package. A wrapper and its underlying library need a recorded relationship too, since their package names may be unrelated.

A library's incoming dependency declarations can be informative, while an application may have few such declarations because people run it directly. [The Roles of Packages](https://nesbitt.io/2026/03/29/the-roles-of-packages.html) sorts packages by role, such as application, library, framework, plugin or wrapper, and [A Taxonomy for Open Source Software](https://nesbitt.io/2025/11/29/oss-taxonomy.html) classifies projects along several facets at once; either lets a cohort group applications with applications and libraries with libraries. Download counters differ between registries as well, and [The Mismeasure of Open Source](https://nesbitt.io/2026/05/09/the-mismeasure-of-open-source.html) covers how these differences in distribution and packaging affect comparisons.

Following the same projects over time measures change within a fixed group, while repeatedly selecting the current top packages also measures projects entering and leaving the list. Both comparisons need a stated observation window and a way to distinguish unknown data from an observed zero. A missing issue record could mean the indexer skipped the tracker or that development happens on another platform.

## Census

In July 2015, a year after Heartbleed, the Linux Foundation's Core Infrastructure Initiative published a [census of open source projects](https://github.com/ossf/census). It took Debian packages above a popularity threshold and scored each for risk, producing a ranked list of 428 projects. [Revisiting the 2015 Open Source Census](https://nesbitt.io/2026/05/06/revisiting-the-2015-open-source-census.html) compares those rankings with what happened to the projects over the following ten years.

libexpat scored the maximum of 13 with its maintenance apparently halted; it then had a run of CVEs, received CII funding and is now actively maintained. unzip, rsync, zlib, ntp and OpenSSL were all in the top quarter, and each had further vulnerabilities of the kinds the model scored for.

xz-utils was at row 254 with a score of 6, largely because the heaviest term, worth up to 5 of the 13 points, was a contributor count of zero for the previous twelve months. OpenHub recorded five contributors for xz, who were effectively one exhausted maintainer. The formula was modelled on OpenSSL's 2014 situation, a widely deployed library whose maintenance had lapsed, whereas xz had an outsider keen to help; Jia Tan's arrival raised every contributor count anyone was tracking, which would have moved xz further down the list. A reviewer's free-text comment on the same row read "Vital, a vulnerability here could be very serious", and that row's score ranked it below 236 others.

Only Debian packages above a popularity threshold were scored, so selection removed projects before any weights applied. sudo and polkit were absent from the 428, and both later had serious vulnerabilities (Baron Samedit and PwnKit) present in their code since 2011 and 2009.

libxml2 scored 8 as a widely used C parser with few contributors, and in 2025 its sole maintainer stepped down after triaging embargoed security reports unpaid had become a part-time job. The census scored the structural risk, a widely used parser with a thin contributor base, but its inputs had no measure of when or how that risk would surface, and the funding it was meant to direct went elsewhere.

Current scoring tools weight recent contributor counts heavily: OpenSSF Scorecard checks for commits in the last 90 days, and criticality_score, the census formula's direct descendant, weights recent committer counts and commit frequency. In criticality_score those inputs raise a project's score, so a project losing contributors looks less critical at the point it most needs help, and lists built from it rank struggling projects lower. [The Mismeasure of Open Source](https://nesbitt.io/2026/05/09/the-mismeasure-of-open-source.html) describes the same pattern across download counts, dependency graphs, contributor metrics, Scorecard, funding records and activity checks: "the quiet system library with one tired maintainer and no dashboard footprint is exactly what we built all of this tooling to find, and it remains the thing the tooling is structurally worst at seeing." Each input is useful to look at, but once one becomes the sort key, reviewers work down from the top and mostly stop before the bottom half. Publishing the inputs and reviewer notes alongside a ranking preserves comments like the 2015 reviewer's note on xz. Each scoring model is built around a failure its designers had seen: the census formula around OpenSSL in 2014, and contributor counts around abandonment, so the arrival of an outsider at xz counted in its favour.

## Scores

A stable library developed through a mailing list and distributed through operating-system packages might have few registry downloads and little GitHub activity, and an empty public sponsorship record. The project can lose points in a composite score for each gap. [The Mismeasure of Open Source](https://nesbitt.io/2026/05/09/the-mismeasure-of-open-source.html) gives examples of one project scoring low on several inputs because all of them are drawn from platforms it uses little.

A requirement for a GitHub repository or a minimum download count excludes some projects before scoring begins. Smaller ecosystems can fall below global volume thresholds while containing dependencies important to their own users. Reweighting changes only the order of projects already admitted, and publishers of a ranking may leave out any list of the excluded projects.

[Centrality is not vitality](https://nesbitt.io/2026/05/14/centrality-is-not-vitality.html) argues that a high graph centrality score gets misread as a sign of active maintenance. A package whose maintainer has stopped responding can still rank as highly central, since other packages declare it. Its score also depends on packaging conventions: a project publishing many packages produces a different structure from a similar project distributed as one package.

Changes in source coverage can move a score when only the data collection changed. [How much should you trust your OSS data?](https://nesbitt.io/2026/09/04/how-much-should-you-trust-your-oss-data.html), co-authored with Sophia Vargas, documents this problem with GH Archive, and any dataset built on those records contains the same gaps. When funders or security teams use rankings to allocate money or audits, projects with less familiar development practices or less visible users receive less of both.

## AI

AI lowers the effort of generating a pull request but leaves review effort on the maintainer, so a rising count can mean a larger review burden. [CHAOSS Metrics in 2026](https://nesbitt.io/2026/05/27/chaoss-metrics-in-2026.html) examines this change, along with automated replies that shorten response times and multiple accounts that inflate contributor counts.

CHAOSS metric definitions already account for automation: its [Time to First Response](https://www.chaoss.community/kb/metric-time-to-first-response/) definition excludes automated replies, and [Bot Activity](https://www.chaoss.community/kb/metric-bot-activity/) measures automation separately. Applying those definitions is harder when agents commit through ordinary accounts and their operators omit any disclosure.

[A year of AI disclosure in critical packages](https://nesbitt.io/2026/08/06/a-year-of-ai-disclosure-in-critical-packages.html) counts explicit markers of assistance, which gives a lower bound on AI use, since unmarked commits could go either way. Inspecting the resulting code or asking maintainers about their work supplies evidence beyond event counts.

## Bernie's

The Weekend at Bernie's studies check whether the maintainers behind critical packages are still active and responding, and store the evidence behind each classification with the label. The [May study](https://nesbitt.io/2026/05/08/weekend-at-bernies.html) joined critical-package records to commit, issue and advisory data. Its 8,606 packages mapped to 5,874 distinct repositories across sixteen registries. It separated low development activity from observed maintainer interaction and from cases where responsiveness had not been tested. Packages with unanswered requests and zero recorded maintainer activity were still installed and downloaded.

The [November follow-up](https://nesbitt.io/2026/11/06/weekend-at-bernies-ii.html) reported a similar overall distribution, alongside substantial movement between the published classifier labels:

| Published category | May | November |
| --- | ---: | ---: |
| `active` | 48.8% | 49.9% |
| `dormant` | 20.2% | 18.7% |
| `dead` | 12.1% | 11.8% |
| `unknown` | 18.9% | 19.5% |

Behind the steady totals, movement went both ways: 421 repositories moved into `active` from other categories and 295 moved into `dead`. Running the May version of the classifier over the November data changed only 23 classifications, so the movement came from activity in the repositories and from older issues and releases leaving the one-year window, with rule changes accounting for little of it. Registry maintainer lists changed for only 16 of the 421 revived repositories, and six of those involved a new person taking on the work. Of the 1,086 repositories that were `unknown` in May, 189 received an outside issue or pull request, maintainers responded in 94, and 78 with zero maintainer activity moved to `dead`.

The November cohort contained 6,106 repositories, and some returning maintainers disclosed AI assistance in their commits. The follow-up also reports apparently unpatched advisories whose fixes shipped under successor package names or in downstream distributions, and measures delays between a maintainer publishing an advisory and its inclusion in a reviewed database.

In the [analysis code](https://github.com/andrew/weekend-at-bernies), `fetch.rb` selects critical packages and `classify.rb` applies thresholds to the collected evidence, storing each result with its supporting signals. The current classifier checks source freshness, and reports include source sync dates alongside the classification date: rerunning a calculation can reuse older observations.

The `dead` label covers archived repositories and observed non-response within the study's window. [Dumb Ways for an Open Source Project to Die](https://nesbitt.io/2026/05/19/dumb-ways-for-an-open-source-project-to-die.html) lists routes into that state, including a maintainer leaving, sabotage, a broken release pipeline and a project split, several of which look identical in the records. The label applies to those records only; code defects and a volunteer's personal circumstances are outside its inputs. `unknown` holds cases with too little evidence to classify. Automated closes can resemble maintainer interaction, and in a monorepo, activity elsewhere can obscure the state of one package.

## Criticality

A dependency declaration might help identify affected applications during an incident or trace use for a funding assessment. The same record supports both uses, with the person making each decision supplying the criteria.

A list of critical packages is built on choices: the threshold, whether it counts downloads, dependents or both, which registries were collected and how package identities were matched across them. A list built to capture concentrated usage puts packages in a different order from one built to assess security or maintainer availability. Record those choices with the package records when the list is used as a cohort.

## Requirements

### Measurements

- A cohort's selection rule is published with its membership, including what was excluded before any observation or scoring, since selection limits which projects any later analysis can include.
- Each observation records its source, collection date and the window it covers.
- Missing data is recorded as unknown, separately from an observed zero, with the reason where known, such as an unindexed tracker or a registry without a public download counter. An observed zero records which sources were checked, since zero activity across forge, registry and mailing list is stronger evidence than zero activity on one partially indexed source.
- Coverage is published for each source: which registries, forges and distribution channels were collected, and which users and channels are absent.
- Relationships between records are explicit: packages to repositories, wrappers to the libraries they wrap, repackaged copies to their upstream project, and accounts to people where they can be resolved.

### Interpretations

- Classifications such as `dormant` or `dead` are published separately from their inputs, with the rule version and the signals behind each label, so comparing a rerun with the original separates changes in the project from changes in the window or the rule.
- Each classification records its subject: code, project arrangements, contributor work or use.
- Statements about maintainer availability distinguish observed responses from responsiveness that has not been tested.
- Each score is published next to its inputs, with a record of the failure it was designed around.

### Decisions

- A ranking or funding list is published with the stakeholder and rubric it was built for.
- A metric used to direct funding or support does not lower a project's position because of signs of struggle, such as falling activity, a shrinking maintainer team or unanswered reports; how much those signs raise its priority depends on the funder's rubric.
- Comparisons hold staffing and package role roughly constant, or record where they differ.
- The point where an observed fact becomes a priority is recorded, so another stakeholder can reuse the same observations with their own criteria.

## License

The contents of this repository are dedicated to the public domain under [CC0 1.0 Universal](LICENSE).
