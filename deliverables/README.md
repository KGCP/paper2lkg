## Abstract

**Title**: Local Knowledge Graph Construction from Academic Documents using Large Language Models

**Keywords**: Knowledge Graph Construction, Natural Language Processing, Large Language Model

**Type**: Honours Research Project

**Weight**: 24 Units (50% of Honours year)

**Duration**: Feb 2024 – Nov 2024 

**Course Name**: [COMP4550](https://programsandcourses.anu.edu.au/2024/course/comp4550) – Computing Research Project

**Final Mark**: 90 / 100

**Supervisors**: [Sergio José Rodríguez Méndez](https://researchportalplus.anu.edu.au/en/persons/sergio-rodriguez-mendez/), [Pouya Ghiasnezhad Omran](https://comp.anu.edu.au/people/pouya-ghiasnezhad-omran/)

**Deliverables**: [thesis](https://github.com/KGCP/paper2lkg/blob/master/deliverables/thesis-ver.2024.11.18.pdf), [poster](https://github.com/KGCP/paper2lkg/blob/master/deliverables/poster-ver.2024.11.18.pdf), [code](https://github.com/KGCP/paper2lkg), [published paper](https://dl.acm.org/doi/10.1145/3701716.3717820), [presentation](https://github.com/KGCP/paper2lkg/tree/master/deliverables/2025-www-presentation)

**Description**:
- This project has developed an agentic Knowledge Graph Construction (KGC) pipeline to transform unstructured academic text documents into their structured local Knowledge Graphs (KGs) representations, via Entity Recognition, Entity Linking, Relation Extraction, and Schema Generation.
- Local KGs can facilitate Graph-RAG for knowledge assistance and themselves be integrated into a global academic KG.
- Traditional deep learning methods for local KGC from text rely heavily on training on limited datasets, which makes it difficult to capture diverse, long-tail entities and relations in deployment.
- The project specifically addresses the issues by leveraging the more adaptable Generative Language Model and In-Context Learning methods.
- The project has proposed two novel evaluation setups for KGC tasks on unlabelled datasets. (1) One is to build an external RAG agent to assess the output KG quality through question answering about the original document by visiting the KG only. (2) The second is to build a reverse pipeline from a KC to a synthesised document and compare it with the original document.
- Evaluation shows a relatively high output KG quality, with the flexibility and ability to capture the overall ideas of documents. The model has achieved a similarity score of 0.85-0.88 for the RAG test and 0.9 for the reverse engineering test when comparing with pseudo-ground-truth labels on a customised dataset. 
- Future work includes improving detailed triple accuracy, KG conciseness, and pipeline efficiency.

**Publication**:
- **Haoting Chen**, Sergio José Rodríguez Méndez, and Pouya Ghiasnezhad Omran. 2025. *Open Local Knowledge Graph Construction from Academic Papers Using Generative Large Language Models*. In **Companion Proceedings of the ACM on Web Conference 2025 (WWW '25)**. Association for Computing Machinery, New York, NY, USA, 2551–2559. https://doi.org/10.1145/3701716.3717820
About Publication:
- The paper for this project was accepted for the 4th International Workshop on Natural Language Processing for Knowledge Graph Creation (NLP4KGC), held in conjunction with The 2025 Web Conference, and was published in the ACM library. The paper covers most of the original honours research outputs, with additional experiments. Haoting Chen, the **primary author**, was responsible for programming, manuscript drafting and editing. The coauthors, who were also the supervisors, provided high-level guidance for this publication. During The 2025 Web Conference, Haoting Chen delivered an **oral presentation** about the research findings at the NLP4KGC workshop.
