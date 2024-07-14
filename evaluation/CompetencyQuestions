# Technical Evaluation of ELECTRICA with Competency Questions

We designed a set of competency questions to ensure that the ELECTRICA ontology covers all the concepts needed to describe fractures, their characteristics, and associated patient and family history. These concepts model the data elements of the knowledge base that contains data on paediatric fractures and suspected child abuse cases. This evaluation aims to check that the necessary data elements required by the ELECTRICA ontology are adequately represented.

We present the competency questions in the table below along with the expected responses:

| Competency Question  | Expected Answer |
| --- | --- |
| CQ1. What is the specific location of a fracture in a child? | Location of the fracture (e.g., left femur, right temporal bone) |
| CQ2. What is the type of a given fracture? | Type of fracture (e.g., buckle, greenstick, transverse) |
| CQ3. What is the age of the fracture as determined by radiological analysis? | Age of the fracture (e.g., 0-2 weeks, 2-4 weeks) |
| CQ4. What are the characteristics of the fracture healing process? | Healing characteristics (e.g., lamellar bridging bone of hard callus) |
| CQ5. Is the fracture compatible with the reported history of injury? | Boolean value (True/False) |
| CQ6. What are the details of the patient’s family history relevant to the injury? | Family history details (e.g., family known to social services) |
| CQ7. What pre-existing medical conditions does the patient have? | Pre-existing conditions (e.g., osteogenesis imperfecta) |
| CQ8. What radiological findings are associated with the fracture? | Radiological findings (e.g., periosteal reaction, sutural diastasis) |

As an example dataset for this evaluation, we obtained data from several paediatric radiology reports. We collected the data using Survey Monkey, then used a Python script to convert it into RDF format and annotated it with the ontology classes. The complete dataset is available in [electrica-dataset.ttl](https://github.com/fatibaba/electrica/electrica-dataset.ttl). We used a local installation of Apache Jena Fuseki server to run the SPARQL queries. Instructions on how to install and use the Apache Jena Fuseki server can be found [here](https://jena.apache.org/documentation/fuseki2/). The SPARQL queries we designed to represent the competency questions and the results we obtained by running the queries are presented below. Initial iterations identified missing concepts which were added subsequently, and redundant or overly complex concepts were simplified.

## SPARQL Queries and Answers

1. **What is the specific location of a fracture in a child?**

We designed this SPARQL query to find the specific location of a fracture. The result shows the locations of the fractures identified in the sample dataset.

```sparql
PREFIX rdfs: <http://www.w3.org/2000/01/rdf-schema#>

SELECT DISTINCT ?fractureLocation
WHERE {
  ?fracture rdfs:label ?fractureLocation.
  ?fracture a <http://purl.org/electrica#Fracture>.
}
**Answer:**

| "fractureLocation" |
| --- |
| "Fracture of the left femur" |
| "Fracture of the right temporal bone" |
| "Fracture of the left parietal bone" |

2. **What is the type of a given fracture?**

```sparql
PREFIX rdfs: <http://www.w3.org/2000/01/rdf-schema#>

SELECT DISTINCT ?fractureType
WHERE {
  ?fracture rdfs:label ?fractureType.
  ?fracture a <http://purl.org/electrica#FractureCharacteristic>.
}
**Answer:**

| "fractureType" |
| --- |
| "Buckle fracture" |
| "Greenstick fracture" |
| "Transverse fracture" |

3. **What is the age of the fracture as determined by radiological analysis?**

```sparql
PREFIX rdfs: <http://www.w3.org/2000/01/rdf-schema#>

SELECT DISTINCT ?fractureAge
WHERE {
  ?fracture rdfs:label ?fractureAge.
  ?fracture a <http://purl.org/electrica#RadiologicalDatingOfFracture>.
}
**Answer:**

| "fractureAge" |
| --- |
| "0-2 weeks" |
| "2-4 weeks" |
| "Beyond 4 weeks" |

4. **What are the characteristics of the fracture healing process?**

```sparql
PREFIX rdfs: <http://www.w3.org/2000/01/rdf-schema#>

SELECT DISTINCT ?healingCharacteristic
WHERE {
  ?fracture rdfs:label ?healingCharacteristic.
  ?fracture a <http://purl.org/electrica#FractureHealingCharacteristic>.
}
**Answer:**

| "healingCharacteristic" |
| --- |
| "Lamellar bridging bone of hard callus" |
| "Subperiosteal new bone formation" |

5. **Is the fracture compatible with the reported history of injury?**

```sparql
PREFIX rdfs: <http://www.w3.org/2000/01/rdf-schema#>

SELECT DISTINCT ?compatibility
WHERE {
  ?fracture ?compatibleWithHistory ?compatibility.
  ?compatibleWithHistory rdfs:label "fractureCompatibleWithHistory".
}
**Answer:**

| "compatibility" |
| --- |
| "True" |
| "False" |

6. **What are the details of the patient’s family history relevant to the injury?**

```sparql
PREFIX rdfs: <http://www.w3.org/2000/01/rdf-schema#>

SELECT DISTINCT ?familyHistory
WHERE {
  ?patient ?hasFamilyHistory ?familyHistory.
  ?hasFamilyHistory rdfs:label "familyKnownToSocialServices".
}
**Answer:**

| "familyHistory" |
| --- |
| "Family known to social services" |

7. **What pre-existing medical conditions does the patient have?**

```sparql
PREFIX rdfs: <http://www.w3.org/2000/01/rdf-schema#>

SELECT DISTINCT ?medicalCondition
WHERE {
  ?patient ?hasPreExistingCondition ?medicalCondition.
  ?medicalCondition a <http://purl.org/electrica#Disorder>.
}
**Answer:**

| "medicalCondition" |
| --- |
| "Osteogenesis imperfecta" |

8. **What radiological findings are associated with the fracture?**

```sparql
PREFIX rdfs: <http://www.w3.org/2000/01/rdf-schema#>

SELECT DISTINCT ?radiologicalFinding
WHERE {
  ?fracture ?hasRadiologicalFinding ?radiologicalFinding.
  ?radiologicalFinding a <http://purl.org/electrica#RadiologicalFinding>.
}
**Answer:**

| "radiologicalFinding" |
| --- |
| "Periosteal reaction" |
| "Sutural diastasis" |

These SPARQL queries and their results demonstrate that the ELECTRICA ontology effectively captures the necessary concepts to represent paediatric fractures, their characteristics, and associated patient and family history.
