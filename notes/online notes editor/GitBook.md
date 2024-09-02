# GitBook
## [overview](https://docs.gitbook.com/content-editor/overview)
GitBook has a powerful block-based editor that allows you to seamlessly create, update, and enhance your content.

## import
There are several ways to import.

+ [Using our import tool](https://docs.gitbook.com/content-editor/import#using-our-import-tool): Import files from local device
+ [Using Git Sync](https://docs.gitbook.com/content-editor/import#importing-via-git-sync): Import repos from GitHub or GitLab.

### Using our import tool
#### supported format
GitBook supports imports from websites or files in the following formats:

+ Markdown (.md or .markdown)
+ HTML (.html)
+ Microsoft Word (.docx)
+ Confluence
+ Notion
+ GitHub Wiki
+ Google Docs
+ Quip
+ Dropbox Paper

#### limitations
GitBook currently has the following limits for imported content:

+ The maximum number of pages that can be uploaded in a single import is 20.
+ The maximum number of files (images etc.) that can be uploaded in a single import is 20.

### Importing via Git Sync
If you want to import large amounts of content, you can use our Git Sync feature, which has no limitation on the amount of content that can be imported. 

To import using Git Sync, you’ll first need to add your content to a GitHub or GitLab repository (or folder if you're using a monorepo setup - as Markdown files). If your current tool does not support Markdown export, various online tools can assist with conversion from other formats, such as PDF, HTML, etc.

Once you’ve set up your Git repository, simply set up a Git Sync integration in your GitBook organization. Be sure to select the direction GitHub -> GitBook when choosing the initial sync direction. 
