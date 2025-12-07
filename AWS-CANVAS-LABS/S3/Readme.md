# **Amazon S3**

This is a simple practice lab I did on AWS to host a static website using S3.  
I followed the steps, made a few changes, and got the website running.  

Here is exactly what I did:

## What I did

1. I typed `s3` in the AWS search bar at the top and clicked on S3 under Services.

2. I went to the **General purpose buckets** tab and opened the bucket that starts with `website-bucket-`. That bucket already had the files for the lab.

3. I copied the full bucket name to a text file because I needed it later.

4. In the **Objects** tab I saw five files (the website files).

5. I selected the file called `text.html`, clicked **Actions → Rename object**, and changed its name to `error.html` (this is the error page).

6. I went to the **Permissions** tab and checked that **Block all public access** was turned off (it needs to be off for the website to work).

7. I looked at the bucket policy – it allows anyone to read the files (GetObject). It’s okay for this lab, but in real life I would make it stricter.

8. I switched to the **Properties** tab.

9. I scrolled down to **Static website hosting** and clicked **Edit**.

10. I turned on static website hosting:
    - Chose **Enable**
    - Hosting type: **Host a static website**
   
---
Contacts:
- Mokgadi: 067 719 3860
- mokgadi9939@gmail.com
    - Index document: `index.html`
    - Error document: `error.html`

11. Clicked **Save changes**.

12. After saving, I copied the **Bucket website endpoint** (the special S3 website URL).

13. I opened a new browser tab, pasted that endpoint, and the “Beach Wave Conditions” website loaded perfectly.

14. Finally, for the validation part of the lab, I renamed `index.html` to `waves.html` using the **Actions → Rename object** menu again.

That’s it – the static website is now hosted on S3 and working!

## Bucket name
The bucket name starts with `website-bucket-` (the full name is different for every person). I saved mine in a text file.

## Files in the bucket after I finished
- waves.html (was index.html)
- error.html (was text.html)
- plus the other original files (CSS, images, etc.)

The lab is complete and the test servers found the `waves.html` file without any problem.

Feel free to use this repo as a quick reminder of how to set up a basic static website on S3!

---
Contacts:
- Mokgadi: 067 719 3860
- mokgadi9939@gmail.com
