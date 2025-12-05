# **AWS SimuLearn: Create an AI Smart Assistant**
**Use Amazon Bedrock to create a knowledge base and an agent**
- Before AI Agent:
<img width="940" height="554" alt="image" src="https://github.com/user-attachments/assets/b7cef42e-ca98-4933-8657-68e1db8ca632" />

- After AI Agent:

<img width="966" height="621" alt="image" src="https://github.com/user-attachments/assets/f24edce6-f461-4d70-92ca-11bd277cabf0" />

---

**Ok! Here are the steps I followed to Create an AI Smart Assistant**

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
<img width="1900" height="890" alt="image" src="https://github.com/user-attachments/assets/ba6316b1-302c-46da-870f-c7fae106c695" />

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
<img width="1918" height="873" alt="image" src="https://github.com/user-attachments/assets/c7bcc283-831a-440f-ab29-88553a323a8b" />

I chose hr‑knowledge‑base from the Select Knowledge Base dropdown, reviewed the note about adding instructions when using multiple knowledge bases, clicked Add, and moved on to the next step.
<img width="1891" height="877" alt="image" src="https://github.com/user-attachments/assets/d5ff9e5d-dced-4b59-a2d8-bd7873425767" />

I checked the success alert, hit Save under Agent builder, then clicked Prepare, and moved on to the next step.
<img width="1894" height="879" alt="image" src="https://github.com/user-attachments/assets/93630a07-a069-4945-bcf3-ffbfd7328224" />
<img width="1895" height="882" alt="image" src="https://github.com/user-attachments/assets/e7d0b28f-e3f1-42d7-9ed7-3bd218c84332" />

I reviewed the success alert, typed “What are the standard work hours?” into the Test Agent pane, hit Run, and moved on to the next step
<img width="1917" height="880" alt="image" src="https://github.com/user-attachments/assets/98289abe-1f36-45a2-afc3-cffc13f2166c" />
<img width="1906" height="887" alt="image" src="https://github.com/user-attachments/assets/e7cce492-fb19-4fa3-aec5-589b90cb0cf7" />

I checked that the agent’s response came from the employee handbook (and peeked at the .txt files in S3), typed “What is the vacation policy?” into the input box, hit Run, and moved on to the next step.
<img width="1910" height="884" alt="image" src="https://github.com/user-attachments/assets/aa1cb462-efdd-4b5e-a4c5-fce5cd3d8814" />
<img width="1919" height="880" alt="image" src="https://github.com/user-attachments/assets/83ea9fd5-8421-4c12-a7e2-7a7e844d0100" />

I scrolled down to Action groups in the Agent builder pane, hit Add, and moved on to the next step.
<img width="1913" height="875" alt="image" src="https://github.com/user-attachments/assets/fca8a505-cc31-41ce-93ef-453b14b7fda7" />

I typed submit_leave_action as the Action group name, scrolled down to Action group invocation, and moved on.
<img width="1912" height="888" alt="image" src="https://github.com/user-attachments/assets/e6bc8ad7-0507-41e0-84da-70447922b543" />

I chose Select an existing Lambda function, picked submit_leave, scrolled down to Action group function 1, and moved on to the next step.
<img width="1912" height="890" alt="image" src="https://github.com/user-attachments/assets/fd2d2dac-842f-4be7-aaac-eccaa15ca4ec" />

I typed submit_leave for the name, scrolled down to Parameters, and moved on.
<img width="1917" height="877" alt="image" src="https://github.com/user-attachments/assets/88eeae82-7578-4f34-aaeb-58a650970ef5" />

I clicked Add parameter, entered employee_name as the name, typed “Name of employee” for the description, set Required to True, and moved on to the next step.
<img width="1911" height="877" alt="image" src="https://github.com/user-attachments/assets/a37fd1c5-f360-48bc-8104-fae852eeb695" />

I clicked Add parameter twice to create two more parameters, set Name to startDate (description “Start date of leave”) and endDate (description “End date of leave”), confirmed all three parameters were required, then saved and exited.
<img width="1897" height="869" alt="image" src="https://github.com/user-attachments/assets/c46bff46-e71c-4043-9356-1d2c2ea19291" />
<img width="1915" height="887" alt="image" src="https://github.com/user-attachments/assets/dc302a29-e35a-41db-a6b9-e808f17eef94" />

I expanded the Additional settings, enabled User input, scrolled back to the top, and moved on to the next step.
<img width="1902" height="883" alt="image" src="https://github.com/user-attachments/assets/cb7cd4a0-22df-4251-b744-ad664a99e5a9" />

I hit Save and Prepare in the Agent builder, typed “submit my vacation request” in the Test Agent pane (opened it with the Test button), clicked Run, and moved on to the next step.
<img width="1913" height="877" alt="image" src="https://github.com/user-attachments/assets/6f827ae6-496e-43fc-affe-a8df0ca4256d" />
<img width="1918" height="885" alt="image" src="https://github.com/user-attachments/assets/f22cfcd2-5c9c-43b4-9d66-bea6a0bb896c" />

I read through the Agent’s questions, answered each one as needed, hit Run, and moved on to the next step.
<img width="1915" height="882" alt="image" src="https://github.com/user-attachments/assets/ebdea511-50df-40e3-b8e9-9193a2f98f8e" />

I verified that the Agent confirmed the vacation request was submitted successfully (keeping in mind the wording could vary) and then moved on to the next step.
<img width="1911" height="875" alt="image" src="https://github.com/user-attachments/assets/7e5524f1-b2dd-4aa4-977f-5cae7300c2cb" />
<img width="1918" height="891" alt="image" src="https://github.com/user-attachments/assets/ab180735-05e9-4fe4-82b2-2f47c4189164" />

I typed lambda into the top‑navigation search box, clicked Lambda under Services in the results, and moved on to the next step.
<img width="1910" height="882" alt="image" src="https://github.com/user-attachments/assets/5a58c952-868a-4ee4-b3ef-f96857bf4aa0" />
<img width="1919" height="719" alt="image" src="https://github.com/user-attachments/assets/97b0a07d-0d5c-47a4-aa9b-a4af05d42303" />

I looked over the submit_benefits and submit_leave Lambda functions, clicked submit_leave, and moved on to the next step.
<img width="1907" height="835" alt="image" src="https://github.com/user-attachments/assets/60d5ab31-cf83-4927-b43d-f32876d97f4d" />

I opened the Code tab, checked out submitLeave.py, and saw that it grabs the action‑group parameters and writes them to the VacationTable in DynamoDB. Then I moved on to the next step. If you need more details, a quick web search might help.
<img width="1912" height="874" alt="image" src="https://github.com/user-attachments/assets/87cebdf2-9d6e-4496-a228-9a00e044c436" />

I typed dynamodb into the top‑navigation search box, clicked DynamoDB under Services in the results, and moved on to the next step.
<img width="1912" height="879" alt="image" src="https://github.com/user-attachments/assets/bfe83042-d1bf-4834-a031-7a7f32ee7ef8" />
<img width="1915" height="885" alt="image" src="https://github.com/user-attachments/assets/49309a4f-fecb-414f-a45c-590f60e5ef8a" />

I opened the left navigation pane, clicked Tables, saw the two lab‑created tables (VacationTable for vacation details and BenefitsTable for claim details), selected VacationTable, and moved on to the next step.
<img width="1918" height="825" alt="image" src="https://github.com/user-attachments/assets/a8c2cb61-3a83-47d2-91ab-8a3dc18022ba" />
<img width="1911" height="872" alt="image" src="https://github.com/user-attachments/assets/e66c126d-db03-4174-a9e8-185070e0b40a" />
<img width="1916" height="874" alt="image" src="https://github.com/user-attachments/assets/319bc3ca-15b0-4acd-a68e-5adfad4a7a0b" />

I clicked Explore table items under VacationTable, checked the Partition key details in the General information section, and moved on to the next step.
<img width="1914" height="872" alt="image" src="https://github.com/user-attachments/assets/59eb6568-15da-4450-bf2b-029d3b8fe5f1" />
<img width="1915" height="883" alt="image" src="https://github.com/user-attachments/assets/b8e33fcb-785b-41d1-acfa-cb0a49012ceb" />

I checked the single item returned in the VacationTable – the entry the Bedrock agent added when the vacation details were submitted – and then moved on to the next step.
<img width="1906" height="874" alt="image" src="https://github.com/user-attachments/assets/dff73290-6385-4c4f-9214-40894a5295e6" />

<img width="1905" height="819" alt="image" src="https://github.com/user-attachments/assets/91fb0d4d-ee99-4ccd-80e2-c085a5c4200d" />

<img width="1405" height="774" alt="image" src="https://github.com/user-attachments/assets/81a00e80-ed47-466f-85ba-491f36a5e4db" />
<img width="1409" height="866" alt="image" src="https://github.com/user-attachments/assets/9d003f8f-c474-4640-aa16-8b7a5dd2edf0" />
<img width="1413" height="872" alt="image" src="https://github.com/user-attachments/assets/b4a79faa-3c18-4eeb-9426-95b714a02d95" />
<img width="1416" height="880" alt="image" src="https://github.com/user-attachments/assets/fbb43acd-0cb9-4190-9715-e60a5dffff3b" />
<img width="1410" height="876" alt="image" src="https://github.com/user-attachments/assets/3f516f5e-ebfb-4788-8ff1-f5010af32020" />
<img width="764" height="584" alt="image" src="https://github.com/user-attachments/assets/6e7d29f6-d0d3-40d8-a3a7-80ee1fc72093" />
<img width="1430" height="890" alt="image" src="https://github.com/user-attachments/assets/759c2c96-0a88-41ab-955b-7823b74596f7" />
<img width="1407" height="877" alt="image" src="https://github.com/user-attachments/assets/c1e9167c-4904-468d-a014-53e0667db181" />
<img width="1425" height="880" alt="image" src="https://github.com/user-attachments/assets/9a24c39d-a106-466c-857c-ce22dee40d93" />








