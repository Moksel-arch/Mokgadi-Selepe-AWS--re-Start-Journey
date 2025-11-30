# **Internet Protocols - Static and Dynamic Addresses**

***Objectives*
<img width="867" height="569" alt="image" src="https://github.com/user-attachments/assets/4f7595d5-89c0-406d-b4db-63a33696c27f" />

In this lab, I must:

- Summarize the customer scenario
- Analyze the difference between a statically and dynamically assigned IP addresses using EC2 instances
- Assign a persistent (static) IP to an EC2 instance
- Develop a solution to the customers issue found within this lab; after developing a solution, summarize and describe your findings
<img width="1909" height="878" alt="image" src="https://github.com/user-attachments/assets/a2573262-ae7c-4820-945d-95a6afd00bba" />
<img width="1912" height="885" alt="image" src="https://github.com/user-attachments/assets/cd415361-a89c-4286-a208-98dda3340372" />
<img width="1911" height="915" alt="image" src="https://github.com/user-attachments/assets/1c8138a0-bbd4-442d-b639-b21ae711ad1d" />
<img width="1913" height="884" alt="image" src="https://github.com/user-attachments/assets/e092024b-ed99-404d-a649-9740e361daf7" />
<img width="1914" height="889" alt="image" src="https://github.com/user-attachments/assets/f4868c64-0157-4a2f-b9a9-e4e45dbd712c" />
<img width="1919" height="893" alt="image" src="https://github.com/user-attachments/assets/7729fdfd-b3f6-42f5-ac35-51ddf1be1bd9" />
<img width="1912" height="886" alt="image" src="https://github.com/user-attachments/assets/6fd65f4c-c99a-4cf7-aab8-eb782e3ca60f" />
<img width="1027" height="616" alt="image" src="https://github.com/user-attachments/assets/60d6ee89-40cf-4314-8ccb-7da209eae15e" />
<img width="1913" height="884" alt="image" src="https://github.com/user-attachments/assets/a21fb29b-e289-4f5f-993e-8515099c8ddf" />
<img width="1913" height="889" alt="image" src="https://github.com/user-attachments/assets/577402ac-a0d5-4085-a105-e8f620549e8a" />
<img width="1913" height="882" alt="image" src="https://github.com/user-attachments/assets/03f14f27-41d8-4a52-8e60-b93c520c0f0c" />
<img width="1915" height="882" alt="image" src="https://github.com/user-attachments/assets/8c47407c-1a8c-42df-8529-eba0d0b331dc" />
<img width="1916" height="881" alt="image" src="https://github.com/user-attachments/assets/ca280b38-aabe-476f-8de2-dc0ef1f4c09b" />
<img width="1914" height="891" alt="image" src="https://github.com/user-attachments/assets/7782ccc6-b277-47ae-9bf5-09d55e054965" />
<img width="1909" height="887" alt="image" src="https://github.com/user-attachments/assets/8d52f4a4-0525-4c74-bfe3-86ee4cdd3e72" />
<img width="1905" height="882" alt="image" src="https://github.com/user-attachments/assets/f589dc76-564d-454e-997d-c5c86202e92c" />
<img width="1912" height="843" alt="image" src="https://github.com/user-attachments/assets/05354d50-07f8-485b-86ca-d21f324c1812" />
<img width="1917" height="882" alt="image" src="https://github.com/user-attachments/assets/7132363a-9b4d-49b8-b313-3943c5c8e37e" />
<img width="1912" height="882" alt="image" src="https://github.com/user-attachments/assets/f1188ec0-0019-4000-a6e2-6f1a45b6151f" />
<img width="1914" height="883" alt="image" src="https://github.com/user-attachments/assets/361bd41a-5bbf-4520-969f-dd907d62945f" />
<img width="1915" height="875" alt="image" src="https://github.com/user-attachments/assets/ae0ab34f-9f4d-4553-b19a-8bd469731991" />
<img width="1917" height="846" alt="image" src="https://github.com/user-attachments/assets/65b2579d-a09f-492c-9fde-5ff65944bb65" />
<img width="1906" height="868" alt="image" src="https://github.com/user-attachments/assets/9c4a4fdf-58ce-47cd-b2cb-fd210eb4e65c" />
<img width="1905" height="880" alt="image" src="https://github.com/user-attachments/assets/11762d33-240c-4538-ac74-dcd15dc163a6" />
<img width="1909" height="876" alt="image" src="https://github.com/user-attachments/assets/e13db7f6-89b8-47a4-8841-618eab8e78ad" />

***2: Send the Response to the customer (Group Activity)*
What I did:

- I finished the lab and wrote down what I found.
- My notes include:
    - Both EC2 instances are in the same VPC (10.0.0.0/16).
    - Instance B has a public IP and can reach the internet; Instance A does not.
    - The private IP range is fine, but the missing public address (or missing route to an Internet Gateway) is why Instance A can’t get out.

Group activity

- In my group we will submit the findings.
- Person 1 (me) will play Bob the customer.
- Person 2 will be the Cloud Support Engineer.
- Person 2 will explain the findings to me in plain language.
- We’ll keep it short – about 5‑10 minutes – and then share a quick summary with the class.

