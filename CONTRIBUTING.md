## Contributing to the Brainery

We'd love to accept your contributions to the project. There are just a few small guidelines you need to follow before submitting a note.

## Pull Request Process

1. Put your note into a Pull Request and submit it to https://github.com/dwarvesf/brain.
2. Ensure to prefix your **pull request naming** AND **initial commit naming** with the main tag and folder it is associated to. This is to allow us to easily find and categorize commits to ping and post on our changelogs. For instance:

- `engineering: Edsger Dijkstra interview`
- `writing: question tree`
- `communication: Linguistics`

3. Request any one of these reviewers to check and proofread your submitted note:

- @zlatanpham
- @monotykamary
- @trankhacvy
- @duynglam

4. You may merge the Pull Request in once you have the sign-off of our reviewers, or if you do not have permission to do that, you may request the reviewer to merge it for you.

> If it happens that you aren't familiar with using Github, simply join our [Discord](https://discord.com/invite/Y2vvH9rQE4) and drop your note into a relevant discussion channel. Our team will edit and submit the note for you.

## Manual of style

### Writing, semantics, grammar

We aren't actually too strict on grammar or semantics in your notes. Our only requirement is that it is easy to read and is relatively skimmable. As for note structure, we will follow Wikipedia and previous SEO standards:

1. Each page should only have one H1 `#` header.

2. All subsequent headers should be nested as H2 `##` headers.

3. Avoid separating topics with `---` unless absolutely necessary.

**Notes on Plagiarism**: Please don't plagiarize. If you have similar ideas to the article you're referencing your notes from, at the very least paraphrase or compose your notes in a way that makes it your own.

### Folder structure

1. We prefer to use 1-level folders unless necessary. If you feel that your content belongs to a specific nested folder or would like to create one, we'll have a look at it.

2. Any notes or articles in the folder should also have the related tag mentioned in the metadata. For instance, if the note is placed `Writing` folder, the metadata must have at least:

- ```md
  ---
  tags: writing, ...
  ---
  ```

3. All notes should have metadata pertaining to the content of the note, its author, and date of publish (YYYY-MM-DD):

- ```md
  ---
  tags: engineering, database, transaction
  author: Nguyen Xuan Anh
  github_id: monotykamary
  date: 2022-08-23
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

## Editing tools

As notes are based on the markdown format, you can literally use any text editor to write down your thought. However, we started the Second Brain with [Obsidian](https://obsidian.md/) and most of us continue using it daily for note taking. We recommend you to use Obsidian too since the tool offers a robust way of linking documents together as well as providing an incredible searching experience.

## Map of Content (MoC) Management

If you are responsible for managing an MoC, make sure to occasionally check in on what areas of interest within a topic is worth connecting and making sure entries have their appropriate tags.
