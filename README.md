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
# Function Documentation

```
Some additional documentation:
```
## `FC_MakeRect`

**Purpose**: Creates and returns a rectangle structure.

### Parameters:
- `x` (float): The X-coordinate of the top-left corner of the rectangle.
- `y` (float): The Y-coordinate of the top-left corner of the rectangle.
- `w` (float): The width of the rectangle.
- `h` (float): The height of the rectangle.

### Returns:
- `FC_Rect`: A rectangle structure with the given positional and dimensional values.

### Description:
This function initializes and returns an `FC_Rect` structure used for creating rectangles. These can be used in various graphical operations such as rendering text or drawing shapes.

---

## `FC_LoadFont`

**Purpose**: Loads a TrueType font from a specified file into memory.

### Parameters:
- `font` (FC_Font*): A pointer to the font object to be loaded.
- `renderer` (SDL_Renderer*): The SDL renderer used for loading the font.
- `fontPath` (const char*): Path to the TrueType font file.
- `fontSize` (int): The desired size of the font.
- `color` (SDL_Color): The color of the font.
- `style` (int): Style flags for the font (e.g., bold, italic).

### Returns:
- `FC_Font*`: A pointer to the newly loaded font object.

### Description:
This function loads a font from a specified TrueType file and returns a pointer to the loaded font object. It also handles setting the font style and color.

---

## `FC_Draw`

**Purpose**: Renders a string of text at specified coordinates using a given font.

### Parameters:
- `font` (FC_Font*): A pointer to the font object used to render the text.
- `renderer` (SDL_Renderer*): The SDL renderer used for drawing.
- `x` (float): The X-coordinate where the text will be rendered.
- `y` (float): The Y-coordinate where the text will be rendered.
- `text` (const char*): The string of text to be rendered.

### Returns:
- `void`: This function does not return any value.

### Description:
This function renders a text string at the given position using the provided font and color. It is capable of rendering UTF-8 encoded text.

---

## `FC_FreeFont`

**Purpose**: Frees the memory used by a font object.

### Parameters:
- `font` (FC_Font*): A pointer to the font object to be freed.

### Returns:
- `void`: This function does not return any value.

### Description:
This function frees the memory allocated for a font object previously loaded using `FC_LoadFont`. It is important to call this function to avoid memory leaks.

---

## `FC_MakeColor`

**Purpose**: Creates an SDL_Color structure with the given RGBA values.

### Parameters:
- `r` (Uint8): The red component of the color (0-255).
- `g` (Uint8): The green component of the color (0-255).
- `b` (Uint8): The blue component of the color (0-255).
- `a` (Uint8): The alpha (transparency) component of the color (0-255).

### Returns:
- `SDL_Color`: The color structure with the specified RGBA values.

### Description:
This function creates an SDL_Color structure that can be used to define the color of fonts, shapes, or other graphical elements in the SDL rendering context.

---

## `FC_FreeText`

**Purpose**: Frees the memory used by a text object.

### Parameters:
- `text` (FC_Text*): A pointer to the text object to be freed.

### Returns:
- `void`: This function does not return any value.

### Description:
This function frees the memory allocated for a text object created by `FC_LoadText`. It is important to call this function to avoid memory leaks when you are done with the text object.
