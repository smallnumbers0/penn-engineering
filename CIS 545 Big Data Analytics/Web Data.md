**Extracting Content from Web Documents**

- HTML and XML documents are made of nested tags (e.g., ‎`<table>`, ‎`<span>`) with opening/closing pairs and properties (key-value pairs).
- This structure forms a hierarchy—think of it as a tree, with tags nested inside each other.
- 
**Document Object Model (DOM)**

- Libraries like LXML (with its etree parser) can turn HTML/XML into a DOM tree.
- The root is usually the ‎`<html>` tag, with branches for ‎`<head>`, ‎`<body>`, and further nested elements.

**Navigating the DOM Tree**

- You can traverse the tree programmatically to get to specific elements (e.g., from ‎`<html>` to ‎`<body>` to a ‎`<table>`).
- XPath is a powerful tool for navigating and extracting data from this tree.

**XPath Basics**

- XPath expressions work like file paths but for HTML/XML trees.
- ‎`/html` gets the root; ‎`/html/body` drills down further.
- XPath returns sets of matching nodes (not just single nodes).

**Advanced XPath**

- ‎`//span` finds all ‎`<span>` elements anywhere in the document.
- You can filter results using predicates (conditions in square brackets).
- Example: ‎`//span[@class="bday"]` grabs all spans with the class “bday”.
- Attributes are referenced with ‎`@` (e.g., ‎`@class`).

**Extracting Text**

- You can ask for the text content inside a matched element by adding ‎`/text` to your XPath.

- **More Precise Queries**

- You can restrict searches to elements within certain parents (e.g., tables with a specific class).
- Use string functions in XPath to match substrings within attributes.

**Why XPath Matters**

- XPath is great for extracting structured data from messy web pages—essential for “screen scraping.”
- It’s inspired by Unix file paths but returns sets of nodes (sub-trees), not just files.

**Information Extraction**

- XPath is just one approach; there are many tools for pulling structured info from HTML.
- This is a key part of turning web data into something you can analyze.