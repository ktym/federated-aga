---
title: 'Toward a Federated Asian Genome-Phenotype Archive: data discovery and governance from MedHackathon Asia 2026'
title_short: 'MedHackathon Asia 2026: Federated AGA'
tags:
  - human genomics
  - data sharing
  - controlled access
  - federated archive
  - Asia
  - Data Access Committee
authors:
  - name: Toshiaki Katayama
    orcid: 0000-0003-2391-0384
    affiliation: 1
    role: Conceptualization, Writing – original draft
  - name: Soichi Ogishima
    orcid: 0000-0001-8613-2562
    affiliation: 2
    role: Investigation, Writing – review & editing
  - name: Yosuke Kawai
    orcid: 0000-0003-0666-1224
    affiliation: 3
    role: Investigation, Writing – review & editing
  - name: Shailesh Kumar
    affiliation: 4
    role: Investigation, Writing – review & editing
  - name: Francis Tablizo
    affiliation: 5
    role: Investigation, Writing – review & editing
  - name: Jakris Eu-ahsunthornwattana
    orcid: 0000-0002-8060-9566
    affiliation: 6
    role: Investigation, Writing – review & editing
  - name: Nicolas Bertin
    orcid: 0000-0002-9835-9606
    affiliation: 7
    role: Investigation, Writing – review & editing
affiliations:
  - name: Database Center for Life Science (DBCLS), Joint Support-Center for Data Science Research, Research Organization of Information and Systems (ROIS), Japan
    index: 1
  - name: Tohoku Medical Megabank Organization (ToMMo), Tohoku University, Japan
    index: 2
  - name: National Center for Global Health and Medicine (NCGM), Japan
    index: 3
  - name: Indian Biological Data Centre (IBDC), India
    index: 4
  - name: Philippine Genome Center / Filipinome, Philippines
    index: 5
  - name: Faculty of Medicine Ramathibodi Hospital, Mahidol University, Thailand
    index: 6
  - name: Precision Health Research, Singapore (PRECISE), Singapore
    index: 7
date: 31 July 2026
cito-bibliography: paper.bib
event: MH26ASIA
biohackathon_name: "MedHackathon Asia 2026"
biohackathon_url:   "https://medhackathon.github.io/2026/"
biohackathon_location: "Singapore, 2026"
group: Federated Asian Genome-Phenotype Archive (AGA)
# URL to project git repo --- should contain the actual paper.md:
git_url: https://github.com/ktym/federated-aga
# This is the short authors description that is used at the
# bottom of the generated paper (typically the first two authors):
authors_short: Toshiaki Katayama \emph{et al.}
---

# Abstract

Open-access human sequence data can already be discovered through International Nucleotide Sequence Database Collaboration (INSDC) resources. The harder problem for Asian biomedical research is discovering and requesting controlled-access (CA) human genotype–phenotype and cohort data that remain fragmented across national archives, biobanks, and project-specific Data Access Committees (DACs). At MedHackathon Asia 2026 in Singapore, participants from Japan, India, Thailand, Singapore, and the Philippines examined how a Federated Asian Genome-Phenotype Archive (AGA) could improve regional data discoverability without requiring a single centralized data store. Building on MedHackathon Asia 2025 outcomes and on lessons from dbGaP, the European Genome-phenome Archive (EGA) and its Federated EGA network, and the Japanese Genotype-phenotype Archive (JGA), we compared repository models, surveyed country-specific access regimes, and outlined a two-step roadmap: first federate indexes of existing CA archives such as JGA and India’s INDA-CA; then design how national genome projects and biobanks should be represented in a shared catalog. We propose that AGA’s primary role is a human- and AI-friendly catalog that answers what data exist where, in what quantity, under which access rules, and through which DAC—while long-term accessibility remains with member archives and projects.

**Keywords:** Federated Asian Genome-Phenotype Archive; controlled access; Data Access Committee; MedHackathon Asia; genomic data sharing

# Introduction

Asian genomic resources are expanding rapidly, yet researchers still struggle to answer a basic question: what human research data exist in Asia, how much of each type is available, and how can access be requested? MedHackathon Asia 2025 highlighted that even the existence of national datasets was not routinely shared across borders [@citesAsRelated:MedHackathon2025]. The 2026 meeting continued that discussion with a concrete infrastructure focus: a Federated Asian Genome-Phenotype Archive (AGA) that would improve discovery of controlled-access data while respecting national and institutional governance [@citesAsSourceDocument:MedHackathon2026Web].

Under INSDC coordination, sister resources archive human research data used in publications: dbGaP in the United States [@citesAsAuthority:Tryka2014; @citesAsAuthority:Mailman2007], EGA in Europe [@citesAsAuthority:Freeberg2022; @citesAsAuthority:Lappalainen2015], and JGA in Japan [@citesAsAuthority:Kodama2015]. These archives assign stable identifiers, support citation, and route reuse through DACs. Federated EGA further shows that national nodes can keep data under local jurisdiction while exposing a shared discovery layer [@citesAsPotentialSolution:DAltri2025]. AGA aims at a related goal for Asia: not necessarily copying one federation architecture, but enabling a regional catalog that spans both INSDC-aligned CA archives and the large biobank and national genome projects that sit outside those archives [@citesAsRelated:MedHackathon2025; @citesAsAuthority:Arita2021].

Open-access (OA) data are already discoverable through Sequence Read Archive (SRA), European Nucleotide Archive (ENA), and DDBJ Sequence Read Archive (DRA). This report therefore focuses on CA data: how to find them, how to describe access requirements, and how to navigate applicants to the correct DAC.

# Background: reference genotype–phenotype archives

Table 1 summarizes the three reference CA archives discussed at the meeting. Approximate catalog counts were taken from public portals at the time of discussion and should be treated as snapshots rather than audited statistics [@citesAsDataSource:dbGaPWeb; @citesAsDataSource:EGAWeb; @citesAsDataSource:JGAWeb].

Table: Snapshot comparison of major genotype–phenotype archives discussed at MedHackathon Asia 2026.

| Archive | Region / operator | Approximate public catalog size | DAC model (high level) |
| ------- | ----------------- | ------------------------------- | ---------------------- |
| dbGaP | US / NCBI | ~3,579 studies; ~15,541 phenotype datasets; ~2,122 molecular datasets; ~14 DACs | DACs organized largely by NIH institutes overseeing studies, not one DAC per study |
| EGA / Federated EGA | Europe / EMBL-EBI (+ national nodes) | ~9,962 studies; ~13,779 datasets; ~3,208 DACs | Central and national nodes; often one DAC per dataset or study controller |
| JGA / NBDC Human Database | Japan / NIG-DDBJ (+ NBDC) | ~396 studies; ~979 datasets; 1 DAC | Single institutional DAC (NBDC Human Database) |

The architectural contrast among these systems is illustrated in Figure 1, adapted from the MedHackathon Asia 2025 community report: dbGaP as a centralized repository with multiple institutional DACs; Federated EGA as linked national nodes; and a prospective Asian model in which country- and project-level archives remain distributed while becoming discoverable together [@citesAsRelated:MedHackathon2025].

![Comparative schematic of genotype–phenotype archive architectures for the United States (dbGaP), Europe (Federated EGA), and a prospective Asian Genome Archive (AGA). Adapted from MedHackathon Asia 2025 discussions.](./MedHackathon2025-AGA.jpg){ width=100% }

Federated EGA also surfaces operational risks that AGA should anticipate: when DACs proliferate, or when a principal investigator (PI) effectively serves as the DAC, contact pathways can fail and previously granted access may become unavailable [@discusses:DAltri2025; @discusses:Freeberg2022]. Standards developed by the Global Alliance for Genomics and Health (GA4GH) provide a shared vocabulary for metadata, access, and authentication that AGA should reuse wherever practical [@citesAsRecommendedReading:Rehm2021].

# Needs and design challenges for AGA

Participants agreed that AGA should first be a catalog of datasets and DACs related to studies and cohorts in each country. If Asian research data are listed and searchable in one place, reuse becomes more realistic and dataset visibility improves for data producers as well as consumers. A second, forward-looking need is AI-assisted discovery: researchers should be able to ask questions such as “I want to study X—what Asian data are available and where?” and receive actionable pointers into the catalog and the corresponding DAC application process.

Several catalog-design challenges remain open. First, is the metadata already exposed by JGA and EGA necessary and sufficient for human and machine search? Current faceting and distribution summaries appear weak for large collections. Second, how should cohorts with thousands of phenotype parameters be summarized so that projects can register without unrealistic curation burden? Resources such as Tohoku Medical Megabank Organization (ToMMo) can be viewed either as one project with one mega-dataset or as many purpose-specific subsets. For PRECISE and ToMMo-like cohorts, one working idea was that each approved data-use application defines a research purpose and a corresponding subset; those subsets could later become first-class AGA records. Common ontologies and GA4GH-aligned metadata would improve faceted search if adopted early [@citesAsRecommendedReading:Rehm2021].

Membership and governance also need a pragmatic model. Designating a single representative institution per country is unlikely to succeed quickly. From Japan alone, independently operated resources such as JGA, ToMMo, BioBank Japan (BBJ), and GEM Japan (GeMJ) may each need a path to membership. Access rules themselves vary and should be described explicitly in the catalog. Table 2 records the provisional access-requirement codes used during the discussion.

Table: Provisional codes for additional access requirements beyond DAC approval (Tier 3 modifiers).

| Code | Meaning |
| ---- | ------- |
| A | Local collaborator required to access the data |
| A+ | A plus involvement of a local clinician (for example, clinical data in Thailand) |
| B | Accessible from academia only |
| C | Accessible by industry |
| D | Accessible if the study PI allows |

For browsing, AGA should provide hierarchical summaries and statistics by age, sex, disease, tissue, method, and data type, then navigate users from selected datasets to the correct DAC. Hosting can begin with a lightweight prototype (for example GitHub Pages) and later move to mirrored portals at member institutions; AI features will raise costs for APIs and, if used, local inference hardware.

# Country-specific situations

On 29 July 2026, participants from Japan (JGA, ToMMo, GeMJ), India (Indian Biological Data Centre, IBDC), Thailand (Genomics Thailand), Singapore (PRECISE), and the Philippines (Filipinome) compared national situations. Discussion focused on Tier 2 (controlled access through a DAC) and Tier 3 (DAC approval plus additional local conditions), while Tier 1 (open access) was treated as largely served by INSDC and related OA repositories.

Table: Country and project snapshots from MedHackathon Asia 2026 discussions (qualitative; not a complete inventory).

| Country (discussant) | Project / resource | Tier and access notes | Data held (examples) | International applications |
| -------------------- | ------------------ | --------------------- | -------------------- | -------------------------- |
| India (Shailesh Kumar) | IBDC | Tier 2; IBDC serves as DAC | Normal and cancer human genomics / multi-omics; Indian GTEx-like effort | Discussed in context of INDA / INDA-CA |
| Philippines (Francis Tablizo) | Filipinome (Philippine Genome Center) | Tier 3-D; currently one project with PI approval | Genomic data and clinical information | Not fully specified |
| Thailand (Jakris Eu-ahsunthornwattana) | Genomics Thailand | Tier 3-A+ for clinical data (clinician collaboration) | Genomics Thailand | Yes |
| Japan (Toshiaki Katayama, Soichi Ogishima, Yosuke Kawai) | JGA | Tier 2 via institutional DAC | Genome, transcriptome, exome, array, spatial transcriptome, and more | Yes |
| Japan | ToMMo | Tier 2 own DAC (including external experts); Tier 3-A if collaborating with ToMMo researchers | Cohort, genome, multi-omics, health information | Under consideration |
| Japan | AMED-funded disease studies | Often Tier 3-D; many datasets managed by individual PIs | Disease research data | Case by case |
| Singapore (Nicolas Bertin) | PRECISE / TRUST / MOH | Tier 2; TRUST DAC can route to sub-DACs; direct PRECISE applications also possible | PRECISE: genomic / UK Biobank-like data; MOH: selected EHR; TRUST: environmental and other data | To be clarified |

A recurring theme was the distinction between INSDC-aligned submission archives and national producers that keep their own DACs and large longitudinal collections. Treating an entire national cohort as a single catalog record makes search ineffective; finer-grained breakdowns are needed. The practical question that emerged for Day 2 was therefore: where do researchers in Asian countries actually deposit CA human research data today? For India, IBDC’s operation of INDA (SRA-equivalent) and INDA-CA (dbGaP-equivalent), with IBDC itself acting as DAC for the latter, provided a concrete non-JGA example.

# Vision and portal requirements

AGA’s near-term vision is a federated catalog that promotes mutual use of human research data across Asia by bringing two families of resources into one view [@citesAsRelated:FederatedAGARepo].

The first family is INSDC-aligned human research data: OA streams (SRA, ENA, DRA) and CA streams (dbGaP, EGA, JGA), with CNCB (China) and IBDC (India, including INDA-CA) as important related or upcoming partners. Shared submission and accession conventions already exist here and form the most practical backbone to federate first [@citesAsAuthority:Arita2021].

The second family is biobank and national genome data that largely sit outside those archives—for example ToMMo, GeMJ, and AMED-funded cohorts in Japan; GenomeIndia; PRECISE in Singapore; Genomics Thailand; Filipinome in the Philippines; and additional resources summarized in Table 1 of the MedHackathon Asia 2025 paper [@usesDataFrom:MedHackathon2025]. These resources currently use separate portals, metadata models, and access rules. Without a shared index, no one can answer in one place what human genome data exist in Asia and in what quantity.

The researcher journey that AGA must support mirrors Federated EGA usage today: discover relevant datasets in a catalog; identify and apply to the governing DAC; then analyze data in whatever environment the provider offers (trusted research environment, secure cloud workspace, or download) [@citesAsPotentialSolution:DAltri2025; @citesAsDataSource:EGAWeb]. AGA’s primary function is therefore to provide an overview of holdings by country, enable efficient human and AI search, make the application target unambiguous, and help ensure long-term accessibility by pointing to durable archives rather than ephemeral project websites.

# Discussion

The MedHackathon Asia 2026 AGA track clarified that “federation” in Asia need not mean immediate homogenization of storage or law. A useful first product is a shared index. That index must represent not only publication-supporting archives such as JGA, but also the political and operational reality that many of Asia’s most valuable datasets live in national biobanks with their own DACs and collaboration norms (codes A/A+/B/C/D). Catalog quality will determine success: weak faceting and opaque DAC contact paths already limit reuse in existing systems, and AI agents will amplify those weaknesses unless metadata and APIs are designed for machine consumption.

There is also a strategic choice between registering national-project data through an existing CA archive (for example depositing ToMMo subsets in JGA) versus admitting projects as AGA member nodes that publish their own indexes. Both routes may coexist; the important requirement is stable identifiers, sufficient summary metadata, and a durable path from discovery to DAC application.

# Conclusions

MedHackathon Asia 2026 advanced the Federated AGA concept from a 2025 aspiration to a concrete catalog-and-governance agenda. Reference systems (dbGaP, EGA/Federated EGA, JGA) show that accessioned CA archives and DAC workflows can work at scale, while Asian country snapshots show heterogeneous Tier 2/3 requirements that must be encoded rather than ignored. AGA should prioritize a discoverability layer that is useful to both humans and AI, federating existing CA archive indexes first and then incorporating national genome projects and biobanks.

# Future work

We propose a two-step program.

Step 1 is to federate controlled-access archives. Survey how many institutions across Asian countries, besides JGA, accept deposits of CA human research data; India’s IBDC INDA / INDA-CA model is an immediate reference. Define how JGA and peer organizations expose dataset indexes to an AGA portal (API plus a JSON schema for necessary-and-sufficient metadata). Prototype a portal that aggregates country indexes into searchable tables, facets, and visualizations.

Step 2 is to bring in national genome projects and biobanks. Revisit indexing strategies and required metadata. For ToMMo, for example, membership as an AGA node and registration of subsets via JGA are both plausible.

We intend to continue this work through interim Zoom meetings, the September BioHackathon 2026 [@citesAsRelated:BioHackathon2026Web], and the next MedHackathon Asia.

# Links to software and data

Working notes and manuscript sources for this report are maintained at [https://github.com/ktym/federated-aga](https://github.com/ktym/federated-aga) [@citesAsSourceDocument:FederatedAGARepo]. Event information is available at the [MedHackathon Asia 2026 website](https://medhackathon.github.io/2026/) [@citesAsSourceDocument:MedHackathon2026Web]. No new primary human datasets were generated for this report.

# Acknowledgements

We thank MedHackathon Asia 2026 organizers and PRECISE for hosting the meeting in Singapore, and all participants in the Federated AGA / data-sharing governance discussions. This report describes work developed and advanced at MedHackathon Asia 2026. Author affiliations and ORCID identifiers should be confirmed by all co-authors before BioHackrXiv submission; affiliations listed here are provisional based on meeting participation.

# References
