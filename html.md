# HTML

## Data-Value attributes

 `"data-*"` attributes are custom data attributes that can be added to HTML elements to store additional information. These attributes can be used to store data that is not visible to the user but can be accessed by JavasScript.
 
```html
<div class="product" data-product-id="12345" data-product-name="Example Product" data-price="49.99">
    <!-- Other product information and content -->
</div>
```

Access in JavaScript using the dataset property:

```javascript
var productElement = document.querySelector(".product");
var productId = productElement.dataset.productId;
console.log(productId);
```

## HTML5 semantic elements

HTML5 introduced several new semantic elements to improve the structure and semantics of web documents. These elements help clarify the purpose of different parts of a web page and provide better accessibility and search engine optimization. They don't have inherent styles on their own, but they can be styled using CSS.

Here are some of the main HTML5 semantic elements:

| Element       | Description                                                    |
|---------------|----------------------------------------------------------------|
| `<header>`    | Container for introductory content or navigational links.     |
| `<nav>`       | Section of a page containing navigation links.                |
| `<main>`      | Main content of an HTML document (only one per page).         |
| `<article>`   | Self-contained composition, e.g., blog post or news article.   |
| `<section>`   | Standalone section within a document, often with a heading.   |
| `<aside>`     | Content tangentially related to the surrounding content.      |
| `<footer>`    | Footer of a section or a page, often containing metadata.     |
| `<figure>`    | Content referenced from the main content, e.g., images.      |
| `<figcaption>` | Caption or legend for a `<figure>` element.                 |
| `<time>`      | Represents a specific period in time, date, or time of day.   |
| `<mark>`      | Highlighted or marked text for reference.                     |
| `<details>`   | Disclosure widget for revealing additional content.           |
| `<summary>`   | Summary or label for content hidden within a `<details>`.     |
| `<menu>`      | List of commands, often used for context or navigation menus. |
