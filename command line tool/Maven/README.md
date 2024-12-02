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
You can download it by click the link in `link` field at [`Downloading Apache Maven 3.9.9` (official website)](https://maven.apache.org/download.cgi?.). 

Framed with red box as [this figure](https://github.com/40843245/tool/blob/main/command%20line%20tool/Maven/attachment/figure/Download%20Apache-Maven%20project.png).

### install
After downloading a zip file, 

1. move the zip in `C:\` (in fact, you can move it to anywhere but you have to remember the file location, you will use it later)
2. unzip the zip file.
3. after unzipping, you may see, in the unzipped file, there is exactly one folder (may be named as `apache-maven-3.9.9`) that contains many folders. The outer-side folder is redundent. And so, move `apache-maven-3.9.9` folder to `C:\` in this example. (according to the file location you moved to, mentioned in step 1)

> [!NOTE]
> Like many zip file, it may contain exactly one folder and the outer-side folder is redudent, so one has to move it. 

4. As in the folder `...\apache-maven-3.9.9\bin`, there is `mvn` execution file, to make `mvn` command in shell available to use. You have to set the system environment variable.
5. check the version.
### Set system environment variable
As in the folder `...\apache-maven-3.9.9\bin`, there is `mvn` execution file, to make `mvn` command in shell available to use. You have to set the system environment variable. 

To do that, add the `...\apache-maven-3.9.9\bin` in system environment variable -- `PATH`

### check the version
You can check the version of `mvn` by typing these command in shell.

```
mvn -v
```

If successfully, you may see the following output.

```
Apache Maven 3.9.9 (8e8579a9e76f7d015ee5ec7bfcdc97d260186937)
Maven home: /opt/apache-maven-3.9.9
Java version: 1.8.0_45, vendor: Oracle Corporation
Java home: /Library/Java/JavaVirtualMachines/jdk1.8.0_45.jdk/Contents/Home/jre
Default locale: en_US, platform encoding: UTF-8
OS name: "mac os x", version: "10.8.5", arch: "x86_64", family: "mac"
```

Stated more in [`Installing Apache Maven` (official website)](https://maven.apache.org/install.html)

## fundamental task
### look at command help at command prompt
To look at command help at command prompt, type the following command.

```
mvn -h
```

You will see help of all `mvn` commands (including the flag of `mvn` command). The console will output like this:

[`command help through mvn -h.txt`](https://github.com/40843245/tool/blob/main/command%20line%20tool/Maven/attachment/shell/output/command%20help%20through%20mvn%20-h.txt)

Stated more in [`Running Apache Maven` (official website)](https://maven.apache.org/run.html)


### creating a Project in MVN
Use `mvn archetype:generate` command to generate a new project.

For example, if you enter the following command.

```
mvn archetype:generate -DgroupId=org.yourcompany.project -DartifactId=application
```

Maven will obtain a list of all available archetypes, ask you for some configuration, and generate a working project. 

The console will print the output like this: [`create a new project through mvn command.txt`](https://github.com/40843245/tool/blob/main/command%20line%20tool/Maven/attachment/shell/output/create%20a%20new%20project%20through%20mvn%20command.txt)

### simplify the process of creating a project in MVN

You can also simplify your choice by providing a _archetypeArtifactId_ property to pick the archetype in advance. 

For example, `-DarchetypeArtifactId=maven-archetype-webapp` will help you create a Java web app project.

You can also package your MVN project into an archetype for the future use with the following command:

```
mvn archetype:create-from-project
```
