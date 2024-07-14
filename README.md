## ELECTRICA Ontology

Welcome to the ELECTRICA Ontology GitHub repository! This repository contains the resources and documentation for the ELECTRICA ontology, designed to describe data for ELEctronic tool for Clinicians, Teachers and Researchers In Child Abuse. The aim of the ontology is to standardise and facilitate the organisation, integration, and analysis of data related to pediatric fractures and potential child abuse cases.

### Table of Contents
- [Overview](#overview)
- [Usage](#usage)
- [Ontology Structure](#ontology-structure)
- [Evaluation](#evaluation)
- [Contact](#contact)

### Overview
The ELECTRICA ontology describes concepts from reports of cases of child abuse or suspected child abuse, with a focus on fractures identified from radiological investigations, the characteristics of those fractures, and the family and medical history of the patients. At the time of writing, the ontology includes 1141 classes and 63 properties. 

### Usage

#### Viewing the Ontology
To get started with the ELECTRICA ontology, clone this repository to your local machine:
```bash
git clone https://github.com/fatibaba/electrica.git
```
You will need [Protégé](https://protege.stanford.edu) to view and modify the ontology files.

1. Open Protégé.
2. Load the electrica.owl file from the cloned repository.

#### Access via BioPortal
The ELECTRICA ontology can also be accessed via BioPortal at [ELECTRICA on BioPortal](https://bioportal.bioontology.org/ontologies/ELECTRICA). BioPortal provides built-in functionalities to view and explore the concepts within the ontology. Users can:

1. Browse the ontology's hierarchy to understand its structure.
2. Use the search functionality to find specific classes or properties.
3. Explore detailed information about each concept, including definitions, synonyms, and mappings to other ontologies.
4. Utilise visualisation tools to see the relationships between different concepts.

### Ontology Structure
The ELECTRICA ontology is intricately structured to cover various aspects of cases that record suspicion of inflicted injury, with a particular focus on paediatric fractures. The core classes cover the following areas:

* Detailed classifications of fractures based on location and type.
* Comprehensive documentation of fracture characteristics.
* Integration of radiological findings and healing characteristics.
* Aspects of how paediatric fractures are identified and recorded.
* Other variables like the family and medical history of the patient.

We use the Basic Formal Ontology (BFO) as the upper-level ontology to provide a structured foundation. This choice facilitates the integration of concepts from the Ontology for General Medical Science (OGMS). We also reused classes from SNOMED-CT and are currently working towards better integration with SNOMED-CT. By leveraging these established ontologies, ELECTRICA ensures a robust and interoperable framework, enhancing its utility for clinical data analysis.

For an in-depth look at the ontology structure, refer to the ontology file `electrica.owl` within this repository.

### Evaluation
The evaluation phase of the ELECTRICA ontology involved multiple methods to ensure its accuracy, consistency, and completeness. We engaged in an iterative process with domain experts to refine the ontology based on their feedback. To validate the ontology against the competency questions identified during the specification phase, we added datasets and mapped them to the ontology classes, then ran SPARQL queries on the annotated dataset. We also used the OntOlogy Pitfall Scanner! (OOPS!) to identify potential modelling pitfalls and Pellet and HermiT reasoners to check for logical issues. The results of this evaluation is detailed in the evaluation folder along with the competency questions, SPARQL queries and small sample dataset.

### Contact
For further information or queries, please reach out to the project maintainers:

* Lead Maintainer: [Dr Fatima Maikore](https://www.sheffield.ac.uk/cs/people/academic/fatima-maikore) 
* Domain Expert: [Professor Amaka Offiah](https://www.sheffield.ac.uk/smph/people/clinical-medicine/amaka-offiah)

Issues and suggestions can be submitted via the repository's [Issues section](https://github.com/fatibaba/electrica/issues).


