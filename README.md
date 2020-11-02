# IDM Senior Project 2021 Contract Book

## Setup local dev

- Fork this repo to your account
- Clone repo to your machine via GitHub deskop or command line

```bash
git clone https://github.com/account/repo.git
// you can find this URL by clicking the green 'code' button on the homepage of your repo
```

- Globally install Docsify CLI (note: requires NodeJS to be installed)

```bash
npm i docsify-cli -g
```

- To launch the site for local dev run

```bash
docsify serve docs
```

## General Guidelines

The Contract Book is documentation of how we are/will do things as well as the materials/components we will use to do things. The purpose of this is *NOT* to document things that we have done. For documentation the UX process and activities we have completed please contribute to the [UX Documentation Repository](https://github.com/IDM-SP-2021/ux-documentation).

Each page should be written in Markdown and the file must be kept in the respective directory for it's section (UI, UX, or Dev) and then linked to in `_sidebar.md`

The top level heading of each document should match or be similar to the link text in the sidebar. Please note that the filename should be as short as possible while still conveying the contents of the document. This could match the top level heading of the document, but if the heading is long *do not* name the document the full length of the heading.

All second level headings will appear in the sidebar when a page is active. If you do not wish to include a specific second level heading in the sidebar, first consider if it should be a second level heading or better organized as a third or lower level heading, if deemed it should be a second level heading include `<!-- {docsify-ignore} -->` on the same line as the heading. If you wish to not include all subheadings on a page in the sidebar you may include `<!-- {docsify-ignore-all} -->` on the same line as the top level heading.

```markdown
## Some Heading <!-- {docsify-ignore} -->
```

All headings should follow standard capitalization rules.

Break the content up into logical sections as much as possible. Any significant sections should be separated by a horizontal rule. If a section is lenghty, this is a candidate for having it's own page in the Contract Book.

Any codeblocks must be fenced and include a language declaration.

```markdown
    ```css
    .someClass {
      color: red;
    }
    ```
```

For any formatting guidelines please consult the the [Docsify documentation](https://docsify.js.org/#/)

## Contribution Guidelines

***All changes must be submitted via pull request***

**Please limit the changes per pull request as much as possible.**
  i.e. "Update style guide information to include buttons" or "Update research methodoligies for interviews"

- Name of the PR should be as desriptive of the work as possible
- Include a two to three sentence summary of the changes made in the comments section of the PR
- PRs *must* request a reviewer to be submitted

## Reviewing

If any General or Contribution Guidelines are not explicitly followed, the reviewer *must* reject the PR and send it back to the team member that submitted it for correction.
