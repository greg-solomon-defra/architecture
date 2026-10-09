<!-- https://greg-solomon-defra.github.io/architecture/guardrails/data/ | maturity: published | site version 0.3.0 | generated from guardrails/data.md -->

# Data

<p class="lead">Defra's science, regulation and payments all depend on trusted data. These guardrails make sure that the data each service creates is an asset for the whole of Defra group, and any other appropriate data users.</p>

<div class="da-trace" markdown>

**Doctrine:** [4. Data is an enterprise asset](https://greg-solomon-defra.github.io/architecture/principles/doctrine/#ddts-04), [5. Assume AI until proven otherwise](https://greg-solomon-defra.github.io/architecture/principles/doctrine/#ddts-05)  
**Principles:** [4. Clean data, clear decisions](https://greg-solomon-defra.github.io/architecture/principles/architecture-principles/#gr-prin-04)

</div>


!!! info "Who these guardrails apply to"
    The core department. Whether the data guardrails also apply to Defra's arm's length bodies is [still to be confirmed](https://greg-solomon-defra.github.io/architecture/guardrails/#arms-length-bodies).


See also [enterprise data architecture](https://greg-solomon-defra.github.io/architecture/data/).

These guardrails are a **draft** proposal. Comment on them by [opening an issue](https://github.com/DEFRA/architecture/issues).

<hr>

## Narrative

Data architecture begins with defining the [CONTEXT](https://greg-solomon-defra.github.io/architecture/guardrails/data/#gr-data-12) and [OWNERSHIP](https://greg-solomon-defra.github.io/architecture/guardrails/data/#gr-data-01) of the proposed data assets.

Bring data into the solution architecture through [RE-USE](https://greg-solomon-defra.github.io/architecture/guardrails/data/#gr-data-02) of authoritative data sources (customers, organisations, land parcels, etc) and ensure [COMPLIANCE](https://greg-solomon-defra.github.io/architecture/guardrails/data/#gr-data-10) in the acquisition of any new data. Seek to [SHARE](https://greg-solomon-defra.github.io/architecture/guardrails/data/#gr-data-04) data wherever it is appropriate to do so, but to classify and [PROTECT](https://greg-solomon-defra.github.io/architecture/guardrails/data/#gr-data-06) all sensitive data.

Create data assets that comply with agreed [STANDARDS](https://greg-solomon-defra.github.io/architecture/guardrails/data/#gr-data-03), so that you can [PUBLISH](https://greg-solomon-defra.github.io/architecture/guardrails/data/#gr-data-07) and [DESCRIBE](https://greg-solomon-defra.github.io/architecture/guardrails/data/#gr-data-05) datasets of known [QUALITY](https://greg-solomon-defra.github.io/architecture/guardrails/data/#gr-data-08). Be open about the [LINEAGE](https://greg-solomon-defra.github.io/architecture/guardrails/data/#gr-data-13) of your data, and ensure [DISPOSAL](https://greg-solomon-defra.github.io/architecture/guardrails/data/#gr-data-09) of it in line with regulation, policy and guidance.

Protect [ANONYMITY](https://greg-solomon-defra.github.io/architecture/guardrails/data/#gr-data-11) by avoiding the use of real personal data in any non-production systems.

<hr>

## How to read a guardrail

Each guardrail has an identifier, a level, a short rationale and a way to show you meet it.

| Level | Means | If you cannot meet it |
| --- | --- | --- |
| <span class="rfc rfc--must">Must</span> | A requirement from law or mandatory government policy, a baseline security control, or a [DDTS doctrine](https://greg-solomon-defra.github.io/architecture/principles/doctrine/) non-negotiable. We keep these few. | You need an approved [exception](https://greg-solomon-defra.github.io/architecture/governance/exceptions/) from the Technical Design Authority. |
| <span class="rfc rfc--should">Should</span> | The strong default. There may be good reasons to differ. | Record why in an [architecture decision record](https://greg-solomon-defra.github.io/architecture/governance/architecture-decision-records/) and share it with your solution design authority. |
| <span class="rfc rfc--could">Could</span> | Recommended good practice. | No action needed, but we would like to know what worked better. |

## GR-DATA-12 CONTEXT: Align with the enterprise data model {#gr-data-12}

<span class="rfc rfc--should">Should</span> Design should begin with the enterprise data model, to ensure that an enterprise view of stakeholders, IT systems, and data designs is taken into sufficient consideration.

??? "The why and how of GR-DATA-12"
    **Why:** All of the data guardrails apply to the enterprise context, and the enterprise data model ensures a written record of that can be used in common across Defra.


<details class="gr-meta"><summary>Phases, evidence and status for GR-DATA-12</summary><dl><dt>Status</dt><dd><span class="gr-status gr-status--draft">Draft</span></dd><dt>Phases</dt><dd>Discovery, Alpha, Beta, Live</dd><dt>Led by</dt><dd><a href="../../deliver/roles/data-architect/">Data architect</a></dd><dt>Evidence</dt><dd>Data model which complies with the data modelling standards</dd><dt>Automated check</dt><dd>Manual</dd><dt>DDTS doctrine</dt><dd><a href="../../principles/doctrine/#ddts-04">4</a>, <a href="../../principles/doctrine/#ddts-05">5</a></dd><dt>Owner</dt><dd>Enterprise data architecture, last reviewed 2026-10-01, since v0.1.0</dd></dl></details>

## GR-DATA-01 OWNERSHIP: Assign an accountable owner to your data assets {#gr-data-01}

<span class="rfc rfc--should">Should</span> Each data set a service creates or holds has a named business owner (information asset owner) and is recorded in the information asset register.

??? "The why and how of GR-DATA-01"
    **Why:** Data without an owner is not maintained, not trusted and not deleted when it should be.


<details class="gr-meta"><summary>Phases, evidence and status for GR-DATA-01</summary><dl><dt>Status</dt><dd><span class="gr-status gr-status--draft">Draft</span></dd><dt>Phases</dt><dd>Alpha, Beta, Live</dd><dt>Led by</dt><dd><a href="../../deliver/roles/data-architect/">Data architect</a>, <a href="../../deliver/roles/product-manager/">Product manager</a></dd><dt>Evidence</dt><dd><ul class="gr-meta__phases"><li><strong>Alpha:</strong> Each data set the service will create or hold identified, with a proposed information asset owner</li><li><strong>Beta:</strong> Information asset register entries with a named owner for each data set</li><li><strong>Live:</strong> Register entries and owners kept current</li><li><strong>Retire:</strong> Information asset register updated to show what happened to each data set</li></ul></dd><dt>Automated check</dt><dd>Manual</dd><dt>Maps to</dt><dd><a href="https://www.gov.uk/guidance/the-technology-code-of-practice">Technology Code of Practice</a> <abbr title="Make better use of data">10</abbr></dd><dt>DDTS doctrine</dt><dd><a href="../../principles/doctrine/#ddts-04">4</a>, <a href="../../principles/doctrine/#ddts-05">5</a></dd><dt>Owner</dt><dd>Enterprise data architecture, last reviewed 2026-10-01, since v0.1.0</dd></dl></details>

## GR-DATA-02 DATA RE-USE: Use authoritative data sources {#gr-data-02}

<span class="rfc rfc--should">Should</span> Use the authoritative source for shared entities - customers, organisations, land parcels, holdings, locations, species - rather than creating local copies that drift. See [Defra on a page](https://greg-solomon-defra.github.io/architecture/data/defra-on-a-page/).

??? "The why and how of GR-DATA-02"
    **How to meet it:** If you must cache or replicate, record the source, refresh frequency and how you handle changes.


<details class="gr-meta"><summary>Phases, evidence and status for GR-DATA-02</summary><dl><dt>Status</dt><dd><span class="gr-status gr-status--draft">Draft</span></dd><dt>Phases</dt><dd>Discovery, Alpha, Beta, Live</dd><dt>Led by</dt><dd><a href="../../deliver/roles/data-architect/">Data architect</a></dd><dt>Evidence</dt><dd><ul class="gr-meta__phases"><li><strong>Discovery:</strong> Shared entities the service needs identified, with their authoritative sources</li><li><strong>Alpha:</strong> Data flow diagram naming the authoritative source for each shared entity, and how any copies are refreshed</li><li><strong>Beta:</strong> The service reads from the authoritative sources as designed, tested with the source owners</li><li><strong>Live:</strong> Copies and refresh arrangements reviewed when sources change</li></ul></dd><dt>Automated check</dt><dd>Manual</dd><dt>Maps to</dt><dd><a href="https://www.gov.uk/guidance/the-technology-code-of-practice">Technology Code of Practice</a> <abbr title="Make better use of data">10</abbr></dd><dt>DDTS doctrine</dt><dd><a href="../../principles/doctrine/#ddts-04">4</a>, <a href="../../principles/doctrine/#ddts-05">5</a></dd><dt>Owner</dt><dd>Enterprise data architecture, last reviewed 2026-10-01, since v0.1.0</dd></dl></details>

## GR-DATA-10 COMPLIANCE: Acquire new data safely {#gr-data-10}

<span class="rfc rfc--should">Should</span> Collect research data only with informed consent, store recordings and notes only in Defra-approved places, delete them when they are no longer needed, use only Defra-approved research tools, and screen research for a DPIA.

??? "The why and how of GR-DATA-10"
    **Why:** User research often collects personal data: recordings, notes, contact details and what participants type into prototypes. How to do this is set out in the user research [standards and guidance](https://digital.defra.gov.uk/user-research/standards-and-guidance) (consent, participant data handling, and storage and retention) and [tools](https://digital.defra.gov.uk/user-research/tools) in the Defra Digital Service Manual. Research recordings and notes are personal data about real people. Keeping them in personal accounts, unapproved tools or for longer than needed puts participants at risk and breaks data protection law.

    **How to meet it:**

    - Get informed consent before each session, using the templates in the manual's [standards and guidance](https://digital.defra.gov.uk/user-research/standards-and-guidance).
    - Store recordings and notes only where the manual's participant data storage and retention guidance says, and set a deletion date when you collect them.
    - Use only the manual's [approved research tools](https://digital.defra.gov.uk/user-research/tools), and check a tool can hold the data you plan to collect. Assess any new tool before using it ([GR-TECH-04](https://greg-solomon-defra.github.io/architecture/guardrails/choosing-technology/#gr-tech-04)).
    - Screen the research for a DPIA ([GR-DATA-06](https://greg-solomon-defra.github.io/architecture/guardrails/data/#gr-data-06)), especially for new tools, sensitive topics or recordings of people's homes or farms.
    - Do not put recordings or transcripts into AI tools except as the [AI digital toolkit](https://digital.defra.gov.uk/ai-toolkit/guidance/keeping-data-safe) allows.


<details class="gr-meta"><summary>Phases, evidence and status for GR-DATA-10</summary><dl><dt>Status</dt><dd><span class="gr-status gr-status--draft">Draft</span></dd><dt>Phases</dt><dd>Discovery, Alpha, Beta, Live</dd><dt>Led by</dt><dd><a href="../../deliver/roles/user-researcher/">User researcher</a></dd><dt>Evidence</dt><dd><ul class="gr-meta__phases"><li><strong>Discovery:</strong> Consent forms and privacy notice in use, recordings and notes stored only in approved places, and a deletion date set</li><li><strong>Alpha:</strong> The same for alpha research, with DPIA screening done for the research and any new research tool assessed</li><li><strong>Beta:</strong> Research data from earlier phases deleted on schedule, and the same controls for beta research</li><li><strong>Live:</strong> Research data handled the same way for ongoing research, and deletion checked</li></ul></dd><dt>Automated check</dt><dd>Manual</dd><dt>DDTS doctrine</dt><dd><a href="../../principles/doctrine/#ddts-04">4</a>, <a href="../../principles/doctrine/#ddts-05">5</a></dd><dt>Owner</dt><dd>Enterprise data architecture, last reviewed 2026-10-01, since v0.3.0</dd></dl></details>

## GR-DATA-04 SHARE: Collect once, share safely {#gr-data-04}

<span class="rfc rfc--should">Should</span> Do not ask users for information Defra already holds. Share data between services through APIs or governed data products, with data sharing agreements where required.


<details class="gr-meta"><summary>Phases, evidence and status for GR-DATA-04</summary><dl><dt>Status</dt><dd><span class="gr-status gr-status--draft">Draft</span></dd><dt>Phases</dt><dd>Alpha, Beta</dd><dt>Led by</dt><dd><a href="../../deliver/roles/service-designer/">Service designer</a></dd><dt>Evidence</dt><dd>Journey design showing users are not asked for information Defra already holds, and data sharing agreements where required</dd><dt>Automated check</dt><dd>Manual</dd><dt>Maps to</dt><dd><a href="https://www.gov.uk/guidance/the-technology-code-of-practice">Technology Code of Practice</a> <abbr title="Share, reuse and collaborate">8</abbr>, <abbr title="Make better use of data">10</abbr></dd><dt>DDTS doctrine</dt><dd><a href="../../principles/doctrine/#ddts-04">4</a>, <a href="../../principles/doctrine/#ddts-05">5</a></dd><dt>Owner</dt><dd>Enterprise data architecture, last reviewed 2026-10-01, since v0.1.0</dd></dl></details>

## GR-DATA-06 PROTECT: Protect sensitive data by design {#gr-data-06}

<span class="rfc rfc--must">Must</span> Complete a data protection impact assessment (DPIA) before processing personal data, minimise what you collect, and apply retention and deletion automatically.

??? "The why and how of GR-DATA-06"
    **Why:** UK GDPR and the Data Protection Act 2018; TCoP point 7.


<details class="gr-meta"><summary>Phases, evidence and status for GR-DATA-06</summary><dl><dt>Status</dt><dd><span class="gr-status gr-status--draft">Draft</span></dd><dt>Phases</dt><dd>Discovery, Alpha, Beta, Live</dd><dt>Led by</dt><dd><a href="../../deliver/roles/data-architect/">Data architect</a>, <a href="../../deliver/roles/product-manager/">Product manager</a></dd><dt>Evidence</dt><dd><ul class="gr-meta__phases"><li><strong>Discovery:</strong> DPIA screening completed, showing whether personal data is involved</li><li><strong>Alpha:</strong> Draft DPIA, with data minimisation and retention designed in</li><li><strong>Beta:</strong> Approved DPIA, and retention and deletion built and tested</li><li><strong>Live:</strong> DPIA reviewed when processing changes, and deletion running as designed</li><li><strong>Significant change:</strong> DPIA updated for any change in how personal data is processed</li><li><strong>Retire:</strong> Personal data deleted or transferred lawfully, as set out in the DPIA</li></ul></dd><dt>Automated check</dt><dd>Manual</dd><dt>Maps to</dt><dd><a href="https://www.gov.uk/service-manual/service-standard">Service Standard</a> <abbr title="Create a secure service which protects users&#x27; privacy">9</abbr>; <a href="https://www.gov.uk/guidance/the-technology-code-of-practice">Technology Code of Practice</a> <abbr title="Make privacy integral">7</abbr></dd><dt>DDTS doctrine</dt><dd><a href="../../principles/doctrine/#ddts-04">4</a>, <a href="../../principles/doctrine/#ddts-05">5</a></dd><dt>Owner</dt><dd>Enterprise data architecture, last reviewed 2026-10-01, since v0.1.0</dd></dl></details>

## GR-DATA-03 STANDARDS: Use data standards identifiers {#gr-data-03}

<span class="rfc rfc--should">Should</span> Use the [data standards](https://greg-solomon-defra.github.io/architecture/data/data-standards/) for dates, addresses, locations, identifiers and code lists, so data can be joined across services.


<details class="gr-meta"><summary>Phases, evidence and status for GR-DATA-03</summary><dl><dt>Status</dt><dd><span class="gr-status gr-status--draft">Draft</span></dd><dt>Phases</dt><dd>Alpha, Beta</dd><dt>Led by</dt><dd><a href="../../deliver/roles/data-architect/">Data architect</a></dd><dt>Evidence</dt><dd><ul class="gr-meta__phases"><li><strong>Alpha:</strong> Data model using the agreed data standards and identifiers</li><li><strong>Beta:</strong> Data stored and exchanged using the agreed standards, checked in testing</li></ul></dd><dt>Automated check</dt><dd>Manual</dd><dt>Maps to</dt><dd><a href="https://www.gov.uk/service-manual/service-standard">Service Standard</a> <abbr title="Use and contribute to open standards, common components and patterns">13</abbr>; <a href="https://www.gov.uk/guidance/the-technology-code-of-practice">Technology Code of Practice</a> <abbr title="Make use of open standards">4</abbr>, <abbr title="Make better use of data">10</abbr></dd><dt>DDTS doctrine</dt><dd><a href="../../principles/doctrine/#ddts-04">4</a>, <a href="../../principles/doctrine/#ddts-05">5</a></dd><dt>Owner</dt><dd>Enterprise data architecture, last reviewed 2026-10-01, since v0.1.0</dd></dl></details>

## GR-DATA-07 PUBLISH: Make your data open by default {#gr-data-07}

<span class="rfc rfc--should">Should</span> Publish non-personal, non-sensitive data as open data under the Open Government Licence, through the [Defra Data Services Platform](https://environment.data.gov.uk/) or [data.gov.uk](https://www.data.gov.uk/).


<details class="gr-meta"><summary>Phases, evidence and status for GR-DATA-07</summary><dl><dt>Status</dt><dd><span class="gr-status gr-status--draft">Draft</span></dd><dt>Phases</dt><dd>Beta, Live</dd><dt>Led by</dt><dd><a href="../../deliver/roles/data-architect/">Data architect</a>, <a href="../../deliver/roles/product-manager/">Product manager</a></dd><dt>Evidence</dt><dd>Link to the published open data and its licence</dd><dt>Automated check</dt><dd>Manual</dd><dt>Maps to</dt><dd><a href="https://www.gov.uk/guidance/the-technology-code-of-practice">Technology Code of Practice</a> <abbr title="Make better use of data">10</abbr></dd><dt>DDTS doctrine</dt><dd><a href="../../principles/doctrine/#ddts-04">4</a>, <a href="../../principles/doctrine/#ddts-05">5</a></dd><dt>Owner</dt><dd>Enterprise data architecture, last reviewed 2026-10-01, since v0.1.0</dd></dl></details>

## GR-DATA-05 DESCRIBE: Explain your data to users {#gr-data-05}

<span class="rfc rfc--should">Should</span> Publish metadata for data sets so they can be found and understood - [UK GEMINI](https://www.agi.org.uk/why-uk-gemini/) for geospatial data and [DCAT](https://www.w3.org/TR/vocab-dcat-3/) for other data sets.


<details class="gr-meta"><summary>Phases, evidence and status for GR-DATA-05</summary><dl><dt>Status</dt><dd><span class="gr-status gr-status--draft">Draft</span></dd><dt>Phases</dt><dd>Beta, Live</dd><dt>Led by</dt><dd><a href="../../deliver/roles/data-architect/">Data architect</a></dd><dt>Evidence</dt><dd>Published metadata records in UK GEMINI or DCAT</dd><dt>Automated check</dt><dd>Manual</dd><dt>Maps to</dt><dd><a href="https://www.gov.uk/guidance/the-technology-code-of-practice">Technology Code of Practice</a> <abbr title="Make better use of data">10</abbr></dd><dt>DDTS doctrine</dt><dd><a href="../../principles/doctrine/#ddts-04">4</a>, <a href="../../principles/doctrine/#ddts-05">5</a></dd><dt>Owner</dt><dd>Enterprise data architecture, last reviewed 2026-10-01, since v0.1.0</dd></dl></details>

## GR-DATA-08 QUALITY: Define, measure & manage data quality {#gr-data-08}

<span class="rfc rfc--should">Should</span> Define, measure and report data quality using the [Government Data Quality Framework](https://www.gov.uk/government/publications/the-government-data-quality-framework), especially for data that feeds payments, regulatory decisions or official statistics.


<details class="gr-meta"><summary>Phases, evidence and status for GR-DATA-08</summary><dl><dt>Status</dt><dd><span class="gr-status gr-status--draft">Draft</span></dd><dt>Phases</dt><dd>Beta, Live</dd><dt>Led by</dt><dd><a href="../../deliver/roles/data-architect/">Data architect</a>, <a href="../../deliver/roles/performance-analyst/">Performance analyst</a></dd><dt>Evidence</dt><dd>Data quality measures and regular reports</dd><dt>Automated check</dt><dd>Manual</dd><dt>Maps to</dt><dd><a href="https://www.gov.uk/guidance/the-technology-code-of-practice">Technology Code of Practice</a> <abbr title="Make better use of data">10</abbr></dd><dt>DDTS doctrine</dt><dd><a href="../../principles/doctrine/#ddts-04">4</a>, <a href="../../principles/doctrine/#ddts-05">5</a></dd><dt>Owner</dt><dd>Enterprise data architecture, last reviewed 2026-10-01, since v0.1.0</dd></dl></details>

## GR-DATA-13 LINEAGE: Trace decisions to trusted data {#gr-data-13}

<span class="rfc rfc--should">Should</span> Record where the data behind each decision comes from, how it was transformed and which rules or models were applied, so any decision can be traced back to trusted sources.

??? "The why and how of GR-DATA-13"
    **Why:** Payments, regulatory decisions and official statistics must be explainable and open to challenge. Without lineage you cannot show why a decision was made, correct it when a source turns out to be wrong, or reproduce it later.

    **How to meet it:**

    - Identify the decisions the service makes or supports, and the data each one depends on.
    - Take that data from authoritative sources ([GR-DATA-02](https://greg-solomon-defra.github.io/architecture/guardrails/data/#gr-data-02)) and record the version or time of each extract.
    - Capture lineage automatically in pipelines rather than in documents written by hand.
    - Record the rule or model version used for each decision, alongside the data quality measures for its inputs ([GR-DATA-08](https://greg-solomon-defra.github.io/architecture/guardrails/data/#gr-data-08)).
    - Keep lineage records for as long as the decision records they support ([GR-DATA-09](https://greg-solomon-defra.github.io/architecture/guardrails/data/#gr-data-09)).


<details class="gr-meta"><summary>Phases, evidence and status for GR-DATA-13</summary><dl><dt>Status</dt><dd><span class="gr-status gr-status--draft">Draft</span></dd><dt>Phases</dt><dd>Alpha, Beta, Live</dd><dt>Led by</dt><dd><a href="../../deliver/roles/data-architect/">Data architect</a></dd><dt>Evidence</dt><dd><ul class="gr-meta__phases"><li><strong>Alpha:</strong> Decisions the service makes or supports identified, with the data each one depends on and its authoritative source</li><li><strong>Beta:</strong> Lineage captured automatically from source to decision, including transformations, rules and model versions</li><li><strong>Live:</strong> Lineage kept current when sources, rules or models change, and used to explain or reproduce past decisions</li></ul></dd><dt>Automated check</dt><dd>Manual</dd><dt>Maps to</dt><dd><a href="https://www.gov.uk/guidance/the-technology-code-of-practice">Technology Code of Practice</a> <abbr title="Make better use of data">10</abbr></dd><dt>DDTS doctrine</dt><dd><a href="../../principles/doctrine/#ddts-04">4</a>, <a href="../../principles/doctrine/#ddts-05">5</a></dd><dt>Owner</dt><dd>Enterprise data architecture, last reviewed 2026-10-01, since v0.4.0</dd></dl></details>

## GR-DATA-09 DISPOSAL: Retain and dispose of records properly {#gr-data-09}

<span class="rfc rfc--must">Must</span> Apply Defra's retention schedules. Records of permanent value are identified for transfer to The National Archives.


<details class="gr-meta"><summary>Phases, evidence and status for GR-DATA-09</summary><dl><dt>Status</dt><dd><span class="gr-status gr-status--draft">Draft</span></dd><dt>Phases</dt><dd>Beta, Live</dd><dt>Led by</dt><dd><a href="../../deliver/roles/data-architect/">Data architect</a></dd><dt>Evidence</dt><dd><ul class="gr-meta__phases"><li><strong>Beta:</strong> Retention schedule identified for each type of record, and disposal built in</li><li><strong>Live:</strong> Retention applied and records of permanent value identified for The National Archives</li><li><strong>Retire:</strong> Records kept, transferred to The National Archives or destroyed, as agreed with the information asset owner</li></ul></dd><dt>Automated check</dt><dd>Manual</dd><dt>DDTS doctrine</dt><dd><a href="../../principles/doctrine/#ddts-04">4</a>, <a href="../../principles/doctrine/#ddts-05">5</a></dd><dt>Owner</dt><dd>Enterprise data architecture, last reviewed 2026-10-01, since v0.1.0</dd></dl></details>

## GR-DATA-11 ANONYMITY: No real personal data in prototypes {#gr-data-11}

<span class="rfc rfc--should">Should</span> Prototypes, research materials and test environments use made-up or anonymised data, never real personal data copied from a live service or spreadsheet.

??? "The why and how of GR-DATA-11"
    **Why:** Prototypes are shared widely, hosted on less protected platforms and shown to participants. Real data in them can be seen by people who should not see it.

    **How to meet it:** make up realistic names, addresses, holdings and reference numbers. Tell participants not to enter their own real details into a prototype unless the research plan allows it and the data is handled under [GR-DATA-10](https://greg-solomon-defra.github.io/architecture/guardrails/data/#gr-data-10). If a test genuinely needs real data, agree it through a DPIA first.
<details class="gr-meta"><summary>Phases, evidence and status for GR-DATA-11</summary><dl><dt>Status</dt><dd><span class="gr-status gr-status--draft">Draft</span></dd><dt>Phases</dt><dd>Discovery, Alpha, Beta</dd><dt>Led by</dt><dd><a href="../../deliver/roles/interaction-designer/">Interaction designer</a>, <a href="../../deliver/roles/user-researcher/">User researcher</a>, <a href="../../deliver/roles/developer/">Developer</a></dd><dt>Evidence</dt><dd><ul class="gr-meta__phases"><li><strong>Discovery:</strong> Any prototype uses made-up data</li><li><strong>Alpha:</strong> Prototypes and research materials use made-up data, including data a participant types in during a session</li><li><strong>Beta:</strong> Test and research environments use synthetic or anonymised data; any exception agreed through a DPIA</li></ul></dd><dt>Automated check</dt><dd>Manual</dd><dt>DDTS doctrine</dt><dd><a href="../../principles/doctrine/#ddts-04">4</a>, <a href="../../principles/doctrine/#ddts-05">5</a></dd><dt>Owner</dt><dd>Enterprise data architecture, last reviewed 2026-10-01, since v0.3.0</dd></dl></details>


