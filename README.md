# DString

DString (Dynamic String) is a Python library that provides a simple and intuitive syntax for creating richly styled text in Flet applications. With DString, you can easily add colors, fonts, decorations, gradients, and other text styling effects to your Flet UI components.

## Features

- Simple, intuitive syntax for text styling
- Support for multiple styling parameters
- Color gradients
- Font styling (size, family, weight)
- Text decorations (underline, overline, strikethrough)
- Spacing controls (letter spacing, word spacing)
- Text shadows
- Overflow handling
- Baseline control
- Combination of multiple styles
- Gradient text effects

## Installation

```bash
pip install flet-dstring
```

## Quick Start

```python
import flet as ft
from flet_dstring import DString

def main(page: ft.Page):
    # Create styled text
    styled_text = "d[<f=ff6b6b,b>, <Hello>] d[<f=4ecdc4,i>, <World>]"
    text = DString(styled_text).to_flet()
  
    # Add to page
    page.add(text)

ft.app(target=main)
```

## Syntax

The basic syntax for DString is:

```
d[<style_params>, <text>]
```

Multiple style parameters can be combined using commas. For example:

```
d[<f=ff6b6b,b,size=20>, <Hello World>]
```

### Available Style Parameters

| Parameter | Format                | Description                  | Example               |
| --------- | --------------------- | ---------------------------- | --------------------- |
| f         | XXXXXX                | Foreground color (hex)       | f=ff6b6b              |
| b         | XXXXXX                | Background color (hex)       | b=000000              |
| dc        | XXXXXX                | Decoration color (hex)       | dc=ff0000             |
| size      | N                     | Font size (integer)          | size=20               |
| ff        | name                  | Font family                  | ff=Arial              |
| h         | N                     | Height (float)               | h=1.5                 |
| ls        | N                     | Letter spacing (float)       | ls=2                  |
| ws        | N                     | Word spacing (float)         | ws=10                 |
| dt        | N                     | Decoration thickness (float) | dt=2                  |
| ds        | style                 | Decoration style             | ds=solid              |
| d         | type                  | Decoration type              | d=underline           |
| bl        | type                  | Baseline                     | bl=alphabetic         |
| o         | type                  | Overflow                     | o=ellipsis            |
| w         | weight                | Font weight                  | w=bold                |
| shadow    | color,x,y,blur,spread | Box shadow                   | shadow=000000,2,2,4,0 |
| gs        | XXXXXX                | Gradient start color (hex)   | gs=ff0000             |
| ge        | XXXXXX                | Gradient end color (hex)     | ge=0000ff             |
| i         | -                     | Italic                       | i                     |
| u         | -                     | Underline                    | u                     |
| b         | -                     | Bold                         | b                     |

### Style Values

#### Decoration Types

- underline
- overline
- line-through

#### Decoration Styles

- solid
- double
- dotted
- dashed
- wavy

#### Baseline Types

- alphabetic
- ideographic

#### Overflow Types

- clip
- ellipsis
- fade
- visible

#### Font Weights

- normal
- bold
- w100 through w900

## Examples

### Basic Styling

```python
# Bold red text
"d[<f=ff6b6b,b>, <Bold Red Text>]"

# Italic green text
"d[<f=4ecdc4,i>, <Italic Green Text>]"

# Underlined blue text
"d[<f=45b7d1,u>, <Underlined Blue Text>]"
```

### Colors and Sizes

```python
# Large red text
"d[<f=ff0000,size=20>, <Large Red Text>]"

# Medium green text
"d[<f=00ff00,size=16>, <Medium Green Text>]"

# Small blue text
"d[<f=0000ff,size=12>, <Small Blue Text>]"
```

### Text Decorations

```python
# Solid underline
"d[<d=underline,ds=solid,dc=ff0000>, <Solid Underline>]"

# Dotted overline
"d[<d=overline,ds=dotted,dc=00ff00>, <Dotted Overline>]"

# Wavy strikethrough
"d[<d=line-through,ds=wavy,dc=0000ff>, <Wavy Strikethrough>]"
```

### Gradients

```python
# Basic gradient
"d[<gs=ff0000,ge=0000ff>, <Red to Blue Gradient>]"

# Styled gradient
"d[<gs=ff0000,ge=00ff00,size=24,b>, <Bold Gradient Text>]"
```

### Complex Styling

```python
text = (
    "d[<f=ff6b6b,w=bold,size=32,b=000000>, <Welcome>] to the "
    "d[<f=4ecdc4,i,ff=Arial>, <Extended>] "
    "d[<f=45b7d1,d=underline,ds=wavy,dc=ff0000>, <Styling>] "
    "d[<f=96ceb4,h=1.5>, <System>]!"
)
```

## Configuration

You can customize the default behavior of DString using the `DStringConfig` class:

```python
from flet_dstring import DString, DStringConfig

config = DStringConfig(
    default_color="ff0000",  # Default text color
    default_size=16,         # Default font size
    pattern=r"d\[<(.*?)>, <(.*?)>\]"  # Custom pattern
)

dstring = DString("d[<b>, <Hello>]", config)
```

## Error Handling

DString provides several exception classes for error handling:

- `DStringError`: Base exception for DString-related errors
- `DStringParseError`: Raised when parsing a DString fails
- `DStringStyleError`: Raised when creating a text style fails

## Contributing

Contributions are welcome! Please feel free to submit a Pull Request.

## License

This project is licensed under the MIT License - see the LICENSE file for details.
