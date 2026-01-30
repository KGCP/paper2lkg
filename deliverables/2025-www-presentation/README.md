## Script

#### S1:

Hello everyone. In today’s presentation, we are going to introduce our research, Open Local Knowledge Graph Construction from Academic Papers Using Generative Large Language Models. 

#### S2:

The motivation for this research on building local academic KGs comes from the fact that: current academic KGs typically lack a detailed and structured representation of the local knowledge conveyed in each individual paper. For example, as shown on the RHS of the slide, an academic KG usually contains much global or inter-paper knowledge, such as “John Smith is the author of Paper 1”, “Paper 2 references Paper 1”. However, the internal knowledge for each paper is limited. In contrast, a local academic KG is constructed from a single paper only, instead of a large corpus of papers. Therefore, it can focus more on the details about the targeted paper, such as the models it presents and the future work it highlights. Hence, if they are combined, an academic KG can now preserve structured knowledge to a greater extent and enable more complex querying. 

#### S3:

This figure shows a potential application of an academic KG. A person tries to ask a graph-based retrieval augmented generation agent how a concept is mentioned differently across all relevant papers in the academic knowledge base. If local-domain knowledge for each paper is preserved, the generate answer should be more thorough. 

#### S4:

Over time, more and more methods for building local KGs from documents have been developed. In our study, we chose the more recent generative LLM approach. The reason is that generative LLM is simpler and more adaptive. The RHS of the slide shows how Named Entity Recognition is typically performed by LLM encoders and generative LLMs. The use of generative LLMs typically involves writing prompts in human language to guide the LLM to achieve a specific task, such as directly asking GPT to output a list of detected named entities and their entity types from a given sentence, which requires minimal or no training or fine-tuning. On the other hand, the LLM encoder approach typically involves turning the input tokens into embeddings through an LLM encoder, such as BERT, and training a classifier to read the embedding and convert them into human-readable labels, such as a label indicating whether a current position is part of an Entity and what the Entity Type is. However, the main advantage of using generative LLM is not only because it is simple but also adaptive because we don’t need to worry about the domain adaptation problem caused by a limited fine-tuning dataset. For example, a classifier trained to detect PERSON and LOCATION entities may fail to identify ALGORITHM entities. In contrast, we can prompt generative LLMs to output any type of entities in the first place. However, the use of generative LLM can incur a high complexity due to its autoregressive nature, but it is also worth studying its downside. 

#### S5:

Therefore, our goal is to present a pipeline design and its corresponding prototype that can transform individual papers into their local Knowledge Graph representation, by leveraging generative LLMs as much as possible. Briefly discover the efficiency and efficacy of using such a local KGC pipeline that is mostly based on generative LLMs. 

#### S6:

Instead of building the pipeline from scratch, our research utilises the outcome of a preceding work, which has been introduced in the previous talk, that can help us pre-process raw documents into a semi-structured representation called Deep Document Model, which organises the document into a hierarchy of sections, paragraphs, and sentences, along with its metadata. In this way, we can focus more on the main procedure of building knowledge graphs. 

#### S7:

This slide shows the ontology of the input DDM and the output local KG. The output local KG consists of a set of entity nodes with some attributes, and these Entities are related by some predicates. Each Entity has one or more mentions, that is，their specific forms appearing in the document, and each mention is linked to a specific sentence. 

#### S8:

To construct a local KG from a DDM, the pipeline consists of several stages. The Entity Extraction stage finds entity mentions from the document. The Entity Linking stage groups highly similar entity mentions into entity nodes. The Local Relation Extraction stage finds relations between entity nodes within a limited context (e.g., a section, paragraph, or sentence). The Global Relation Extraction stage finds relations that span across the entire document. Finally, The Taxonomy Generation stage involves finding more taxonomical relations between entities & The Predicate Resolution stage involves grouping highly similar predicates. 

#### S9:

To extract entities thoroughly, the program traverses the paper at three different levels: section by section, paragraph by paragraph, and sentence by sentence. It also extracts entity mentions from three different levels, from the narrowest Named Entity Mentions to any Mentions. 

#### S10:

At the beginning of stage 2, an Entity node is constructed from each entity mention, and we assume all entities are distinct. To perform Entity Linking, the program first carefully merges Entities with the same names. Next, the program uses an LLM to generate a short description for each entity based on its context and the LLM’s background knowledge. The descriptions are then embedded, and the entities with highly similar description embeddings are merged， regardless of the difference in their original names. 

#### S11:

For local relation extraction, the program loops through the paper at three different levels, as before, to prompt an LLM to extract relations between the entities found previously. For global relation extraction, the program first summarises the document until it fits the context limit of the LLM. Select the k % most relevant entities and for each pair of significant entities, extract their relations from the shorten document. 

#### S12:

In the taxonomy generation stage, the program first uses generative LLMs to generate descriptions for all entities and several potential parent entities that are guessed by an LLM based on both its background knowledge and the context. If the description of a potential parent of Entity A is found to be highly similar to the description of Entity B，then, we would consider that Entity B is a parent of Entity A. Predication Resolution is mostly similar to the Entity linking step, except that we are merging predicates now instead of entities.

#### S13:

The evaluation comes with two approaches. Both work for unlabelled datasets. Evaluation via Reverse Engineering reconstructs a document from a local KG and compares it with the original document. Evaluation via Application uses an LLM to directly read the whole document and generate question-answer pairs for ground truth. Then, another LLM tries to answer these questions using only the local KG. Finally, their results are compared. The dataset we used for evaluation consist of 10 papers from the ANU academic scholarly knowledge graph and 100 abstract-only paper from the SciERC dataset. However, we acknowledge that these approaches come with limitations. The first major limitation is that the embedding itself is lossy. This means that even if we have two documents with highly similar embeddings, it does not necessarily mean they are similar. Another limitation is that the result is based on the performance of the whole system instead of paper2lkg itself. Even so, it should be a reasonable estimation of the performance, given that we have only the unlabeled datasets.

#### S14:

The result is quite desirable and the performance of the model seems to be consistent across papers of different lengths. However, there is still room for improvement. For example, the outliers on the boxplot on the RHS indicate the graph RAG agent has failed to use the constructed local KGs to answer some questions.  

#### S15:

The complexity of the pipeline is approximately linearly proportional to the paper length, which seems to be acceptable. However, if we look at the yaxis， the actual time of constructing a paper is quite high in a general sense due to the high proportional coefficient because each gemerative LLM call is expensive, which is still a major issue in practice.

#### S16:

In conclusion, our research has presented the paper2lkg pipeline, although it is still experimental. We  found that found that such a pipeline based on generative LLMs may be slow, even though the complexity measure is linear, since every single generative LLM is expensive. Future research can build on this existing framework and present a better LLM-based local academic KGC pipeline with higher output KG quality and lower complexity. Future work may also target the integration of local academic KG into global academic KG.

#### S17:

Now, if you have any questions, please feel free to ask now. 