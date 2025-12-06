Generate Code for Webpage!!

1. Review the practice lab objectives in the Concept section.
2. Click Start Lab or Open AWS Console to begin.
3. Follow the lab instructions carefully, and use the arrows to navigate between steps.

AWS services not used in this lab are disabled in the lab environment. In addition, the capabilities of the services used in this lab are limited to what the lab requires.

---
1. In the top navigation bar search box, type:

bedrock

2. In the search results, under Services, click Amazon Bedrock.
3. Go to the next step.
<img width="1913" height="879" alt="image" src="https://github.com/user-attachments/assets/8827a19b-f31e-423b-a517-3b5c57c7e89d" />
<img width="1915" height="884" alt="image" src="https://github.com/user-attachments/assets/ad7375f5-b2dd-451e-8046-103fef05a0e1" />
---

1. In the left navigation pane, under Test, click Chat / Text playground.
2. Go to the next step.
<img width="1916" height="884" alt="image" src="https://github.com/user-attachments/assets/6a867703-8fe8-4913-a079-613756099e0f" />

---

1. On the Chat / Text playground page, for Mode, click the arrow to expand the dropdown list.

- Be sure to review the available modes.

2. Choose Chat.
3. Go to the next step.
 <img width="1898" height="828" alt="image" src="https://github.com/user-attachments/assets/7d865d0c-1ca0-42d3-af5e-1305bf83f686" />

---

1. Click Select model.
2. Go to the next step.
<img width="1034" height="852" alt="image" src="https://github.com/user-attachments/assets/eb2543d4-d32c-486e-843e-9e9f231b4ebe" />

---

1. In the pop-up box, for Serverless model providers, choose Amazon.
2. For Models, choose Nova Lite.
3. For Inference, choose On demand.
4. Click Apply.
5. Go to the next step.
<img width="1028" height="861" alt="image" src="https://github.com/user-attachments/assets/f5b09949-1135-4229-9447-303abd4f312c" />

---

1. In the pop-up box, for Serverless model providers, choose Amazon.
2. For Models, choose Nova Lite.
3. For Inference, choose On demand.
4. Click Apply.
5. Go to the next step.
<img width="1917" height="873" alt="image" src="https://github.com/user-attachments/assets/0ddc88d9-e861-44d7-bc35-14d5d9c0fa55" />
---

1. In the Configurations window, under Length, for Maximum output tokens, move the slider to 5120.

- Length parameters control how much text the model generates in its responses.

2. Under Randomness and diversity, for Temperature, move the slider to 0.

- Temperature controls the randomness of the model's responses.
- Top P (Nucleus Sampling) controls the cumulative probability threshold for token selection.
- 3. In the right pane prompt box, type:

Generate a static webpage for AnyCompany marketing agency without any explanation.

4. Click Run.
5. Go to the next step.
<img width="1914" height="884" alt="image" src="https://github.com/user-attachments/assets/d8e8f43b-0a38-4b5f-ada9-6ecacd700805" />
<img width="1919" height="876" alt="image" src="https://github.com/user-attachments/assets/f3a12029-727d-4f37-a09b-245df9b387d7" />

---

1. Review the generated response.
2. Highlight the generated response, copy, then paste it in the text editor of your choice on your device.

- You use this response in a later step.

3. Go to the next step.
<img width="1913" height="843" alt="image" src="https://github.com/user-attachments/assets/1ae8b693-dc34-4ba8-ae97-ff4ee543c367" />

---

1. In the top navigation bar search box, type:

ec2

2. In the search results, under Services, click EC2.
3. Go to the next step.
<img width="1912" height="882" alt="image" src="https://github.com/user-attachments/assets/713ba164-272f-4e1e-a1d3-8fb4240d8dad" />
<img width="1919" height="872" alt="image" src="https://github.com/user-attachments/assets/5f009e45-aa86-4e9b-8d00-8f4fb23b07fd" />

1. On the Dashboard, in the Resources section, click Instances (running).
2. Go to the next step.
---

1. In the Instances section, review the details of the available EC2 instance, app-server.
2. Choose app-server.
3. On the Details tab, under Public IPV4 address, click the copy icon to copy the IP address for the app-server instance, and then paste it in the copy editor of your choice on your device.
4. Go to the next step.
<img width="1917" height="849" alt="image" src="https://github.com/user-attachments/assets/deefb22a-2173-4f08-813f-24abd2cc0c73" />

--

1. In a new browser tab (or window) address bar, type:

http://

and then, paste the IP address that you just copied, and then press Enter.

- Your IP address will differ from what is displayed in the screenshot example.

2. Review the Hello World message.

- This message is from the index.html file that was created on the EC2 instance during the lab's prebuild process.

3. Go to the next step.
<img width="1907" height="239" alt="image" src="https://github.com/user-attachments/assets/e5781c8c-945d-4a66-a9b9-7eb4ded3a607" />

---

. Return to the Amazon EC2 browser tab.
2. In the Instances section, click Connect.
3. Go to the next step.
<img width="1913" height="874" alt="image" src="https://github.com/user-attachments/assets/33e623da-4dbc-4bf2-8fbd-a3bb944ff988" />

---

1. Click the Session Manager tab.
2. Click Connect.
3. Go to the next step.
<img width="1914" height="878" alt="image" src="https://github.com/user-attachments/assets/41b29371-b878-4baa-9504-931dfb4ed9c3" />
<img width="1917" height="709" alt="image" src="https://github.com/user-attachments/assets/26682792-6c3c-4302-a153-603391bc5c28" />
<img width="1911" height="905" alt="image" src="https://github.com/user-attachments/assets/4ea8faa0-c3fd-49cc-adea-9a093ef4fffa" />

---

1. In the terminal window, at the command prompt, to change the directory to the nginx html folder, run (type the command and press Enter):

cd /usr/share/nginx/html

2. To list the files in the html folder, run:

ls -ltrh

3. Review the two .html files created as part of the prebuild process.
4. To view the contents of the index.html file, run:

nano index.html

- Nano is a basic, user-friendly text editor for Unix-based systems (such as Linux and macOS). 

5. Go to the next step.
<img width="1915" height="501" alt="image" src="https://github.com/user-attachments/assets/e608b619-5e4e-4712-8bc8-9a50991d3caa" />
<img width="1912" height="919" alt="image" src="https://github.com/user-attachments/assets/413ba755-d0aa-4132-bd4d-b1269f04c4e0" />

---

1. Review the file contents.
2. Review the nano commands listed at the bottom of the terminal window.

- You can always access the help menu within nano by pressing Ctrl+G for a complete list of commands.

3. Delete the file contents.

- You can use the backspace or delete command to delete the file contents.

4. Go to the next step.
<img width="1910" height="916" alt="image" src="https://github.com/user-attachments/assets/190dd904-a78f-40c9-944e-62183f43d440" />

---

1. Paste the contents of the static webpage that you copied in an earlier step.
2. Go to the next step.
<img width="1894" height="907" alt="image" src="https://github.com/user-attachments/assets/a099a7ca-7ec5-4d99-8d54-9490af2f90a6" />

---

1. Press Ctrl+X on your keyboard (not shown).
2. For "Save modified buffer?", type:

Y

- If the terminal prompts you to enter the file name, press Enter.

3. Go to the next step.
<img width="1911" height="914" alt="image" src="https://github.com/user-attachments/assets/37d6d6ed-1695-4616-89c6-ad2131fa01ed" />
<img width="1916" height="905" alt="image" src="https://github.com/user-attachments/assets/eb134639-1e25-4a16-9c3f-dd54ede77461" />
<img width="1918" height="926" alt="image" src="https://github.com/user-attachments/assets/f8804643-81a0-47ac-91bb-beade41776bc" />

---

1. In the terminal, run:

ls -ltrh

2. Review to confirm that the index.html file is updated.

- To confirm that it's updated, you can check the file timestamp.

3. Go to the next step.
