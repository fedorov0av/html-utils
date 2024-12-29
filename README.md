# html-utils

Utilities for working with HTML pages

## Abstractions

### Node

This abstract object represents a DOM Node. It can be a String which represents a DOM text node or a NodeElement object.

### NodeElement

This object represents a DOM element node.

* **tag (String)**
  Name of the DOM element. Available tags: a, aside, b, blockquote, br, code, em, figcaption, figure, h3, h4, hr, i, iframe, img, li, ol, p, pre, s, strong, u, ul, video.
* **attrs (Object)**
  Optional. Attributes of the DOM element. Key of object represents name of attribute, value represents value of attribute. Available attributes: href, src.
* **children (Array of Node)**
  Optional. List of child nodes for the DOM element.

## Installation

Install the package using pip:

```bash
poetry add git+https://github.com/fedorov0av/html-utils.git
```

## Usage

### Example

```
html_content = """
<p><img src="https://...."/></p><pre>TestPRE<br/>TestBR</pre><br/><br/>TestBR2<a href="https://....">TestA</a>. <br/><br/>Test<a href="https://.....">TestA2</a> TesT<br/><br/>Test3<code>TestC</code><p><strong>TestSTRONG</strong></p>
"""
# Create a string of HTML content containing various tags like <p>, <img>, <pre>, <br>, <a>, <code>, <strong>.
# This HTML will be passed to a function for parsing into a data structure.

nodes = html_to_nodes(html_content)
# Convert the HTML content into a data structure (a list of nodes).
# Each node will be a dictionary containing the tag, attributes, and child elements.

json_str = json_dumps(nodes, indent=2)
# Serialize the resulting node structure into a JSON string.
# Use the `indent=2` parameter for pretty formatting, making the output more readable.

html = nodes_to_html(nodes)
# Convert the node structure back into an HTML string.
# This function generates HTML code corresponding to the original HTML content.

nodes_from_js = json_loads(json_str)
# Deserialize the JSON string back into a node structure.
# We get a list of nodes that should be identical to the one generated from the HTML.
```

