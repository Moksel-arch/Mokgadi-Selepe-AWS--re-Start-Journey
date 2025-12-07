# **AWS Bedrock + EC2 Lab - Generate a Static Webpage with AI**

Hey, this is my little repo where I saved the stuff from an AWS lab I just finished.  
The lab shows how to use Amazon Bedrock (the new Nova Lite model) to generate a full static webpage with one prompt, and then put that page on a real EC2 instance that runs Nginx.

## What I did (simple steps I followed)

1. Opened Amazon Bedrock  
2. Went to the Chat playground  
3. Picked the Amazon → Nova Lite (on-demand) model  
4. Set max tokens to 5120 and temperature to 0 (so it gives me clean code)  
5. Typed this prompt:

```
Generate a static webpage for AnyCompany marketing agency without any explanation.
```

6. Copied the full HTML it gave me (it was a complete ready-to-use page)  
7. Went to my EC2 instance (already running, called app-server)  
8. Copied the public IP and opened http://<ip> → saw the default “Hello World” page  
9. Connected with Session Manager (no SSH key needed)  
10. Went to `/usr/share/nginx/html`  
11. Opened `index.html` with nano, deleted everything, pasted the AI-generated HTML  
12. Saved the file (Ctrl+X → Y → Enter)  
13. Refreshed the browser → boom, my new fancy marketing page is live!

## Files in this repo

- `index.html` → the exact HTML that Bedrock Nova Lite generated for me  
- `screenshot.png` → quick photo of how the page looks when live (optional, I added it later)

## Why I kept this

- Super fast way to make a good-looking landing page without writing HTML/CSS myself  
- Shows that Bedrock can output clean, ready-to-use code with temperature 0  
- Cool proof that you can deploy AI-generated stuff in seconds on real AWS servers

Feel free to fork, use the HTML, change the prompt, whatever you want.

That’s it! Simple lab, but I think it’s pretty awesome what you can do with Bedrock now.

---
Contacts:
- Mokgadi: 067 719 3860
- mokgadi9939@gmail.com
