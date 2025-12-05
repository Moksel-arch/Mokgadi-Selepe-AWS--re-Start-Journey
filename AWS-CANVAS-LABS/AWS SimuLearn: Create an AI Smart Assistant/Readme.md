# **AWS SimuLearn: Create an AI Smart Assistant**
---
**"Explaination of what has happened here!"**

I followed an **AWS SimuLearn lab** to build a **simple AI Smart Assistant** using **Amazon Bedrock**. 
The goal was to create an intelligent system that could answer HR questions using a knowledge base and also handle a specific task: submitting a **vacation request**.

---

### What I Did 

I successfully set up a full workflow for the AI assistant:

* **Data Preparation (S3 & Handbooks):**
    * I started the lab and accessed the **AWS Console**.
    * I found and inspected the **HR handbook files** (`employee_handbook.txt` and `compensation_handbook.txt`) stored in a dedicated **S3 bucket** (`knowledge-base-bucket-`). This is the raw data the AI needs to learn from.

* **Vector Store Setup (OpenSearch):**
    * I created a serverless collection in **OpenSearch** called `bedrock-knowledge-base`.
    * I set up the index, `bedrock-knowledge-base-index`, within OpenSearch Dashboards. This acts as the vector database, which stores the semantic embeddings of my documents.

* **Building the Knowledge Base (Amazon Bedrock):**
    * I created the **Amazon Bedrock Knowledge Base** named `hr-knowledge-base`.
    * I linked the **S3 bucket** as the data source and the **OpenSearch index** as the vector store.
    * I configured the **Titan Text Embeddings V2** model to process and embed the documents.

* **Creating the Smart Agent (Amazon Bedrock):**
    * I created the main agent, `hr-assistant-agent`, and attached the necessary **Bedrock\_Agent\_Role**.
    * I chose the **Nova Pro model** as the underlying Large Language Model (LLM).
    * I pasted in a customized **prompt** to guide the agent's behavior.

* **Connecting and Testing the Knowledge Base:**
    * I attached the `hr-knowledge-base` to the agent, saved, and prepared it.
    * I successfully tested the agent with simple knowledge-based questions:
        * "What are the standard work hours?"
        * "What is the vacation policy?"

* **Adding an Action Group (Lambda Integration):**
    * I added an **Action Group** named `submit_leave_action`.
    * This action group calls an existing **Lambda function** (`submit_leave`) to handle the vacation request.
    * I defined the three **required parameters** for the action: `employee_name`, `startDate`, and `endDate`.

* **Final Test and Verification:**
    * I prepared the agent again and ran a final **vacation-request test**, which confirmed the agent successfully reported the action's success.
    * I reviewed the `submit_leave` Lambda function's code (`submitLeave.py`), which showed it writes data to a **DynamoDB** table named `VacationTable`.
    * I checked **DynamoDB** and verified that the item the agent added during the test was correctly present in the `VacationTable`.

---

### What I Learned 

* How to **wire S3, OpenSearch, and Bedrock** together to create a functional and intelligent **Knowledge Base**.
* The process of creating and configuring an **Amazon Bedrock Agent** and linking it to a **vector store**.
* Using **Lambda Action Groups** to seamlessly extend the agent’s capabilities beyond just answering questions (i.e., enabling it to *take action*).
* Simple testing of an AI assistant and verifying its results in a persistent data store like **DynamoDB**.

---

### Next Steps 

* **Data Expansion:** Add more documents to the knowledge base for broader HR coverage (e.g., benefits, training, etc.).
* **Capability Expansion:** Expand the action groups for other HR tasks (e.g., benefits enrollment, expense reporting).
* **Refinement:** Fine-tune the Bedrock model if needed for better conversational flow and response accuracy.

Feel free to explore the code and let me know if anything’s unclear!
