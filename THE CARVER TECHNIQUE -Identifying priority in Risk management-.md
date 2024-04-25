# THE CARVER TECHNIQUE -Identifying priority in Risk management- 

### Introdduction
The CARVER technique, short for:
* **Criticality :** The value of the target
* **Accessibility :** How easily can the target be reached? be accessed?
* **Reoverability :** How long will it take for the target to recover?
* **Vulnerability :** How vulnerable is the target? Or the level of capability needed to overcome the target’s security
* **Effect :** The magnitude of the negative effect that would've been caused as a consequence of a malicious action done to the target.
When used as a tool for management and goal assessment, it could be seen as “the negative effect resulting from failure to reach the goal on time.”
* **Recognizability :** How easily can the target be identified and attacked?

Developed during the Vietnam War by the US as a tool to rank potential high-value enemy targets with scale. Today, this technique is employed across the civilian and military worlds for various purposes, but most often it’s used in a security context to assess the risk associated with the analyzed target. In actual use, the CARVER technique is often seen as a table with at least 8 columns, with the number of rows corresponding to the number of targets to be analyzed. Below is a sample of how such a table might’ve looked:

### Applying CARVER technique to a Discord-server database:
For a Discord server database. We can also apply the CARVER technique to manage the risk associated with each of its components:
| **Target** | **C** | **A** | **R** | **V** | **E** | **R** | **Total** |
|:----------:|:----------:|:----------:|:----------:| :----------:| :----------:| :----------:| :----------:|
| User data | 5 | 3 | 3 | 5 | 5 | 5 | 26 |
| Admin account | 5 | 1 | 3 | 4 | 5 | 5 | 22 |
| Chat logs | 3 | 2 | 3 | 3 | 4 | 2 | 23 |

The example table is a hypothetical CARVER assessment used in "Informational Security". We will be focusing 
on the target 'Mail server' for a detail explanation of why we assigned these scale number:
+ User Data:
    * **Criticality :** it has the highest rating as an exposure of this means a compromise of user’s personal information and privacy
     * **Accessibility :** this is dependent on how secure the server is against an attack. Generally, the responsibility of this falls into the role of the Server’s Admin and to Discord own security infrastructure. As Discord is very serious about the security of their user data and there had only been 2 security breaches during its 8 years of active service. It’s fair to assign the scale of 3 to Accessibility as its neither too serious nor low-risk enough to be ignored
     * **Reoverability :** With proper backup, data related to the User such as their roles within the server, activities, etc can be properly restored
     * **Vulnerability :** Although Discord's own infrastructure is well-protected against external attack. It still lacks virus scanning function for user-uploaded files so malware file, phishing link, etc is still a problem for most Discord users. The only protection a Discord user has against these attack is by better armed themself with “internet’s security” knowledge
     * **Effect :** Any server with its user data leaked will be dealt a severe blow to its reputation
     * **Recognizability :** High, the value of personal data can be used for various malicious activities such as Identity theft and blackmailing, etc
+ Admin account:
    * **Criticality :** High, as an Admin has full control over the entire server
    * **Accessibility :** Low, as only the admin has control over his account if there is no account sharing
    * **Reoverability :** Due to a very large amount of active users, Discord support takes time to go through user submitted support-requests. Therefore, it can be reasoned that even in the event of account lost, the server Admin still have to wait sometime to get his account recovered
    * **Vulnerability :** Even with 2 factor-authentication, an expert malicious actor still have the means and method to gain access to an account
    * **Effect :** A stolen Admin account will have a detrimental effect on the server as the account thief is free to do whatever he want with the server at will
    * **Recognizability :** Everyone know the important of an Admin account
+ Chat log:
    * **Criticality :** As long as the server’s user understands the ‘public nature’ of a server chat channel and does not reveal any critical information related to their personal life and information. It shouldn’t be anything critical
    * **Accessibility :** As Discord server moderator and admin can set level of access to different chat channels and can limit what user has access to what and what not. The accessibility is Low
    * **Reoverability :** With proper backup, chat log can be properly restored
    * **Vulnerability :** This depend more on the Admin and Moderator ability to vet people to determine whether or not they should grant someone access to difference channels
    * **Effect :** A leak in chat message can be detrimental to the user privacy and can tarnish a server’s reputation
    * **Recognizability :** Low, as the chat is not the first thing an attack would take a look at if they want to steal a personal information from a user
    
From the total score for each 3 categories, we can reason that User Data possess a greatest risk-factor and should be the number 1 security priority

Reference : 
https://blog.fentress.com/blog/the-importance-of-the-carver-method-in-security-assessments

