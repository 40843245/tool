# GitBook
## [overview](https://docs.gitbook.com/content-editor/overview)
GitBook has a powerful block-based editor that allows you to seamlessly create, update, and enhance your content.

## integration
### [build your first integration](https://developer.gitbook.com/integrations/integrations)
#### [build your first integration with CLI](https://developer.gitbook.com/integrations/integrations#cli-quickstart)
To build your first integration with CLI, follow these steps.
1. Install the GitBook CLI
2. Authenticate with your account (with GitBook API token)
3. Bootstrap your app 

## authentication
### authenticate with your account with GitBook API token
To authenticate with your account (with GitBook API token), follow these steps.
1. create an API token in your GitBook.com in [Developer Settings](app.gitbook.com/account/developer).
2. add `Create new token` Button.
3. then run these commands in GitBook CLI.

```
gitbook auth
```

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

#### steps:
To import files from local device, follow these steps.
1. sign in GitBook.
2. create your GitBook notes.
3. in the left panel, under space option, add `+` icon.

![image](https://github.com/user-attachments/assets/076680a9-1ed2-4637-a73b-5cf4a1f6a634)

4. select `Import Content` option.
5. choose file format you want to import.
6. select the file from your local device.
7. click `Import file` button.
8. wait until success.

#### Demo
About demo, see my YT video - [import files from local device](https://www.youtube.com/watch?v=t96v9beAdeI)
### Importing via Git Sync
If you want to import large amounts of content, you can use our Git Sync feature, which has no limitation on the amount of content that can be imported. 

To import using Git Sync, you’ll first need to add your content to a GitHub or GitLab repository (or folder if you're using a monorepo setup - as Markdown files). If your current tool does not support Markdown export, various online tools can assist with conversion from other formats, such as PDF, HTML, etc.

Once you’ve set up your Git repository, simply set up a Git Sync integration in your GitBook organization. Be sure to select the direction GitHub -> GitBook when choosing the initial sync direction. 

#### Import files from GitHub
> [!NOTE]
> Prequisite:
>
> + Github Account
> + GitLab Account (You can only sign it with your Github account.)
> + GitHub repos in the account

To import files from GitHub, follow these steps:
1. [Enable your Git sync](https://docs.gitbook.com/integrations/git-sync/enabling-github-sync)
2. 

#### Import files from GitLab
