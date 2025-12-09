# **@MALLS PRESENTATION**

<img width="600" height="600" alt="image" src="https://github.com/user-attachments/assets/2dc3ffa7-2880-4565-ae64-2533d0c97bdb" />

**Sticky notes!!**

Miss Leah!

Set the tone: Welcome everyone to the presentation about our digital journey at @MALLS—”Africa's finest roots”.

Focus: Today, we'll cover our restaurant's challenges and how our migration to AWS has provided a modern, cost-effective solution.

Handover: I will handover to Moks to demonstrate further…

Moks take over

<img width="600" height="600" alt="image" src="https://github.com/user-attachments/assets/63752033-d03d-46eb-829e-75cdf61dd626" />

**Sticky notes!!**

Moks part:

Great everyone in class first:

Introducing the Team:

We are @MALLS Restaurant team – bringing South African culture to life with vibrant colours.

Go to the next slide..

<img width="600" height="600" alt="image" src="https://github.com/user-attachments/assets/51258a1f-8583-4256-9b02-6131081b91ce" />

**Sticky notes!!**

Moks, start by saying: I will walk you through our restaurant current situation..

History of the restaurant:
- It Started(2020)-founded by 5 great Team players, and branded the Restaurant @MALLS, so we can bring SA flavours to Gauteng.
- Our Milestone(pause a little bit)-We opened a permanent spot in Bramley view.

Our restaurant Uniquenes:
- The Core value: its being authentic South African cuisine for every South African culture.
- Our restaurant is a go-to for locals, a must-see for tourists craving real SA taste.

Customer:
- The Locals: families, students, office workers seeking fast food and home-cooked meal feeling.
- Food lovers: they love braai, bobotie, bunny chow..etc..
- Tourists visitors: wanting an authentic SA culinary experience.

Go to the next slide..

<img width="600" height="600" alt="image" src="https://github.com/user-attachments/assets/4bf70dd3-76d6-4676-bf66-60bcf267eddf" />

**Sticky notes!!**

Challenges we faced in our restaurant:

Before the digital upgrade we had big problems:

- We had Order Issues- Orders got mixed up and wrong dishes went out, making customers angry.

- Double bookings caused long waits for tables.

- No central customer information(Data), so we lost repeat business and loyalty from our customers.

- Not enough staff meant everything had to be done manually slowing us down.

Go to the next slide..


<img width="600" height="600" alt="image" src="https://github.com/user-attachments/assets/3f8f2142-1295-4e06-9d24-a1c136dd18d0" />

**Sticky notes!!**

Our Vision was to build simple, powerful online presence: 

So we aimed for a simple static website that would include:

- High-quality pictures of our dishes.

- Integrated forms for dine-in bookings and take-away orders.

- A robust loyalty programme.

- Customer login/register/sign-up functionality, this will help us to track our loyal customers and not to lose customers but to grow the business.

- Interactive Map & directions for easy access to our premises.

Moks, give Miss Leah a chance to bring in the next segment!!

Miss Leah come in:

Leah: We now going to handover our web devs to demonstrate the website on S3..
Leah: Lethabo & Skhuh the floor is yours..
Lethabo: We deployed on AWS S3, and show them a little demonstration e.g the pics. And handover to Skhuh & Moks 
Skhuh: Lead the demonstration(show off the websites function and if you feel you enough just say.. Moks take over)
Moks: finish off the demonstration..

Miss Leah come in and hand over to Aytee:
Leah: Aytee please take us to the end!

Go to the next slide:

Aytee: finish off the slides


<img width="600" height="600" alt="image" src="https://github.com/user-attachments/assets/ca03d6e4-f762-4a69-b662-95f8d7963dde" />

**Sticky notes!!**

This is where the AWS S3 is presented by Lethabo..

<img width="600" height="600" alt="image" src="https://github.com/user-attachments/assets/461d237c-91ef-4085-a80b-93fac985513b" />

**Sticky notes!!**

This is where the website presented, by Skhuh and Moks..

<img width="600" height="600" alt="image" src="https://github.com/user-attachments/assets/c483844e-329c-497f-b8cc-7a0c21c87119" />

**Sticky notes!!**

Our Current Static Website on AWS 

The Architecture: We decided to leverage the power of Amazon Web Services (AWS) to host our site.

The "Serverless" Approach: Show how we built the site using various AWS services.

- S3 & CloudFront: The website and images are hosted on S3 and delivered globally fast via CloudFront.

- Route 53: Custom domain & DNS, like (www.@MALLS.co.za)

- API Gateway & Lambda: Forms connect to the back-end using API Gateway, and Lambda handles the actual booking and order logic.

- DynamoDB & Cognito: DynamoDB stores all reservations, orders, and loyalty points, while Cognito manages secure customer login and registration.

- Location services for interactive Map.

- Benefit: This keeps the site cheap, scalable, and always available for our guests.

Go to the next slide:

<img width="600" height="600" alt="image" src="https://github.com/user-attachments/assets/92aa6534-b480-4424-8699-82e147e06d55" />

**Sticky notes!!**

AWS COST ANALYSIS:

[Full names](Don’t say them outloud, this is only if they ask us of the abbreviations only)
- ACM = AWS Certificate Manager
- SSL= Secure Sockets Layer (The protocol that ACM uses for its certificates)

AWS cost breakdown:
- Most expensive: Cloudfront – R470(Makes pages and images load super fast worlwide)

- Free or cheap: 
- S3 = Low cost service (Stores all the pictures, the website files, the menu pdfs)

- Route 53 = Low cost service (Handles our custom domain like, www.@MALLS.co.za)

- SSL certificates via ACM = Free service (Gives us a free SSL certificates so the site runs on https)

- API Gateway = Low cost service (Lets the booking and take-away forms talk to the back-end)

- Lambda = Low cost service (Tiny functions that actually save the reservation or order details)

- DynamoDB = Low cost service (The database that actually save the reservation or order details)

- Location Service = Free service (Powers the Map on our site so people can find us)

- Cognito = Free service (Handles login, sign-up and password resets for customers)

Total monthly bill: Only R540 – R630, a very cost-effective upgrade.

Bottom line: Using AWS lets us run a high-traffic site with bookings, maps and a loyalty program cheaply, while AWS handles the servers and upgrades, so we don’t have to.

Go to the next slide..

<img width="600" height="600" alt="image" src="https://github.com/user-attachments/assets/31810127-9bcf-4588-9ffb-46b2a4722834" />

**Sticky notes!!**

Using Manual System VS AWS Migration

- Dramatic Difference: Visually shows the difference between the manual system cost and the AWS cost.

- Old Cost: The manual system cost was roughly +R6,000 monthly.

- New Cost: The AWS migration costs are now only ~R540 – R630 monthly.
Return On Investment: This migration provides an immediate, massive return on investment(ROI).

Go to the next slides..

<img width="600" height="600" alt="image" src="https://github.com/user-attachments/assets/db5921b7-1d73-48eb-a101-5ebdfb417ccf" />

**Sticky notes!!**

Benefits of Moving to AWS:

Say this slowly as you demonstrate..just to give the audience to read further what is in there..
We considered the speed.., reliability.., security.., scalality.., cost control.., managed services.

Key Advantages-

- Speed: it Updates roll out in minutes, and not days. 

- Reliability: 
The system is 99.9% up(pause a little), it’s up and running most of the time (only about 8 hours of downtime per year).
(pause a little in between)
- Automatic failover, if something goes wrong, the system switches to a backup automatically so you don’t notice the problem 

- Security: 
-AWS manages patches(they automatically apply software updates and fixes to keep the system secure),
(pause a little in between)
-encryption(data is scrambled so only authorized users can read it, both while it’s stored and while it’s moving),
(pause a little in between)
-backups(they regularly copy your data to safe locations so you can restore it if something goes wrong).

- Scalability: We can handle peak nights and sudden spikes without buying new hardware, extra staff and new technology.

- Cost Control: We now use a pay-as-you-go model, resulting in a monthly bill of about R540-R630.

 Ooh this is awesome guys!!(Giggle a little bit to show that we are excited as a business)
- Managed services: 
-AWS handles the IT work.
-No server patching = we don’t have to apply software updates ourselves.
-Backups handled = they take care of saving copies of our data.

Go to the next slide for a conclusion..

<img width="600" height="600" alt="image" src="https://github.com/user-attachments/assets/3e328bdd-d2d8-460d-9f51-0b6c8dba3ef5" />

**Sticky notes!!**

Conclusion:

- Final Summary: We successfully moved from a manual paper-based system to AWS.

- Impact: The monthly cost dropped from over R6,000 to about R540–R600.

The system stays up 99.9 % of the time, even when we’re busy.
We can add more power with just a click – no new hardware needed.
AWS takes care of security patches and encryption, so we worry less about data breaches.
Updates go live in minutes, not days, so we can improve the service quickly.

- The Bottom Line: The cloud gives us a cheaper, more reliable, and faster way to run our business. It allows us to focus on serving our customers and our unique South African food, instead of fixing computers

Say: “Thank you”

Go to the next slide..

Miss Leah take over..

<img width="600" height="600" alt="image" src="https://github.com/user-attachments/assets/8e93fe10-5a91-497f-a0bc-6bb777b94bf1" />

**Sticky notes!!**

Questions & Answers!

Leah: Thank you class, we now going to take questions and answers!!

(Open the floor for questions.) Lets all as a group listen and be ready to answer questions!!


This is for my Team mates..

I can’t thank you enough for how brilliantly we’ve been pulling together. From the late‑night crunch sessions to the instant support whenever anyone calls, you’ve turned sleepless nights into victories and made this team feel unstoppable. 

Woow—you’re a powerhouse crew, and I’m privileged to work side‑by‑side with such amazing mates! 

🙌I personally worked well and learned a lot from you all, and for that, thank you.

Let’s keep crushing it!




