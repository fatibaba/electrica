# Technical Evaluation of ELECTRICA with Competency Questions

We designed a set of competency questions to ensure that the ELECTRICA ontology covers all the concepts needed to describe fractures, their characteristics, and associated patient and family history. These concepts model the data elements of the knowledge base that contains data on paediatric fractures and suspected child abuse cases. This evaluation aims to check that the necessary data elements required by the ELECTRICA ontology are adequately represented.

We present the competency questions in the table below along with the expected responses:

| Competency Question  | Expected Answer |
| --- | --- |
| CQ1. What is the specific location of a fracture in a child? | Location of the fracture (e.g., Fracture of the left femur, Fracture of the anterior arch of c1) |
| CQ2. What is the characteristic of a given fracture? | Type of fracture (e.g., buckle fracture (torus fracture), greenstick fracture) |
| CQ3. What is the age of the fracture as determined by radiological analysis? | Age of the fracture (e.g., 0-2 weeks, 2-4 weeks) |
| CQ4. What are the characteristics of the fracture healing process? | Healing characteristics (e.g., lamellar bridging bone of hard callus) |
| CQ5. Is a given fracture compatible with the reported history of injury? | Boolean value (True/False) |
| CQ6. Is the family known to social services? | Boolean value (True/False) |
| CQ7. What pre-existing medical conditions does the patient have? | Pre-existing conditions (e.g., osteogenesis imperfecta) |
| CQ8. What is the outcome of investigation for a given case? | Outcome of investigation (e.g., accidental injury, inflicted injury) |

As an example dataset for this evaluation, we obtained data from several paediatric radiology reports. We collected the data using Survey Monkey, then used a Python script to convert it into RDF format and annotated it with the ontology classes. Due to the sensitive nature of the data, it is not publicly available. However, if you require access or have any inquiries, please contact the maintainers or submit an issue on GitHub as needed. We used a local installation of Apache Jena Fuseki server to run the SPARQL queries. Instructions on how to install and use the Apache Jena Fuseki server can be found [here](https://jena.apache.org/documentation/fuseki2/). The SPARQL queries we designed to represent the competency questions and some sample results we obtained by running the queries are presented below. Initial iterations identified missing concepts which were added subsequently, and redundant or overly complex concepts were simplified.


## SPARQL Queries and Answers

1. **What is the specific location of a fracture in a child?**

We designed this SPARQL query to find the specific bone location of a fracture. Since the fracture classes are modelled based on the bone location, the label of the class of fracture will show the location.

```sparql
PREFIX rdfs: <http://www.w3.org/2000/01/rdf-schema#>
PREFIX rdf: <http://www.w3.org/1999/02/22-rdf-syntax-ns#>

SELECT DISTINCT ?fractureLocation
WHERE {
  ?fracture rdf:type ?fractureType.
  ?fractureType rdfs:label ?fractureLocation.
}
```
**Answer:**

| "fractureLocation" |
| --- |
| "Fracture of the right temporal bone" |
| "Fracture of the left parietal bone" |

2. **What is the characteristic of a given fracture?**

```sparql
PREFIX rdfs: <http://www.w3.org/2000/01/rdf-schema#>

SELECT DISTINCT ?fractureType
WHERE {
  ?fracture ?hasFractureCharacteristic ?fractureType.
  ?hasFractureCharacteristic rdfs:label "hasFractureCharacteristic"
}
```
**Answer:**

| "fractureType" |
| --- |
| "buckle fracture (torus fracture)" |
| "Greenstick fracture" |
| "Transverse fracture" |

3. **What is the age of the fracture as determined by radiological analysis?**

```sparql
PREFIX rdfs: <http://www.w3.org/2000/01/rdf-schema#>

SELECT DISTINCT ?fractureAge
WHERE {
  ?fracture ?showsRadiologicalDating ?fractureAge.
  ?showsRadiologicalDating rdfs:label "showsRadiologicalDating".
}
```
**Answer:**

| "fractureAge" |
| --- |
| "0 - 2 weeks" |
| "2 - 4 weeks" |

4. **What are the characteristics of the fracture healing process?**

```sparql
PREFIX rdfs: <http://www.w3.org/2000/01/rdf-schema#>

SELECT DISTINCT ?healingCharacteristic
WHERE {
  ?fracture ?showsHealingCharacteristics ?healingCharacteristic.
  ?showsHealingCharacteristics rdfs:label "showsHealingCharacteristic".
}
```
**Answer:**

| "healingCharacteristic" |
| --- |
| "Lamellar bridging bone of hard callus" |
| "Subperiosteal new bone formation" |

5. **Is a given fracture compatible with the reported history of injury?**

```sparql
PREFIX rdfs: <http://www.w3.org/2000/01/rdf-schema#>

SELECT DISTINCT ?compatibility
WHERE {
  ?fracture ?compatibleWithHistory ?compatibility.
  ?compatibleWithHistory rdfs:label "fractureCompatibleWithHistory".
}
```
**Answer:**

| "compatibility" |
| --- |
| "True" |
| "False" |

6. **Is the family known to social services?**

```sparql
PREFIX rdfs: <http://www.w3.org/2000/01/rdf-schema#>

SELECT DISTINCT ?familyHistoryWithSocialServices
WHERE {
  ?patient ?familyKnownToSocialServices ?familyHistoryWithSocialServices.
  ?familyKnownToSocialServices rdfs:label "familyKnownToSocialServices".
}
```
**Answer:**

| "familyHistoryWithSocialServices" |
| --- |
| "True" |
| "False" |

7. **What pre-existing medical conditions does the patient have?**

```sparql
PREFIX rdfs: <http://www.w3.org/2000/01/rdf-schema#>

SELECT DISTINCT ?medicalCondition
WHERE {
  ?patient ?hasPreExistingCondition ?medicalCondition.
  ?hasPreExistingCondition rdfs:label "hasPreExistingCondition".
}
```
**Answer:**

| "medicalCondition" |
| --- |
| "Osteogenesis imperfecta" |

8. **What is the outcome of investigation for a given case?**

```sparql
PREFIX rdfs: <http://www.w3.org/2000/01/rdf-schema#>

SELECT ?investigationOutcome
WHERE {
  ?case ?hasInvestigationOutcome ?investigationOutcome.
  ?hasInvestigationOutcome rdfs:label "hasOutcomeOfInvestigation".
}
```
**Answer:**

| "investigationOutcome" |
| --- |
| "Accidental injury" |
| "Inflicted injury" |
| "Undetermined" |

These SPARQL queries and their results demonstrate that the ELECTRICA ontology effectively captures the necessary concepts to represent paediatric fractures, their characteristics, and associated patient and family history.