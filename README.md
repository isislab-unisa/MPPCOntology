# MPPCO: An Ontology to Support Screenia

This repository contains the **MPPCO** ontology, designed to support the **Screenia** platform. Screenia is a role-based software platform developed by the **IsisLab** laboratory and the **Department of Cultural Heritage (DiSPaC)** at the **University of Salerno (UNISA)**. It is aimed at the digitization, archiving, tagging, and commenting of medieval philosophy works.

## Project Overview

The MPPCO ontology was developed to formalize the core requirements of the Screenia platform while defining additional entities and characteristics to support domain-specific needs in the medieval philosophy commentary domain.

### Core Requirements Formalized
1. **Work Hierarchy**: Works are composed of one or more editions. Each edition comprises books, chapters, and paragraphs.
2. **User Roles**: Users are assigned roles from the set `{admin, commentator, reader}`.
3. **Granular Commenting**: The paragraph is the primary commentable unit. A single comment can reference multiple paragraphs within the same work.
4. **Justified Tagging**: Comments may contain at most one tag, which should be directly justified within the comment text.
5. **Comment History**: Comments are editable, with the system maintaining a full log of modifications.
6. **Discussion Rooms**: Each comment is associated with a discussion room to track updates and host threads among commentators.
7. **Internal & External References**: Comment text can refer to both internal elements of the work (editions, books, chapters, paragraphs) and external entities.
8. **Rich-text**: Comments support rich-text formatting to allow stylized text.

---

## Ontology Structure

The ontology is modular and divided into four sub-ontologies:

### 1. Opera (Work) Sub-Ontology
* **Reference Model**: Inspired by the **FRBR** (Functional Requirements for Bibliographic Records) ontology.
* **Function**: Facilitates the hierarchical management of works, editions, books, chapters, and paragraphs.

### 2. Comment Sub-Ontology
* **Reference Model**: Aligned with **CIDOC-CRM** (specifically using classes like `E33 Linguistic Object` and `E7 Activity`).
* **Function**: Models commenting as a distinct event (`CommentingEvent`) to consolidate metadata (author, timestamp) and preserve modification history. It utilizes a `linkingText` entity to handle rich-text references to internal and external elements.

### 3. Tag Sub-Ontology
* **Reference Model**: Integrates **CIDOC-CRM** and **MOAT** (Meaning Of A Tag) ontologies.
* **Function**: Moves away from treating tags as simple strings. It models the *activity* of tagging, associating the tagger (agent), the comment, the target paragraph, and the specific contextual meaning of the tag.

### 4. Author Sub-Ontology
* **Reference Model**: Built on **CIDOC-CRM**.
* **Function**: Models historical assertions about authors (such as birth and death events). It incorporates a `Statement` entity to address the potential uncertainty of historical facts that require supporting evidence or arguments.

---

## Evaluation and Feedback

To assess its effectiveness as a reference ontology, the structure was evaluated via a questionnaire by four experts (comprising domain experts in medieval philosophy and ontology/solution modeling experts).

### Key Findings
* **General Reception**: Feedback was generally encouraging, with experts highlighting the clarity and essential nature of the structure.
* **Requirements Coverage**: High ratings were given to the modeling of commenting, editing history, and tagging features.
* **Points for Discussion**:
  * An expert pointed out potential ambiguities in using FRBR classes, specifically regarding the categorization of "Edition" as `frbr:Expression` and "Book" as `frbr:Manifestation`.
  * It was suggested that medieval works could also be categorized based on their varying physical supports (carriers), as physical mediums represent an important variable in medieval scholarship.

---

## Future Directions

* **Performance & Scalability**: Testing the ontology implementation on various metrics, including query performance, efficiency, maintainability, and flexibility.
* **Physical Carrier Modeling**: Exploring options to distinguish and recognize work artifacts based on the physical support or medium on which they are located.

---

## Project Credits

* **Presenter / Developer**: Francesco Monzillo
* **Advisor**: Prof. Vittorio Scarano
* **Supervisor**: Prof. Maria Angela Pellegrino
* **Affiliated Labs**: ISISLab, Department of Cultural Heritage (DiSPaC), University of Salerno
