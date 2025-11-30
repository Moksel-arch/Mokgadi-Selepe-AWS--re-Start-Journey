# **AWS Lab – Static vs Dynamic Public IP Addresses**

*My own notes from the lab – written by Mokgadi Selepe*

### What the customer (Bob) was complaining about  
Bob has an EC2 instance called “Public Instance”.  
Every time he stops it (to save money) and starts it again, the public IP changes to a new random number.  
This breaks all the other systems that need to talk to that exact IP. He wants the public IP to stay the same forever.

### What I did in the lab to see the problem myself  
1. Launched a normal EC2 instance in a public subnet with “Auto-assign Public IP = Enable”.  
2. Noted the public IP (for example 54.123.45.67).  
3. Stopped the instance → public IP disappeared.  
4. Started it again → public IP came back as something totally different (like 54.987.65.43).  
5. Private IP never changed – it stayed the same the whole time.

So yes, the normal public IP that AWS gives you is **dynamic** – it changes on every stop/start.  
That is exactly Bob’s problem.

### The real fix – Elastic IP (EIP)  
AWS has a special thing called an **Elastic IP**.  
It is a permanent public IP that belongs to your account and never changes.

How I fixed it in the lab:  
1. Went to EC2 → Network & Security → Elastic IPs.  
2. Clicked “Allocate Elastic IP address” → got a fixed IP (e.g. 3.456.789.012).  
3. Selected the new EIP → Actions → Associate Elastic IP address.  
4. Picked my test instance and clicked Associate.  

Now the instance shows the Elastic IP as its public IP.

### Tested the fix  
- Stopped the instance → Elastic IP stayed attached.  
- Started it again → public IP was still the same Elastic IP. No change!  
It works perfectly.

### Quick summary  
- Normal public IP (auto-assigned) = **dynamic** → changes on stop/start  
- Private IP = always **static**  
- Elastic IP = **real static public IP** → never changes, even after 100 stops/starts  

### Message I will send to Bob  
Hi Bob,  

I found the problem. The normal public IP that AWS gives automatically is temporary – it changes every time you stop and start the instance. That’s why everything breaks.

The fix is super easy: we give your instance an **Elastic IP**. It is a permanent public IP that stays the same forever.

I can do it in 2 minutes and there is no extra cost as long as the instance is running.

Just say “yes please” and I’ll set it up right now and send you the new fixed IP.

Kind regards,  
Mokgadi  

### Status  
Waiting for Bob to reply. As soon as he says go ahead, I will attach the Elastic IP and the problem is gone forever.

-Mokgadi: mokgadi9939@gmail.com
