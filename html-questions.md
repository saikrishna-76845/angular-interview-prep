### **Basic HTML Questions**

1. **What is the difference between HTML and XHTML?**
   - Expected answer: HTML is more lenient and allows some unclosed tags, while XHTML is a stricter version of HTML that follows XML rules and requires proper tag closure and case-sensitivity.

Q. **what are the new tags included in HTML5?**

2. **What are semantic HTML tags? Can you give examples?**
   - Expected answer: Semantic tags clearly describe their meaning in a human- and machine-readable way. Examples: `<article>`, `<section>`, `<header>`, `<footer>`, `<nav>`, `<aside>`.

3. **What is the purpose of the `alt` attribute in the `<img>` tag?**
   - Expected answer: The `alt` attribute provides alternative text for images if the image cannot be displayed or for screen readers to enhance accessibility.

4. **Explain the difference between block-level and inline elements in HTML.**
   - Expected answer: Block-level elements take up the full width available, starting on a new line (e.g., `<div>`, `<p>`, `<h1>`). Inline elements only take up as much width as necessary and do not break the flow (e.g., `<span>`, `<a>`, `<strong>`).

5. **What is the purpose of the `DOCTYPE` declaration in HTML?**
   - Expected answer: The `DOCTYPE` declaration tells the browser which version of HTML the page is written in. It ensures proper rendering and behavior in browsers.

### **Intermediate HTML Questions**

6. **What are the new form input types introduced in HTML5?**
   - Expected answer: HTML5 introduced new input types such as `email`, `tel`, `url`, `date`, `number`, `range`, `search`, `color`, `datetime-local`, and `time`.

7. **What is the difference between the `<div>` and `<span>` tags?**
   - Expected answer: `<div>` is a block-level element used for grouping larger content, while `<span>` is an inline element used for grouping smaller pieces of content or text.

8. **Explain the concept of the "viewport" and how to make a webpage responsive.**
   - Expected answer: The viewport is the visible area of a web page in the browser. To make a webpage responsive, we use the `<meta>` tag with `name="viewport"` and set properties like `width=device-width` and `initial-scale=1`.

9. **What are the new structural elements introduced in HTML5, and why are they important?**
   - Expected answer: HTML5 introduced elements like `<header>`, `<footer>`, `<section>`, `<article>`, and `<nav>`, which help improve the document structure, readability, and SEO.

10. **What is the purpose of the `<meta>` tag in HTML, and what attributes can it have?**
    - Expected answer: The `<meta>` tag provides metadata about the HTML document, such as character encoding, author, and description. Common attributes include `charset`, `name`, `content`, and `http-equiv`.

### **Advanced HTML Questions**

11. **What is the difference between `inline-block` and `block` CSS display properties?**
    - Expected answer: `inline-block` elements behave like inline elements, but they respect width and height properties like block elements. `block` elements start on a new line and take up the full width available.

12. **Can you explain the `data-*` attributes in HTML5?**
    - Expected answer: The `data-*` attributes are used to store custom data in HTML elements. They allow developers to attach extra data to elements without affecting the DOM or page behavior. Example: `<div data-user="123">`.

13. **What is the use of the `async` and `defer` attributes in the `<script>` tag?**
    - Expected answer: 
      - `async`: Scripts are executed as soon as they are downloaded, without blocking the HTML parsing.
      - `defer`: Scripts are executed after the HTML parsing is complete, in the order they appear in the document.

14. **Explain the concept of "HTML5 Web Storage" and its types.**
    - Expected answer: HTML5 Web Storage allows web applications to store data in the browser. There are two types:
      - **LocalStorage**: Stores data with no expiration date and is accessible across sessions.
      - **SessionStorage**: Stores data for the duration of the page session.

15. **What is the Shadow DOM in HTML, and how is it used in web components?**
    - Expected answer: The Shadow DOM is a technique for encapsulating a part of the DOM tree so that it is separate from the main document DOM. It is used in web components to create self-contained components with their own styles and behavior without affecting the rest of the page.

### **Accessibility Question:**

16. **What are the accessibility (a11y) considerations when working with HTML?**
   - Expected answer: Accessibility considerations include using semantic HTML tags, providing text alternatives for non-text content (e.g., `alt` for images), ensuring proper tab navigation, and using ARIA (Accessible Rich Internet Applications) attributes for dynamic content.
