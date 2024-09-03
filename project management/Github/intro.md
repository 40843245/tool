# Github
## intro
In GitHub, one can manage repo which can contain files or project.

## url
I only discuss that the url in viewing mode. One can easily to observe format of url in editing mode.

Format:

```
https://github.com/{accountName}/{repoName}/tree/main/{directory}/{fileName}
```

> [!NOTE]
> NOTICE that
>
> + the url uses [`percent-encoding`](https://en.wikipedia.org/wiki/Percent-encoding)
>   
> + `{fileName}` contains the file name and file extension.
>
> + `{directory}` indicates the directory from root of repo to the file name (exclusive to file name).

For example:

Take url of this file as example.

```
https://github.com/40843245/tool/blob/main/project%20management/GitLab/intro.md
```

In GitHub, one can know

+ `40843245` is my account name.

+ `tool` is my repo name.
  
+ The file is placed in `project management/GitLab` directory. The result of percent encoding of `project managemant/GitLab` is `project%20management/GitLab`

+ The file name is `intro.md` (which indicates markdown language)


