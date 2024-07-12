# pymddoc
## quickstart 
### installation
To install py-md-doc, one can use pip3.

#### installation with pip
For newer version, one may install py-md-doc with pip3.

In terminal, type the following command and click Enter.

    pip3 install py-md-doc

For older version, one may install py-md-doc with pip.

In terminal, type the following command and click Enter.

    pip install py-md-doc

NOTICE that before type, ensure system environment variables PATH about path of pip is set. If NOT, set PATH and reboot the device to make the change effect.

## Intro
pymddoc* is a python package for creating markdown documents with embedded code snippets.

*: name is a work in progress

## How to use
1. create a .py script that will contain code to generate the document.
2. create a DocMaker object by calling Document with desired templates and metadata.
3. add markdown using the .markdown() method
4. add code snippets using the context manager returned by the .snippet() method
5. render the document to markdown or html






