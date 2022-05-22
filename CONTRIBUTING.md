# Contributing to the brainery

## Pull Request Process
1. Ensure to prefix your Pull Request names with the main tag and folder it is associated to. This is to allow us to easily find and categorize commits to post on our changelogs. For instance:
  - `engineering: Edsger Dijkstra interview `
  - `writing: question tree`

2. Request any one of these reviewers to check and proofread your submitted note:
  - @zlatanpham
  - @monotykamary

3. You may merge the Pull Request in once you have the sign-off of our reviewers, or if you do not have permission to do that, you may request the reviewer to merge it for you.


## Manual of style

### Writing, semantics, grammar

We aren't actually too strict on grammar or semantics in your notes. Our only requirement is that it is easy to read and is relatively skimmable. As for note structure, we will follow Wikipedia and previous SEO standards:

1. Each page should only have one H1 `#` header. All subsequent headers should be nested as H2 `##` headers.

**Notes on Plagiarism**: Please don't plagiarize. If you have similar ideas to the article you're referencing your notes from, at the very least paraphrase or compose your notes in a way that makes it your own.

### Folder structure

1. We only have 1-level folders; we don't use nested folders, so no need to create them. They may make the main folder a bit messy to find articles, but it eases the barrier to entry for new writers.

2. Any notes or articles in the folder should also have the related tag mentioned in the metadata. For instance, if the note is placed `Writing` folder, the metadata must have at least:
  - ```md
    ---
    tags: writing, ...
    ---
    ```

3. All notes should have metadata pertaining to the content of the note and its author:
  - ```md
    ---
    tags: engineering, database, transaction
    author: Nguyen Xuan Anh
    ---
    ```


### How to do referencing

1. Use H2 `##` for the heading for `References` in your notes.

2. Since we aren't strict in creating a full-fledged bibliography for notes, just pasting the link is ok. You may also use the markdown to label the link for accessibility. For example:

  - ```md
    ## Reference
    - https://statecharts.dev/state-machine-state-explosion.html
    ```

  - ```md
    ## Reference
    - [Wikipedia - Blockchain oracle](https://en.wikipedia.org/wiki/Blockchain_oracle#:~:text=A%20blockchain%20oracle%20is%20a,that%20decentralised%20knowledge%20is%20obtained.)
    - [https://chain.link/education/blockchain-oracles](https://chain.link/education/blockchain-oracles)
    - [https://coin98.net/what-is-blockchain-oracle](https://coin98.net/what-is-blockchain-oracle)
    ```
