# **AWS SimuLearn: Create an AI Smart Assistant**

I read the lab goals, hit “Start Lab” (or opened the AWS Console), followed the step‑by‑step instructions using the navigation arrows, and noted that unused AWS services are disabled and the used ones are limited to the lab’s needs.
<img width="1912" height="882" alt="image" src="https://github.com/user-attachments/assets/faa32c1a-078f-48dc-adea-8a64149bef56" />

I typed s3 into the top‑navigation search box.
I clicked S3 under “Services” in the search results.
I moved on to the next step.
<img width="1908" height="879" alt="image" src="https://github.com/user-attachments/assets/8d4fa011-23ed-493a-937c-381d487aa73d" />
<img width="1917" height="877" alt="image" src="https://github.com/user-attachments/assets/1d613d57-85b5-4724-b020-a3334eb9d66e" />

I opened the General purpose buckets tab and clicked the bucket whose name starts with lab-bucket-. Then I moved on to the next step.
<img width="1909" height="869" alt="image" src="https://github.com/user-attachments/assets/8ebf3c69-37c6-48a6-97bc-76b6827de149" />

I checked the box next to agent‑prompt.txt, clicked Open, and the file opened in a new browser tab. I then moved on to the next step.
<img width="1887" height="886" alt="image" src="https://github.com/user-attachments/assets/721a4260-69c2-483c-bc18-4ab92e57379e" />

I selected the agent‑prompt.txt file, copied its contents, and pasted them into a text editor on my device. Then I moved on to the next step.
<img width="1914" height="464" alt="image" src="https://github.com/user-attachments/assets/72b00750-775e-4963-a583-27f70b9a2610" />

I went back to the Amazon S3 console, opened the General purpose buckets tab, and clicked the bucket whose name starts with knowledge-base-bucket-. Then I moved on to the next step.

I opened the Objects tab and saw the list of files—​employee_handbook.txt (used in the current Practice section) and compensation_handbook.txt (used later in the DIY section). I could click either file to review its contents, then I moved on to the next step.
<img width="1908" height="875" alt="image" src="https://github.com/user-attachments/assets/33273e09-87bc-4363-93c2-9e10e50988b4" />

I typed “opensearch” into the top‑navigation search box and clicked Amazon OpenSearch Service under “Services” in the results.
<img width="1919" height="884" alt="image" src="https://github.com/user-attachments/assets/3faa3b8d-aa3a-4abc-8577-c64fa9e3668c" />

I opened the left navigation pane, clicked Collections under Serverless, and then selected the bedrock‑knowledge‑base collection in the Collections section.
<img width="1916" height="881" alt="image" src="https://github.com/user-attachments/assets/d09ffce7-e736-4b2c-b221-119ba5aebe6b" />

<img width="1919" height="881" alt="image" src="https://github.com/user-attachments/assets/d39c079a-4395-4d88-acce-7ffc4cfb66ee" />
<img width="1915" height="396" alt="image" src="https://github.com/user-attachments/assets/01c2c114-1cd6-4ae6-8e03-69f2aa5cb52f" />
<img width="1899" height="875" alt="image" src="https://github.com/user-attachments/assets/d3879931-d425-4d7c-b981-643f51ace792" />

I copied the Collection ARN from the Overview tab, pasted it into a text editor, opened OpenSearch Dashboards, and clicked the Indexes tab before moving on to the next step.
<img width="1910" height="697" alt="image" src="https://github.com/user-attachments/assets/e2a0c158-f2ca-4ee2-9f8b-d2964262b97d" />

I clicked the bedrock‑knowledge‑base‑index under “Index name” and then moved on to the next step.
<img width="1908" height="882" alt="image" src="https://github.com/user-attachments/assets/31f113c9-ae64-4bb6-b891-99fa6e6ff7ad" />

I reviewed the other configurations associated with the vector index and then moved on to the next step
<img width="1913" height="867" alt="image" src="https://github.com/user-attachments/assets/06c530dc-7734-43f2-a966-93dc9b65cf8b" />

I typed “bedrock” into the top navigation bar search box, clicked Amazon Bedrock under Services, and moved on to the next step.
<img width="1909" height="852" alt="image" src="https://github.com/user-attachments/assets/b25464fe-b61a-4d58-851a-3db59a9e7cba" />
<img width="1886" height="874" alt="image" src="https://github.com/user-attachments/assets/70a297b0-a877-404b-b544-09dc54e1dab3" />

I opened the left navigation pane and clicked Knowledge Bases, then on the Knowledge Bases tab I clicked Create, selected “Knowledge Base with vector store”, and moved on to the next step.
<img width="1895" height="877" alt="image" src="https://github.com/user-attachments/assets/80056b9f-b25e-4701-8ec5-cd5f531a0b38" />

I clicked Knowledge Bases in the left navigation pane, hit Create, chose “Knowledge Base with vector store” from the dropdown, and then moved on to the next step.
<img width="1886" height="882" alt="image" src="https://github.com/user-attachments/assets/5561aeef-8732-4bed-ad47-0074458ec630" />
<img width="1898" height="876" alt="image" src="https://github.com/user-attachments/assets/09bc0318-42eb-4a22-af80-72f6717cfb45" />

I typed hr-knowledge-base into the Knowledge Base name field in the “Provide Knowledge Base details” step and then moved on to the next step.
<img width="1891" height="870" alt="image" src="https://github.com/user-attachments/assets/9b70df0d-3917-481a-bfaf-3e08ece013df" />

I chose Use an existing service role, selected Bedrock_KB_Role, set the data source to Amazon S3, scrolled to the bottom, hit Next, and moved on to the next step.
<img width="1904" height="873" alt="image" src="https://github.com/user-attachments/assets/24e901ce-cf5e-498a-a971-e76403b5ffa4" />

I typed hr-data-source as the data source name, clicked Browse S3 for the S3 URI, and then moved on to the next step.
<img width="1898" height="878" alt="image" src="https://github.com/user-attachments/assets/a94b9ddc-1ba1-42b3-a30c-adb62b811c0d" />
<img width="1758" height="554" alt="image" src="https://github.com/user-attachments/assets/a5691727-1700-4dd7-baa8-f4281a715e21" />

I selected the bucket that starts with knowledge‑base‑bucket‑, clicked Choose, scrolled to the bottom of the Configure data source page and hit Next, then moved on to the next step.
<img width="1759" height="542" alt="image" src="https://github.com/user-attachments/assets/47302ea1-b97b-4348-a6b4-92da7557ab5c" />

I clicked Select model for the Embeddings model in the Configure data storage and processing step, then moved on to the next step.
<img width="1897" height="879" alt="image" src="https://github.com/user-attachments/assets/68bea1ca-cfa4-4d8e-854b-1cf0e50d2cb1" />

I chose Titan Text Embeddings V2 from the models list, clicked Apply, and then moved on to the next step.
<img width="1027" height="855" alt="image" src="https://github.com/user-attachments/assets/a3782f2a-a21b-4b1b-892e-75bbfd421ee8" />

I selected Use an existing vector store, chose OpenSearch Serverless as the vector store type, pasted the ARN I’d copied earlier into the Collection ARN field, and typed bedrock-knowledge-base-index for the vector index name.
<img width="1888" height="881" alt="image" src="https://github.com/user-attachments/assets/2126ef89-6b63-4538-aca7-f71d050b0932" />

I entered bedrock-knowledge-base-vector as the Vector field name, AMAZON_BEDROCK_TEXT_CHUNK as the Text field name, and AMAZON_BEDROCK_METADATA as the Bedrock‑managed metadata field name, clicked Next, and moved on to the next step.
<img width="1886" height="871" alt="image" src="https://github.com/user-attachments/assets/86622b73-c27d-496f-8184-3fd756e217f8" />

I scrolled to the bottom of the Review and create page and hit Create Knowledge Base, then moved on to the next step
<img width="1904" height="885" alt="image" src="https://github.com/user-attachments/assets/fa943531-face-4eb0-8c31-9fbbb4c3a2fc" />

I checked the information alert to confirm the knowledge base had finished building, waited until the Status switched to Available (about five minutes), and then moved on to the next step.
<img width="1890" height="880" alt="image" src="https://github.com/user-attachments/assets/f78f5ce1-f87c-4fe5-ac38-32bc56f8fe12" />

I scrolled down to Data source, checked the box to select the available data source, hit Sync, waited for the sync to finish, and then moved on to the next step.
<img width="1899" height="881" alt="image" src="https://github.com/user-attachments/assets/147e73b1-af5f-4baa-a011-b1fd049e7512" />

I opened the left navigation pane, clicked Agents, then hit Create agent in the Agents section, and moved on to the next step.
<img width="1891" height="887" alt="image" src="https://github.com/user-attachments/assets/6b963605-7289-4f9b-ba34-fa249ece465b" />

I typed hr-assistant-agent into the Name field in the pop‑up, hit Create, and then moved on to the next step.
<img width="742" height="580" alt="image" src="https://github.com/user-attachments/assets/bf93eccf-39bc-40b6-9916-854cbab5e933" />

I confirmed the agent was created, selected the “Use an existing service role” radio button, chose Bedrock_Agent_Role from the dropdown, scrolled down to the Select model section, and moved on to the next step.
<img width="1910" height="881" alt="image" src="https://github.com/user-attachments/assets/5adbb580-1363-4673-8b07-c52505733c70" />

I clicked the pencil icon next to Select model to change the model, then moved on to the next step.
<img width="1025" height="887" alt="image" src="https://github.com/user-attachments/assets/6f36f8fa-cbb1-438f-af33-381a730eb455" />

I chose Nova Pro under Models, clicked Apply, and moved on to the next step.
<img width="1019" height="884" alt="image" src="https://github.com/user-attachments/assets/a671cf88-82e1-4645-909f-d79265475ea8" />

I pasted the agent prompt I’d copied earlier into the Instructions for the Agent field, scrolled to the top of the page and clicked Save, then moved on to the next step.
<img width="1909" height="879" alt="image" src="https://github.com/user-attachments/assets/e4988aa4-74ed-4943-b4b2-d35865bb609f" />

I scrolled down to Knowledge Bases, hit Add, and moved on to the next step.
<img width="1914" height="887" alt="image" src="https://github.com/user-attachments/assets/e8602085-c0e5-48e3-98f4-a743b7e2ecc3" />

I chose hr‑knowledge‑base from the Select Knowledge Base dropdown, reviewed the note about adding instructions when using multiple knowledge bases, clicked Add, and moved on to the next step.
<img width="1891" height="877" alt="image" src="https://github.com/user-attachments/assets/d5ff9e5d-dced-4b59-a2d8-bd7873425767" />

I checked the success alert, hit Save under Agent builder, then clicked Prepare, and moved on to the next step.
<img width="1894" height="879" alt="image" src="https://github.com/user-attachments/assets/93630a07-a069-4945-bcf3-ffbfd7328224" />
<img width="1895" height="882" alt="image" src="https://github.com/user-attachments/assets/e7d0b28f-e3f1-42d7-9ed7-3bd218c84332" />

I reviewed the success alert, typed “What are the standard work hours?” into the Test Agent pane, hit Run, and moved on to the next step




