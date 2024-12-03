# Group 30 AI Studio Project: Knowledge graph from recent depression & anxiety research | Brightside Health
- Authors: <a href="https://github.com/itsnotleilani" target="_blank">Leilani Isabella Titus</a> | <a href="https://github.com/camilasalinasc" target="_blank">Camila Salinas Camacho</a> |
<a href="https://github.com/juhimanishjain" target="_blank">Juhi Manish Jain</a>

## Project Overview, Objectives, and Goals

This project focuses on creating a knowledge base from up-to-date clinical research papers related to depression and anxiety. The goal was to build a knowledge graph on top of a LLM in order to retrieve more accurate and consistent information from clinical research papers. This structure will allow for more efficient clinical decision-making and better treatment for patients at BrightSide Health.

## Methodology

- **Dataset Description**

   We were given 3 clinical research papers by BrightSide Health. 

- **Approach**

  We selected 2 main models to explore throughout our AI Studio project.

    - **Schema-based** - we selected this model because of its rigid structure and consistency
     - **Free-form** - we selected this model because of its ability to come to unique connections

## Results and Key Findings:

- **Schema-Based Approach**

  The schema-based method resulted in a highly structured and consistent knowledge graph. By defining specific entities (e.g., treatments, symptoms) and relationships (e.g., treats, causes) beforehand, the LLM could focus on extracting relevant connections aligned with our goals. This approach significantly reduced noise and ensured that the extracted triplets were both accurate and meaningful.

- **Free-Form Approach**

  In contrast, the free-form method allowed the LLM to interpret relationships without any predefined guidance. While this added flexibility, it also introduced inconsistencies and irrelevant connections. The lack of structure made it harder to derive actionable insights, as the relationships were often loosely defined or unrelated to the domain-specific knowledge we aimed to capture.

- **Human-in-the-loop Cross-Checking**

  To ensure the accuracy of the extracted relationships, we employed a human-in-the-loop process. Team members manually reviewed the outputs from the model, cross-referencing them with insights from the original research papers. This step not only helped refine the knowledge graph but also reinforced its credibility by validating the extracted data against authoritative sources.

- _**Key Takeaway**_

  The schema-based approach proved to be more effective for our use case, providing structured, domain-specific insights that were aligned with our project’s objectives. While the free-form approach has potential for exploratory analysis, its lack of focus made it less suitable for building a reliable knowledge graph in this context.

## Potential Next Steps

We would eventually like to expand the project by incorporating additional research papers in order to create a more comprehensive knowledge base. And to expand on that, we would also like to create an interface for users to interact with the data visualization. This would allow users who are not as technologically advanced to be able to interact with our knowledge base. Finally, we would also like to refine our methods that we use to extract the nodes and relationships for our knowledge graph, possibly branching out to different types of extraction models, or retrieval methods.


# Directory Structure
```
.
├── clinical-papers                    # Dataset - Research papers
├── important-resources                # Resources and helper files used to create our project
├── Group_30_Brightside_Health.ipynb   # Google Colab Notebook used to develop the Knowledge Graph
├── README.md
└── requirements.txt                   # Requirements and specific version to run our code
```

## Installation

**Prerequisites:**
- Python 3
- Jupyter Notebook Environment
- Required Python libraries (listed in requirements.txt)

**Steps:**

1. _Clone the Repository:_

```bash 
git clone https://github.com/camilasalinasc/Group-30-Brightside-Health.git cd Group-30-Brightside-Health.git

```
  
2. _Install Dependencies_

   Install the necessary Python libraries using pip:

```bash
pip install openai llama_index pyvis
```

3. _Run on Google Colab:_

   - Upload the repository files to Google Drive.
   
   - Open the Colab notebook from Google Drive.
   
   - Ensure you have authorized Colab to access your Drive.

4. _Run the Code:_
	
   Execute the cells in the provided Google Colab notebook step-by-step.

## Credits and Acknowledgments

Today marks the launch of our project, and we are truly excited to share this milestone. Over the past 10 weeks, we have gained invaluable insights and skills, thanks to the incredible support and expertise of everyone at BrightSide Health. We are especially grateful to our Challenge Advisor, Andrew, and all our teammates—Cami, Juhi, and Leilani—for fostering such a collaborative and enriching environment. It has been a privilege to work and learn alongside such talented individuals.


We would also like to extend my heartfelt thanks to Break Through Tech and the Cornell Tech AI Program team for designing such an impactful program. We have already gained so much from this experience, and are eager to see what exciting developments the Spring AI Studio will bring.
