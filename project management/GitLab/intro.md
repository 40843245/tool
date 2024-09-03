# GitLab
## intro
The GitLab is a project management system. One can do these things like in GitHub

+ Create file and directory
+ Upload file
+ Create a repo.

However, there are some small differences and limitations between GitLab and GitHub.

| limitation and difference | GitHub | GitLab |
| :- | :- | :- |
| size of upload file once | max of that is `25MB` | max of that >= `25MB` |
| way to create a repo | fill in name of repo (required) and choose license before creating a repo. | fill in name of project name (required), domain of url (required) |
| url of root in repo | according to name of repo | according to project name and domain. |

About url in GitHub, see [url in GitHub (my Notes at Github)](https://github.com/40843245/tool/blob/main/project%20management/Github/intro.md#url)

## url
+ About root of project.

Format:

```
https://gitlab.com/{domainName}/{projectName}
```

For example:

```
https://gitlab.com/codelover30/GitLabJay30
```

In GitLab, one can know 

+ `codelover30` is the domain.

+ `GitLabJay30` is specified according my project name.

One can know its domain and project name in the following figure.

![image](https://github.com/user-attachments/assets/3f9bb47a-b86a-40a8-8949-1b4eedc30976)

+ About file in a project in viewing mode.

Format:

```
https://gitlab.com/{domainName}/{projectName}/-/blob/main/{directory}/{fileName}?{parameterKeyValuePair}
```

For example:

Take url of my current visiting webpage as example.

```
https://gitlab.com/codelover30/GitLabJay30/-/blob/main/README.md?ref_type=heads
```

One can know

+ `codelover30` is the domain.

+ `GitLabJay30` is specified according my project name.

+ The file is placed in root directory, thus `{directory}` is empty.

+ The file is `README.md` (indicates a markdown language)

+ The parameter `ref_type=heads` indicates that I visit the top the current webpage.

## See Also
See [GitLab (Wiki)](https://en.wikipedia.org/wiki/GitLab)
