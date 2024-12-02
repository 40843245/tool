# Maven 
## intro
`Maven command prompt` is a command line prompt, like `Dos command prompt` in Windows. One can do task simply through the command in `Maven command prompt`. (for convenience, we will call `Maven command prompt` as `Maven` in this article)

## abstract
In this article, I will simply talk how to download, install, then setup the environment setting. Next, I will discuss how to do some fundamental tasks by `Maven command`. 

Then, I will take a deep dive in the structure of `Maven`.

Finally, I will simply list and introduce some common `Maven commands`.

## startup
### check system requirements
Before downloading, one has to check system requirements. System requirement is shown at [`Downloading Apache Maven 3.9.9` (official website)](https://maven.apache.org/download.cgi?.)

### download 
You can download it by click the link in `link` field at [`Downloading Apache Maven 3.9.9` (official website)](https://maven.apache.org/download.cgi?.). Shown as following figure.



### Creating a Project in MVN
Use `mvn archetype:generate` command to generate a new project.

For example, if you enter the following command.

```
mvn archetype:generate -DgroupId=org.yourcompany.project -DartifactId=application
```

Maven will obtain a list of all available archetypes, ask you for some configuration, and generate a working project. 
