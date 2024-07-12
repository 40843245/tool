# API
## function
### markdown.markdown
#### Intro
    
    Convert a markdown string to HTML and return HTML as a Unicode string.
    
    This is a shortcut function for [Markdown][markdown.Markdown] class to cover the most basic use case. 
    
    It initializes an instance of [Markdown][markdown.Markdown], loads the necessary extensions and runs the parser on the given text.
    
#### Syntax

    (function) def markdown(
        text: str,
        **kwargs: Any
    ) -> str
    
#### Arguments     

    text: Markdown formatted text as Unicode or ASCII string.
    
    Keyword arguments:
        **kwargs: Any arguments accepted by the Markdown class.
