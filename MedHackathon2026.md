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

### India ()

Project name: IBDC (Indian Biological Data Centre)

- Tier 2: IBDC serves as DAC
  - Data held: normal & cancer human data (genomics & multi-omics)
    - Building an Indian version of GTEx

### Philippines ()

Project name: ?

- Tier 3: D — Currently only one project exists, and PI approval is required
  - Data held: transcriptome

### Thailand (Jakris)

Project name: ??

- Tier 3: A+ for clinical data (collaboration with the clinician involved in the data is required)
  - Data held: Genomic Thailand
  - International access applications: Yes

### Japan (Toshiaki, Soichi, Yosuke)

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

### Singapore (Nicolas)

Project name: PRECISE

- Tier 2: Applying to TRUST DAC will trigger confirmation with the relevant sub-DACs; direct applications to sub-DACs like PRECISE are also accepted
  - Data held:
    - PRECISE DAC: genomic data, UK Biobank-like data
    - Ministry of Health (MOH) DAC: Selected EHR
	- TRUST DAC: environmental data, traffic data, and more
  - International access applications:
