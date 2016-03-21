py-json-lxml
============

Convert [JSON](http://www.w3schools.com/json/) to an [lxml.etree Element](http://lxml.de/tutorial.html#the-element-class) and back so that [XPath](http://www.w3schools.com/xsl/xpath_syntax.asp) can be used.

## Installation

To install json-xml in your Python environment, make sure that [pip](https://pip.pypa.io/en/stable/quickstart/) is installed, and run:

```
pip install json-xml
```

## Usage

Load a json file into an element structure.

```
from json_lxml import element

# Load the file into a dict
with open("potatoes.json", "r") as _f:
    _json_dict_ = json.load(_f)
    
# Generate the element tree, there has to be a top node, let's call it "top"
_tree_element = _element("top", _json_dict_))
```

Do an XPath selection:
* don't forget to include the top node we previously named "top"
* json array items becomes "item" nodes, so this is how you list and then select from a json array

```
_second_potato = _tree_element.xpath("/top/vegetableGallery/potatoes/item[position()=2]")
```

Writing the data in the _second_potato element to another JSON file:

```
from json_lxml import value
# Generate a dictionary from the tree
_json_out = value(_second_potato)
with open("potato_2.json", "w") as _f:
    json.dump(_json_out,_f) 
```


# Status

Early development, but works.


# Todo
  - Unit testing
  - CLI
  - Example files
