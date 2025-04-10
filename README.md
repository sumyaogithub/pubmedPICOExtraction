
# Datasets  
This experiment uses three datasets:

### (1) EBM-NLP  
Currently one of the most important datasets for PICO element recognition. It contains titles and abstracts from 4,993 randomized controlled trial (RCT) publications across various fields such as endocrinology, gynecology, neurology, orthopedics, pediatrics, and thoracic surgery. Annotations include "population", "intervention/comparison", and "outcome", as well as finer-grained named entity recognition. The dataset was labeled using a combination of expert and non-expert annotations. In this dataset, **intervention** and **comparison** are merged into a single category. The inter-annotator agreement (Cohen’s kappa) for expert annotations ranges from **0.62 to 0.71**.  
- **Dataset Link**: [https://github.com/bepnye/EBM-NLP](https://github.com/bepnye/EBM-NLP)  
- **Citation**:  
  Nye, B., Li, J. J., Patel, R., Yang, Y., Marshall, I., Nenkova, A., & Wallace, B. (2018). *A Corpus with Multi-Level Annotations of Patients, Interventions and Outcomes to Support Language Processing for Medical Literature*. ACL 2018. [DOI](https://doi.org/10.18653/v1/P18-1019)

### (2) Section-Specific  
A recent dataset used in advanced PICO extraction research. It contains 800 publication titles and abstracts sourced from EBM-NLP, Alzheimer’s Disease (AD), and COVID-19 literature. Annotations include **population, intervention, comparator,** and **outcomes**, along with finer-grained categorization. Sentences are primarily drawn from structured and unstructured "Methods" sections of abstracts. The overall Cohen’s kappa for PICO elements is **0.746**.  
- **Dataset Link**: [https://github.com/BIDS-Xu-Lab/section_specific_annotation_of_PICO](https://github.com/BIDS-Xu-Lab/section_specific_annotation_of_PICO)  
- **Citation**:  
  Hu, Y., Keloth, V. K., Raja, K., Chen, Y., & Xu, H. (2023). *Towards precise PICO extraction from abstracts of randomized controlled trials using a section-specific learning approach*. Bioinformatics, 39(9), btad542. [DOI](https://doi.org/10.1093/bioinformatics/btad542)

### (3) PICO-Corpus  
A newer dataset focusing on PICO extraction. It includes abstracts of 1,011 breast cancer-related RCT publications indexed in PubMed. Annotations cover **population, intervention, comparator,** and **outcomes**, with a total of 26 subcategories. Annotators included professional annotators and authors. Cohen’s kappa for agreement is **0.72**.  
- **Dataset Link**: [https://github.com/sociocom/PICO-Corpus](https://github.com/sociocom/PICO-Corpus)  
- **Citation**:  
  Faith Mutinda, Kongmeng Liew, Shuntaro Yada, Shoko Wakamiya, & Eiji Aramaki. (2022). *PICO corpus: A publicly available corpus to support automatic data extraction from biomedical literature*. WIESP 2022. [ACL Anthology](https://aclanthology.org/2022.wiesp-1.4.pdf)

---

# Data Retrieval Source  
- **Clinical Trials Registry**: [https://clinicaltrials.gov/](https://clinicaltrials.gov/)

# Knowledge Injection Sources (Annotation Guidelines)  
- **EBM-NLP**:  
  - Resource: [Appendix PDF](https://pmc.ncbi.nlm.nih.gov/articles/instance/6174533/bin/NIHMS988059-supplement-Appendix.pdf)  of the paper
  - Mentioned in: Supplementary Appendix  
- **Section-Specific**:  
  - Resource: [GitHub](https://github.com/BIDS-Xu-Lab/section_specific_annotation_of_PICO)  
  - Mentioned in: GitHub page  
- **PICO-Corpus**:  
  - Resource: [Annotation Process – Section 3.2](https://aclanthology.org/2022.wiesp-1.4.pdf)  
  - Mentioned in: Paper, Section 3.2

---

# Data Mining

## Data Preprocessing
- **sectionspecific_titles_humanfindPMID.xlsx**: Manual review of annotated content from Section-Specific dataset with manually identified PMIDs.
- **1.ChangeFormat_3datasets.ipynb**: Converts all three datasets into a unified JSON format based on PICO or PIO top-level ontology.
- **dataset_fillnct.ipynb**: Retrieves clinical trial data (NCT entries) and merges them into the dataset.

---

# Modeling

- **RAG.ipynb**: Applies the BM25 algorithm to retrieve the most relevant abstract sentences from clinicaltrials.gov that align with PICO or PIO ontology.
- **chatgpt.py**: Utilizes ChatGPT-3.5 and 4o for retrieval-augmented generation (RAG) and knowledge injection.
- **unlosth_aug_mistral_llama.py**: Leverages open-source models Mistral and LLAMA3 for RAG and knowledge injection.

---

# Evaluation

- **assess.py**: Evaluation functions and metrics.
