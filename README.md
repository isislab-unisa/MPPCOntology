# Screenia Medieval Philosophy Ontology

This repository contains the ontology designed for the **Screenia** platform, a role-based digital archive developed by **ISISLab** and the **Department of Cultural Heritage Sciences (DiSPaC)** at the **University of Salerno (Unisa)**. 

The ontology aims to support the digital preservation, sharing, tagging, and collaborative commenting of medieval philosophy texts.

## Project Overview

The core purpose of this ontology is to formalize the domain of medieval philosophy publications and user interactions within the Screenia platform. It structures how literary works are organized, how comments are created and tracked, and how collaborative discussions are managed among scholars.

To ensure alignment with established semantic web standards, the ontology is built using **OWL (Web Ontology Language)** and integrates several widely accepted foundational models.

## Ontology Architecture & Reused Ontologies

Rather than building the vocabulary from scratch, the design reuses standardized ontologies to model specific aspects of the domain:

*   **FRBR (Functional Requirements for Bibliographic Records):** Used to represent literary works and their structural hierarchies (Work, Expression, Manifestation, and Item).
*   **CIDOC-CRM (Conceptual Reference Model):** Serves as the overarching framework for modeling actors (authors), commenting events, tags, and discussion rooms.
*   **CO (Collections Ontology):** Utilized to represent ordered structures such as the sequence of books, chapters, and paragraphs.
*   **MOAT (Meaning Of A Tag):** Integrated to handle tagging as an activity rather than a flat string, allowing tags to be linked to context-dependent meanings (accounting for language, historical period, or user interpretation).

---

## Sub-Ontologies

The system is modularized into several logical sub-ontologies:

### 1. Work (Opera) Sub-Ontology
Aligned with **FRBR**, this module organizes texts into a hierarchy of:
$$\text{Work} \longrightarrow \text{Edition} \longrightarrow \text{Book} \longrightarrow \text{Chapter} \longrightarrow \text{Paragraph}$$
The paragraph is designated as the primary "commentable unit". It also includes the `EditionAssignment` entity to document how a specific edition is attributed to a work.

### 2. Comment Sub-Ontology
Models the process and structure of user commentary through three primary components:
*   **Comment:** The actual rich-text content written by an authorized user.
*   **Linking Text (References):** Captures references made within a comment to other books, editions, chapters, paragraphs, or other comments.
*   **Commenting Event:** A dedicated class (`CommentingEvent`) that captures the contextual metadata of a comment (e.g., timestamp, author, and paragraph range) and links to a `historyLog` to track revisions.

### 3. Tagging Sub-Ontology
Instead of using tags as simple text strings, this module models tagging as an *activity* (`RestrictedTagging`). Using **MOAT**, it records:
*   The agent (commenter).
*   The related commenting event that justifies the tag.
*   The targeted paragraph.
*   The disambiliated meaning of the tag (`moat:meaning`).

### 4. Discussion Room Sub-Ontology
Enables interactive discussion around comments. Each comment can be associated with a `DiscussionRoom` where user contributions are structured as `Message` entities, preserving the role of participants (e.g., administrator, commenter, reader).

### 5. Author Sub-Ontology
Recognizing that biographical details of medieval authors are often subject to scholarly debate, this sub-ontology models birth and death events with varying degrees of certainty. By using `Statement` and `AuthorAssignment` entities, the system can capture the reliability, context, and arguments supporting different historical assertions.

---

## Core Requirements Addressed
The ontology is designed to satisfy the following platform requirements:
1. Every Work has at least one Edition.
2. Structure: Work $\rightarrow$ Edition $\rightarrow$ Book(s) $\rightarrow$ Chapter(s) $\rightarrow$ Paragraph(s).
3. Defined user roles: Administrator, Commenter, Reader.
4. Comments are linked to one or more paragraphs of the same work.
5. Support for a single tag per comment, justified within the text.
6. Editable comments with access to historical modifications.
7. Interactive discussion rooms associated with comments.
8. Support for internal references (to other parts of the text) and external references.
9. Support for rich-text comments.

## Next Steps
The current design is being presented to domain experts in philosophy and ontology engineering (with a focus on CIDOC-CRM) to gather feedback. An evaluation questionnaire will be used to assess the ontology against the platform's requirements and the correct application of reused semantic models.

## Contributors & Credits
*   **Presenter / Developer:** Francesco Monzillo
*   **Advisor:** Prof. Vittorio Scarano
*   **Supervisor:** Prof. Maria Angela Pellegrino
*   **Research Lab:** ISISLab, Department of Cultural Heritage Sciences (DiSPaC), Università degli Studi di Salerno
