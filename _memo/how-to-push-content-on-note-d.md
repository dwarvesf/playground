---
tags:
  - content
  - instructions
  - guideline
title: How to push content on memo.d.foundation
date: 2024-03-04
description: This is a guide on how to setup your environment and settings to push content to our notes website, note.d.foundation.
authors:
  - minhcloud
menu: memo
type: memo
hide_frontmatter: false
pinned: true
hide_title: false
---

## Before edit or create a new post
Before you can create a new post, please make sure that you have finished setting up the environment for editting memo in this [post](https://memo.d.foundation/playground/_memo/how-to-set-up-environment-for-editing-memo/), and you have the right access and edit the repository note.d.foundation. 

Everytime you want to edit or create a new post, please make sure that the data of your local files is up-to-date by going to Source Control and Sync all the changes in the note.d.foundation repository.

![](assets/how-to-push-content-on-note-d_how-to-push-content-on-memo-1.webp)

## Create a post 
1. Choose a folder that you want to nest your post in.
2. Click to the icon New files, and enter the name of new file. Remember to add the suffix `.md` after the file name to segment the type of file. 

![](assets/how-to-push-content-on-note-d_how-to-push-content-on-memo-5.webp)

3. Insert the code for metadata on the top of your post. 

```md
---
tags: 
  - [tag1]
  - [tag2]
  - [tag3]
title: [The title]
date: yyyy-mm-dd
description: [your description]
authors: [your name]
menu: [folder]
type: null
hide_frontmatter: false
---
```

4. Start editing your post below metadata section.
5. After finish editing, save the file by `Cmd+S`.
6. To preview all the changes on website, open devbox by running command `devbox shell` in Terminal. Then use command `make watch-run` and open the localhost link. 

![](assets/how-to-push-content-on-note-d_how-to-set-up-environment-for-editing-memo-2.webp)

## Review process
After you finish editing the post, you need to capture the whole page of your post on local link, then send it to your supervior and @anna to review. 

We suggest you to use Scrolling Capture of [Cleanshot](https://cleanshot.com/).

## Commit changes 
After editing, your post is only saved on local files. To post it to memo, you will need to create a request for administrator to approve. Before creating a request, you need to commit all changes first:
1. Go to Source control section.
2. Sync all changes in note.d.foundation and in the branch you edited.
3. Stage all changes of the branch you edited.
4. Name the commit and press Commit button.

![](assets/how-to-push-content-on-note-d_how-to-push-content-on-memo-2.webp)

## Create Pull Request 
Now, you should go to your [Github](https://github.com/) and log in. After that follow the guideline to create pull request: 

1. Open the profile dropdown and open Your repositories section.

![](assets/how-to-push-content-on-note-d_how-to-push-content-on-memo-3.webp)

2. Choose the branch that you have edited.
3. Open the pull request list.

![](assets/how-to-push-content-on-note-d_how-to-push-content-on-memo-4.webp)

4. Choose the commit and Create the pull request.


Now all you need is waiting for admin to review your request! 
