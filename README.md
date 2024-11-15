## **Dataset Description**
The **Abstract2Appendix v1** dataset is a high-quality collection of academic peer reviews and their associated research paper metadata. This dataset combines reviews from four premier machine learning and AI conferences: **NeurIPS 2023**, **EMNLP 2023**, **TMLR**, and **ICLR 2023**, shuffled into a unified corpus. It is designed to enhance long-context capabilities in Large Language Models (LLMs) and supports tasks such as fine-tuning, zero-shot evaluation, and benchmarking.

Arxiv paper: 
https://arxiv.org/abs/2411.05232


Huggingface dataset link: 
https://huggingface.co/datasets/alexshengzhili/Abstract2Appendix_v1_10k


### **Key Features**
- **Diverse Sources:** Reviews aggregated from leading AI conferences, ensuring comprehensive representation of modern machine learning research.
- **High-Quality Aggregation:** Reviews were aggregated using advanced techniques, capturing the most detailed and constructive feedback.
- **Rich Metadata:** Each review is paired with the corresponding paper title and abstract, providing valuable context for training models.
- **Long-Context Capability:** Designed for tasks that require handling extensive textual input, such as document-grounded question answering and summarization.

---

## **Dataset Summary**
| **Feature**                | **Description**                                                                 |
|----------------------------|---------------------------------------------------------------------------------|
| **Sources**                | NeurIPS 2023, EMNLP 2023, TMLR, ICLR 2023                                      |
| **Volume**                 | 10K in total                                                   |
| **Average Token Count**    | ~26,353 tokens per paper-review pair                                           |
| **Aggregation Technique**  | Grounded on all human review                                                 |
| **Applications**           | Fine-tuning, zero-shot evaluation, benchmarking long-context comprehension     |

---

## **Dataset Construction**

### **1. Source Collection**
Reviews and metadata were sourced from publicly accessible repositories of NeurIPS, EMNLP, TMLR, and ICLR conferences. Each paper typically had 3-6 reviews.

### **2. Document Parsing**
- Papers and reviews were extracted from PDFs using **Amazon Textract**.

### **3. Aggregated Review Creation**
- **GPT-4** was used to combine multiple reviews for each paper into a coherent aggregated, preference data
- Instructions ensured no hallucination or reliance on external knowledge.

### **4. Cleaning and Filtering**
- Outliers exceeding 33,000 tokens were excluded to maintain compatibility with downstream tasks.
- If there are no signficiant difference among the multiple human reviewer, the entry is deleted for clear prefernce clearning 

### **5. Shuffling and Merging**
- Reviews from all conferences were shuffled and merged into a balanced dataset, ensuring representation across diverse topics.

### **6. Validation**
- Aggregated reviews underwent quality checks using human evaluation and LLM-based assessments.

### **7. Transformation for Fine-Tuning**
- Structured for **Direct Preference Optimization (DPO)** and **Supervised Fine-Tuning (SFT)**:
  - Aggregated, preferred reviews labeled as "preferred" responses.
  - Lowest-rated reviews labeled as "rejected" examples for DPO.
  - We include the score for each origional review, if you intend to do DPO/SFT on origional human reviews. 

---

## **Applications**
- **LLM Fine-Tuning:** Ideal for enhancing models' long-context understanding.
- **Zero-Shot Benchmarks:** Test model performance on document-grounded tasks.
- **Evaluation Frameworks:** Benchmark DPO and SFT methods as demonstrated in the paper ["Abstract2Appendix"](https://arxiv.org/abs/2411.05232).

---

## **Data Structure**

### **Other metadata**
- `review`: Aggregated peer review text.
- `paper_title`: Title of the associated paper.
- `abstract`: Abstract of the associated paper.
- `metadata`: Includes conference name, year, and review rating.



## **Usage Notes**

### **Licensing**
The dataset should be used for academic and research purposes

### **Citation**
```
@misc{li2024abstract2appendixacademicreviewsenhance,
      title={Abstract2Appendix: Academic Reviews Enhance LLM Long-Context Capabilities}, 
      author={Shengzhi Li and Kittipat Kampa and Rongyu Lin and Bohang Li and Shichao Pei},
      year={2024},
      eprint={2411.05232},
      archivePrefix={arXiv},
      primaryClass={cs.CL},
      url={https://arxiv.org/abs/2411.05232}, 
}
```
