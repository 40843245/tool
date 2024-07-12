# API
commonly used API as follows.

## pymddoc
### functoion
#### Document
##### Intro
Construct a new docmaker. One can consider it as a constructor.

##### Syntax

    (function) def Document(
        title: str | None = None,
        subtitle: str | None = None,
        author: str | None = None,
        date: str | datetime | None = None,
        other_metadata: Dict[str, str] | None = None,
        snippet_template: SnippetTemplateType | None = None
    ) -> DocMaker

###### Example

    doc = pymddoc.Document(
        title = 'My Document',
        date = 'Nov 20, 2023',
    )

### method
#### markdown
##### Intro
    Add markdown to the document.
    
##### syntax
    (method) def markdown(
        self: Self@DocMaker,
        text: str,
        indent: str = ''
    ) -> Markdown

#### snippet
##### Intro
    Context manager for adding code snippets to the document.

##### Syntax

    (method) def snippet(
        self: Self@DocMaker,
        frame: FrameInfo,
        template: SnippetTemplateType | None = None,
        print_stdout: bool = False
    ) -> SnippetCtx

#### render_markdown
##### Intro
    Render the existing document into markdown.

##### Syntax

    (method) def render_markdown(
        self: Self@DocMaker,
        include_yaml: bool = True
    ) -> str

#### render_html
##### Intro
    Render the document to html.
    
##### Syntax
    (method) def render_html(**markdown_kwargs: Any) -> str
  


