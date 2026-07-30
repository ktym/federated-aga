# Table 1 Federated genome archive and data-sharing governance

Federated Asian Genome-Phenotype Archive

Since open-access (OA) data can be used as-is, the discussion here focuses on how to discover and access controlled-access (CA) data across Asian countries.

## Background

At MedHackathon Asia 2025, participants recognized that the existence of human research data in each country was not even shared among them.
Under INSDC coordination, dbGaP in the US, EGA in Europe, and JGA in Japan are operated as repositories for human research data associated with publications.
In these repositories, submitted data is assigned an ID that can be cited in publications, and other researchers can apply for reuse.
We considered that a Federated AGA—connecting data across Asian countries through a mechanism similar to the Federated EGA—could promote data utilization within Asia.

- dbGaP: US repository for human research data
  - Description: The database of Genotypes and Phenotypes (dbGaP) was developed to archive and distribute the data and results from studies that have investigated the interaction of genotype and phenotype in humans
  - Searchable by ID, keyword, disease, data type, etc. from https://dbgap.ncbi.nlm.nih.gov/home/
    - 3579 studies, 15541 phenotype datasets, 2122 molecular datasets, 14 DACs?
    - DACs are organized per NIH institute overseeing the research, not per study
- EGA: European repository for human research data
  - Description: The European Genome-phenome Archive (EGA) is a service for permanent archiving and sharing of personally identifiable genetic, phenotypic, and clinical data generated for the purposes of biomedical research projects or in the context of research-focused healthcare systems.
  - Browsable by Studies, Datasets, DACs, Synthetic Data categories, searchable by ID and keyword from https://ega-archive.org/ catalog
    - 9962 studies, 13779 datasets, 3208 DACs
    - Federated EGA is operated in each country; due to country-specific circumstances and per-dataset DACs, contact can sometimes be lost
- JGA: Japanese repository for human research data
  - Description: An enormous amount of human data is being generated with advances in next-generation sequencing and other analytical technologies. We therefore need rules and mechanisms for organizing and storing such data and for effectively utilizing them to make progress in the life sciences. The "NBDC Human Database" promotes the sharing and use of diverse human-derived datasets, balanced with a commitment to protecting personal privacy.
  - Searchable by ID and keyword from https://humandbs.dbcls.jp/
    - 396 studies, 979 datasets, 1 DAC 
    - Single DAC = NBDC human DB (in National Institute of Genetics / Database Division of Life Science)

## Needs

- Catalogue of datasets and DACs related to study in each country
  - If research data from Asian countries is listed and searchable on a common portal, researchers could more easily find and reuse data relevant to their studies, and the visibility of each dataset would be improved.
- Any other ideas?
  - It would be useful to have a system where an AI agent can answer questions like "I want to study xxx—what Asian data is available and where?" by searching the portal and assisting with data access applications.
- Use cases
  - Propose what data access is needed and what procedures/search functionalities are required based on Table 4 discussions

## Challenges

- What metadata should be indexed on the AGA portal site?
  - Is the metadata currently provided by JGA and EGA necessary and sufficient?
    - Search functionality appears insufficient—how can we make it AI-friendly?
  - Is it easy for each country/project to register their data?
    - Cohorts may have thousands of parameters—to what granularity should they be summarized?
    - In the first place, projects like ToMMo could be considered as one project with one dataset
- How to catalog data from cohorts and large-scale national projects?
  - For cohort data like PRECISE and ToMMo, DAC applications by data users resemble studies, and the subset data specified for each purpose could become AGA records in the future

Organizing metadata with common ontologies would likely enable better faceted search.
Standards used by GA4GH and others should be adopted wherever possible.

## TODOs

- How to become a member of Federated AGA
  - Designating a single representative institution per country is not realistic and would take too long
  - From Japan, not only JGA but also independently operated large-scale projects like ToMMo, BBJ, and GeMJ should be able to join individually
- How to navigate researchers to DAC / datasets
  - Human and AI friendly interface
  - Visualize the hierarchical summary of the collection
  - Statistics of data collection by Age, Sex, Diseases, Tissues, Methods, Types of data ...
  - Once a (set of) data is selected, navigate user to DAC for data use application
- How to describe requirements to access each dataset
  - A: requires local collaborator to access data
  - A+: requires A + the local clinician (e.g., in the Thai case)
  - B: accessible from academia only
  - C: accessible by industry
  - D: accessible if PI of the study allows
- Where to host the AGA portal website
  - Start with prototyping on GitHub Pages, etc.
  - Each member institution could host the AGA portal and load-balance
  - If AI is used, required resources will grow, including API billing and GPUs for local LLMs

## Country-specific situations

On 2026-07-29, participants from Japan (JGA, ToMMo, GeMJ), India (IBDC), Thailand, Singapore (PRECISE), and the Philippines discussed the situation in each country.

### Data access modes

Tier 2 and Tier 3 should be discussed here.

- Tier 1: Open access
- Tier 2: Controlled access through DAC
- Tier 3: (Approval of DAC +) A, A+, B, C, D, ...

Whether each country has a submission destination like JGA for Tier 1 data should also be discussed.

### India (Shailesh Kumar)

Project name: IBDC (Indian Biological Data Centre)

- Tier 2: IBDC serves as DAC
  - Data held: normal & cancer human data (genomics & multi-omics)
    - Building an Indian version of GTEx

### Philippines (Francis Tablizo)

Project name: Filipinome (Philippine Genome Center)

- Tier 3: D — Currently only one project exists, and PI approval is required
  - Data held: genomic data, clinical information

### Thailand (Jakris Eu-ahsunthornwattana)

Project name: ??

- Tier 3: A+ for clinical data (collaboration with the clinician involved in the data is required)
  - Data held: Genomic Thailand
  - International access applications: Yes

### Japan (Toshiaki Katayama, Soichi Ogishima, Yosuke Kawai)

Project name: JGA
- Tier 2: DAC
  - Data held: genome, transcriptome, exome, array, spatial transcriptome, and more
  - International access applications: Yes

Project name: ToMMo
- Tier 2: Produces its own data and has its own DAC; DAC members include experts from outside the ToMMo organization
- Tier 3: A — OK if through collaboration with ToMMo researchers
  - Data held: cohort, genome, multi-omics, health information, and more
  - International access applications: Under consideration

Project name: AMED

- Tier 3: D — Many datasets are independently managed by PIs
  - Data held: disease research data
  - International access applications: Case by case

### Singapore (Nicolas Bertin)

Project name: PRECISE

- Tier 2: Applying to TRUST DAC will trigger confirmation with the relevant sub-DACs; direct applications to sub-DACs like PRECISE are also accepted
  - Data held:
    - PRECISE DAC: genomic data, UK Biobank-like data
    - Ministry of Health (MOH) DAC: Selected EHR
	- TRUST DAC: environmental data, traffic data, and more
  - International access applications:

## Day 2

The INSDC centers (NCBI, EMBL-EBI, NIG-DDBJ) operate dbGaP, EGA, and JGA to support researchers in depositing human research data and obtaining IDs for publication, and in making research data accessible long-term (open/controlled).

In contrast, national genome projects and biobanks are themselves data producers, hold their own DACs, and retain large-scale data. Treating an entire large-scale dataset as a single dataset makes search inconvenient, so it is desirable to be able to search by breakdowns. One idea proposed yesterday was: for each data-use application (study) to a DAC, the research purpose and corresponding data become clear, so registering each of those as a separate dataset could be a way forward.

Through various discussions, today's question became: "Where do researchers in Asian countries actually deposit human research data?" → For India, it became clear that IBDC operates INDA-CA.

## Wrap-up slides

### Slide 1

Vision for AGA: a catalog that promotes mutual use of human research data across Asia

* INSDC human research data
  * Open access data
    * SRA (US/NCBI), ENA (EU/EMBL-EBI), DRA (Japan/NIG-DDBJ)
  * Controlled access data
    * dbGaP (US/NCBI), EGA (EU/EMBL-EBI), JGA (Japan/NIG-DDBJ)
  * Upcoming members + CNCB (China), IBDC (India/INDA-CA)

* Biobank human research data
  * Japan: ToMMo, GeMJ, AMED, ...
  * India: GenomeIndia
  * Singapore: PRECISE
  * Thailand: Genomics Thailand
  * Philippines: Filipinome
  * Others: see [MedHackathon 2025 paper](https://doi.org/10.1093/gigascience/giag052) Table 1)


### Slide 2

To design the AGA portal, consider use cases and potential improvements using EGA and others as examples

Typical process for researchers applying for data use
* Find data useful for their research from catalogs such as [Federated EGA](https://ega-archive.org/datasets/)
  * Access the DAC for that data and submit a use application
    * Data access environments vary by provider (TRE, download, etc.)

Challenges
* Catalogs are not particularly human- or AI-friendly
  * Insufficient functionality for breakdowns/distributions of many datasets, faceted search, etc.
    * What metadata should be in the catalog, and what features should the portal provide?
  * With many DACs, applying for multiple datasets becomes cumbersome
    * When a PI also serves as the DAC, contact can be difficult, and future access may become unavailable

The primary function of AGA is to provide an overview of what data exists in each country and in what quantities, enable humans and AI to efficiently find needed data, clarify where to apply for access, and ensure long-term data accessibility.

### Slide 3

Next steps

* Step 1
  * Investigate how many institutions across Asian countries, besides JGA, accept controlled-access research data deposits
    * In India, IBDC operates INDA (equivalent to SRA) and INDA-CA (equivalent to dbGaP); the DAC for the latter is run by IBDC
  * Define a specification for JGA and these organizations to provide research dataset indexes to the AGA portal
    * An API to retrieve the latest list, and a JSON structure containing necessary and sufficient metadata
  * Prototype the AGA portal site, aggregate data from each country via the API, and enable search through tables and visualizations
* Step 2
  * Reconsider how to index datasets from national genome projects and biobanks in AGA, and what metadata is needed for that
    * For example, for ToMMo data in Japan, several approaches are possible: ToMMo joins as an AGA member, or ToMMo data is registered in JGA and listed in the catalog

To this end, we hope to advance collaboration through the September [BioHackathon](https://2026.biohackathon.org/), Zoom meetings, and next year's MedHackathon.
