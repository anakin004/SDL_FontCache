# SDL_FontCache
A generic font caching C library with loading and rendering support for SDL.

SDL_FontCache loads, caches, and renders TrueType fonts using SDL_ttf.  
It fully supports UTF-8 strings and includes some utility functions for manipulating them.

An example using SDL_Renderer:

```
FC_Font* font = FC_CreateFont();  
FC_LoadFont(font, renderer, "fonts/FreeSans.ttf", 20, FC_MakeColor(0,0,0,255), TTF_STYLE_NORMAL);  

...

FC_Draw(font, renderer, 0, 0, "This is %s.\n It works.", "example text"); 
 
...

FC_FreeFont(font);
```
functions:
  - name: FC_MakeRect
    purpose: Creates and returns a rectangle structure.
    parameters:
      - name: x
        type: float
        description: The X-coordinate of the top-left corner of the rectangle.
      - name: y
        type: float
        description: The Y-coordinate of the top-left corner of the rectangle.
      - name: w
        type: float
        description: The width of the rectangle.
      - name: h
        type: float
        description: The height of the rectangle.
    returns:
      type: FC_Rect
      description: A rectangle structure with the given positional and dimensional values.
    description: |
      This function initializes and returns an `FC_Rect` structure used for creating rectangles. These can be used in various graphical operations such as rendering text or drawing shapes.

  - name: FC_LoadFont
    purpose: Loads a TrueType font from a specified file into memory.
    parameters:
      - name: font
        type: FC_Font*
        description: A pointer to the FC_Font structure that will hold the font data.
      - name: renderer
        type: SDL_Renderer*
        description: The SDL renderer for rendering the font.
      - name: filename
        type: const char*
        description: The path to the TrueType font file.
      - name: point_size
        type: int
        description: The size of the font in points.
      - name: color
        type: SDL_Color
        description: The color of the font.
      - name: style
        type: int
        description: The style of the font (e.g., normal, bold, italic).
    returns:
      type: int
      description: Returns 0 if successful, or a negative error code if loading failed.
    description: |
      This function loads a TrueType font from the specified file and creates a texture for rendering. It stores the font information in the provided `FC_Font` structure, which can then be used to render text with the given settings.

  - name: FC_Draw
    purpose: Renders a text string to the screen at a specific position.
    parameters:
      - name: font
        type: FC_Font*
        description: A pointer to the FC_Font structure that holds the font to render.
      - name: renderer
        type: SDL_Renderer*
        description: The SDL renderer used for rendering the text.
      - name: x
        type: float
        description: The X-coordinate of the position where the text should be drawn.
      - name: y
        type: float
        description: The Y-coordinate of the position where the text should be drawn.
      - name: text
        type: const char*
        description: The text string to be rendered. Can include format specifiers for dynamic content.
    returns:
      type: void
      description: This function does not return a value.
    description: |
      This function draws a formatted string at the specified coordinates (`x`, `y`) using the provided font and renderer. It supports formatted text, allowing you to dynamically pass in additional arguments, such as strings or numbers, to be inserted into the text.

  - name: FC_FreeFont
    purpose: Frees the memory allocated for a font.
    parameters:
      - name: font
        type: FC_Font*
        description: A pointer to the FC_Font structure that should be freed.
    returns:
      type: void
      description: This function does not return a value.
    description: |
      This function frees the memory allocated for a font object, ensuring that no memory leaks occur. It should be called when you no longer need the font.
