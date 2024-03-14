---
tags: 
  - dwarves
  - team
  - process
  - updates
title: Configure The Company Email
date: 2022-11-29
description: null
authors: null
menu: memo
type: null
hide_frontmatter: false
---

### 1. **Make sure you have 2FA enabled**
For this method to work, you need to have [two factor authentification](https://www.google.com/landing/2step/) enabled for your Google account. If it’s not, follow the link below and set it up.

[https://www.google.com/landing/2step/](https://www.google.com/landing/2step/)

### 2. **Create an App Password**
Google will verify your ownership with this app password. Select “Mail” under app, and “Mac” under device. Hit “Generate”. Copy and keep for later!

![[75bba213e343be0d54245f70f1bb00b8_MD5.gif]]

### 3. **Add your email to Gmail**
Go to Gmail -> Settings -> Accounts and Import. Then, select “Add another email address you own” under Aliases.

[https://security.google.com/settings/security/apppasswords](https://security.google.com/settings/security/apppasswords)

### 4. **Fill in your sender’s information**
Set your forwarded email (example@d.foundation) and your sender’s name. Untick “treat as an alias”.

![[e40460b7c3bb0a5b24d84d2916ef058a_MD5.gif]]

### 5. **Fill in your email informations**
SMTP is **smtp.gmail.com**, port is right already. 

Username is **your gmail address** (incl. @gmail.com). 

Password is the password you generated on Step 2. 

Leave TLS enabled as is

![[a0083c2a2c03b49be443442fd9b9d388_MD5.gif]]

### 6. **Confirm Ownership**
You will receive an email from GMail asking you to confirm ownership with a code. Fill in the code in the popup modal, and you are all set!

### 7. **Send emails from your alias**
Now you can just select your alias in the list when you compose a new message.

### 8. **To send emails from your Mac client (optional)**
* Go to Mail client -> Settings -> Choose your individual email which added alias -> Edit Email Addresses

![[c636f82d2c678d9d015131573a8bd8e2_MD5.webp]]

* Fill your alias information

![[5ae2d96d24c6e58a28b97536eb54364e_MD5.webp]]

* Now you can just select your alias in the list when you compose a new message in your Mac client.

![[a064fb3d515cf37f25f840c5fc850689_MD5.webp]]

