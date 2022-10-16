# Document Object Model (DOM)

![](/slides/20_document-object-model-dom.png)

## Nodes & Elements

- `Nodes`

  - `Nodes` are objects that make up the DOM
  - HTML tags are `element nodes`(or just `elements`)
  - text creates `text nodes`
  - attributes create `attribute nodes`

- `Elements`
  - are one type of nodes
  - have special properties and methods to interact with the elements
  - have available methods and properties depend on the kind of element
  - can be selected in various different ways (via JavaScript)
  - can be created and removed via JavaScript

## Querying the DOM

- `querySelector()`, `getElementById()`:

  - 1. return direct object reference to DOM element
  - 2. return single element
  - 3. different ways of querying elements (by CSS selector, by ID)

- `querySelectorAll()`, `getElementsByTagName()`:

  - 1. `querySelectorAll()` returns a `non-live (static) NodeList`, `getXByY` returns `live NodeList`
  - 2. return collections of elements (array-like objects) -> `NodeList`
  - 3. different ways of querying elements (by CSS selector, by tag name, by CSS class)

- `document.body` => selects the `<body>` element node.
- `document.head` => selects the `<head>` element node.
- `document.Element` => selects the `<html>` element node
- `Element.closest('CSSselector')` => traverses the element and its parents (heading toward the document root) until it finds a node that matches the specified CSS selector.
- `Element.previousElementSibling`, `Element.nextElementSibling`: read-only property returns the Element immediately prior or after to the specified one in its parent's children list, or `null` if the specified element is the first one in the list.

## Live Node Lists vs Static Node Lists

- `live` means that changes in DOM are reflected in the collection
- `static` means that only a snapshot of the current state is taken
- use e.g. `getElementsByTagName()` instead of `querySelectorAll()` if you want to have a live connection

## Attributes vs Properties

![](/slides/21_attributes-vs-properties.png)

## Traversing the DOM

- `child`, `descendant`, `parent`, `ancestor`

![](/slides/22_children-descendants-parent-ancestors.png)

![](/slides/23_traversing-the-dom.png)

## Styling DOM elements

![](/slides/24_styling-dom-elements.png)

## Creating and Inserting Elements

![](/slides/25_creating-and-inserting-elements.png)

- `Element.insertAdjacentHTML(position, text)`: parses the specified text as HTML or XML and inserts the resulting nodes into the DOM tree at a specified position.
  - Recommended: instead of `innerHTML` method that replaces whole content between selected HTML tags and forces browser to re-render whole block
- `document.createElement()`: creates the HTML element specified by tagName
- `Node.appendChild(CREATED_OR_EXISTING_ELEMENT)`: adds node to end of list of children of a specified parent node. If given child is a reference to an existing node in the document, `appendChild()` moves it from its current position to the new position (-> since you are holding only a reference to the element object).
- `Element.append()` / `Element.prepend()`: inserts a set of Node objects or string objects a) after the last child OR b) before the first child of the Element. String objects are inserted as equivalent Text nodes.
- `Node.cloneNode(deep)`: returns a duplicate of the node on which this method was called. `deep` controls if the subtree contained in a node is also cloned (-> `true`) or not (-> `false`).