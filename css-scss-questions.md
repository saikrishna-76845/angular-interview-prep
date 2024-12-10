### **CSS Interview Questions**

#### **Basic CSS Concepts**

1. **What is the difference between `class` and `id` selectors in CSS?**
   - **Expected Answer:** 
     - `class` selectors can be used on multiple elements, and are generally used for styling a group of elements. They are defined using a period (`.`) before the class name.
     - `id` selectors are unique and are used to style a single, specific element on the page. They are defined using a hash (`#`) before the ID name.

     Example:
     ```css
     .button { color: red; }  /* class selector */
     #header { color: blue; }  /* id selector */
     ```

2. **What is the purpose of the `box-sizing` property in CSS?**
   - **Expected Answer:** The `box-sizing` property controls how the width and height of elements are calculated. When set to `border-box`, padding and border are included within the element's width and height, rather than expanding the element’s size.

     Example:
     ```css
     .element {
       box-sizing: border-box;
       width: 100px;  /* Includes padding and border in the total width */
     }
     ```

3. **What is the difference between `inline`, `block`, and `inline-block` elements?**
   - **Expected Answer:**
     - `inline`: Elements only take up as much width as their content, and do not break onto a new line (e.g., `<span>`).
     - `block`: Elements take up the full width available and start on a new line (e.g., `<div>`).
     - `inline-block`: Elements are inline but can have block-level styles applied (e.g., setting width and height). They do not break onto a new line.

     Example:
     ```css
     .inline { display: inline; }
     .block { display: block; }
     .inline-block { display: inline-block; }
     ```

4. **What is the `z-index` property, and how does it work?**
   - **Expected Answer:** The `z-index` property controls the stack order of elements. Higher values appear in front of elements with lower values. It only works on elements that have a position other than `static`.

     Example:
     ```css
     .element1 {
       position: absolute;
       z-index: 10;
     }
     .element2 {
       position: absolute;
       z-index: 5;
     }
     ```

5. **What is a CSS Flexbox, and how does it work?**
   - **Expected Answer:** Flexbox is a layout module that allows you to align and distribute space within a container, even when the size of the items is unknown or dynamic. It provides powerful alignment capabilities along the main and cross axes (horizontal and vertical).

     Example:
     ```css
     .container {
       display: flex;
       justify-content: space-between;  /* Distribute items evenly */
     }
     ```

---

#### **Intermediate CSS Concepts**

6. **What is the difference between `position: relative` and `position: absolute`?**
   - **Expected Answer:**
     - `position: relative` positions an element relative to its normal position. It allows you to offset an element using the `top`, `right`, `bottom`, and `left` properties.
     - `position: absolute` positions an element relative to its nearest positioned ancestor (i.e., an ancestor element with a position other than `static`).

7. **Explain the concept of CSS Grid Layout and how it differs from Flexbox.**
   - **Expected Answer:** CSS Grid Layout is a two-dimensional layout system that allows you to design complex layouts with rows and columns. Unlike Flexbox, which is one-dimensional (it handles either rows or columns), Grid can manage both dimensions simultaneously.

     Example:
     ```css
     .grid-container {
       display: grid;
       grid-template-columns: repeat(3, 1fr);
       grid-gap: 10px;
     }
     ```

8. **What is the difference between `visibility: hidden` and `display: none`?**
   - **Expected Answer:**
     - `visibility: hidden` hides an element, but the element still takes up space in the layout.
     - `display: none` completely removes the element from the document flow, meaning it no longer occupies any space in the layout.

9. **What is the `@media` rule in CSS?**
   - **Expected Answer:** The `@media` rule allows you to apply different styles to different screen sizes or devices. It is commonly used for responsive design to adjust layouts based on the viewport size.

     Example:
     ```css
     @media (max-width: 600px) {
       .container {
         flex-direction: column;  /* Stack items vertically on small screens */
       }
     }
     ```

10. **What is the difference between `em` and `rem` units in CSS?**
    - **Expected Answer:**
      - `em` is relative to the font size of the parent element, meaning it is context-dependent.
      - `rem` (root em) is relative to the font size of the root element (`<html>`), making it more predictable and consistent throughout the document.

---

#### **Advanced CSS Concepts**

11. **What is the `calc()` function in CSS, and how do you use it?**
    - **Expected Answer:** The `calc()` function allows you to perform calculations in CSS for property values, such as widths, margins, or padding. It supports addition, subtraction, multiplication, and division.

      Example:
      ```css
      .element {
        width: calc(100% - 20px);
      }
      ```

12. **What are CSS pseudo-classes and pseudo-elements? Give examples.**
    - **Expected Answer:**
      - **Pseudo-classes** are used to define the special state of an element (e.g., `:hover`, `:focus`, `:nth-child`).
      - **Pseudo-elements** are used to style a part of an element (e.g., `::before`, `::after`, `::first-letter`).

      Example:
      ```css
      a:hover { color: red; }  /* pseudo-class */
      p::after { content: "End"; }  /* pseudo-element */
      ```

13. **Explain the concept of `CSS Variables` and how to use them.**
    - **Expected Answer:** CSS Variables (custom properties) allow you to define reusable values that can be applied throughout a stylesheet. They are particularly useful for maintaining consistent themes and colors across a site.

      Example:
      ```css
      :root {
        --primary-color: #3498db;
      }
      .element {
        color: var(--primary-color);
      }
      ```

14. **What is the difference between `float` and `clear` in CSS?**
    - **Expected Answer:**
      - `float` is used to push elements to the left or right, allowing other elements to wrap around them. It was commonly used for layouts before Flexbox and Grid.
      - `clear` is used to control the flow of elements that follow floated elements, preventing them from wrapping around floated items.

15. **What are CSS Transitions and CSS Animations? How are they different?**
    - **Expected Answer:**
      - **CSS Transitions** allow you to change property values smoothly over a specified duration when a state change occurs (e.g., hover effects).
      - **CSS Animations** allow for more complex animations, including keyframes, and can run continuously or indefinitely.

      Example:
      ```css
      .element {
        transition: transform 0.5s ease;
      }
      .element:hover {
        transform: rotate(45deg);
      }
      ```

---

### **SCSS Interview Questions**

#### **Basic SCSS Concepts**

1. **What is SCSS, and how does it differ from CSS?**
   - **Expected Answer:** SCSS (Sassy CSS) is a superset of CSS that extends CSS with features like variables, nesting, mixins, and functions. SCSS files must be compiled into regular CSS before they can be used on a webpage.

2. **How do you declare and use variables in SCSS?**
   - **Expected Answer:** Variables in SCSS are declared using the `$` sign. They can store values like colors, fonts, or any CSS value, and can be reused throughout the stylesheet.

     Example:
     ```scss
     $primary-color: #3498db;
     .button {
       color: $primary-color;
     }
     ```

3. **What is nesting in SCSS, and why is it useful?**
   - **Expected Answer:** Nesting in SCSS allows you to write CSS selectors inside other selectors, reflecting the HTML structure. It makes the code more readable and organized.

     Example:
     ```scss
     .container {
       .header {
         background-color: #333;
       }
       .content {
         padding: 20px;
       }
     }
     ```

4. **What are mixins in SCSS, and how are they used?**
   - **Expected Answer:** Mixins are reusable pieces of code that can include properties and methods. They are defined using the `@mixin` directive and included using the `@include` directive.

     Example:


     ```scss
     @mixin border-radius($radius) {
       -webkit-border-radius: $radius;
       -moz-border-radius: $radius;
       border-radius: $radius;
     }

     .box {
       @include border-radius(10px);
     }
     ```

5. **What is the purpose of the `@import` directive in SCSS?**
   - **Expected Answer:** The `@import` directive allows you to include one SCSS file into another. It helps modularize your SCSS code by splitting it into smaller, more manageable files.

---

#### **Intermediate SCSS Concepts**

6. **What are `@extend` and `@mixin` in SCSS, and when would you use one over the other?**
   - **Expected Answer:**
     - `@extend` allows a class to inherit the styles of another class, reducing redundancy.
     - `@mixin` is more flexible, allowing you to reuse a block of styles and even pass parameters to customize them.
     - Use `@extend` for shared styles and `@mixin` when you need reusable functionality or styles with parameters.

7. **What is the difference between `@function` and `@mixin` in SCSS?**
   - **Expected Answer:**
     - `@function` is used to return a value based on input parameters. It allows you to create logic to calculate values.
     - `@mixin` is used for creating reusable chunks of styles, which can be included in other selectors.

8. **How do you create a responsive design using SCSS?**
   - **Expected Answer:** SCSS makes it easier to implement media queries by using variables for breakpoints and nesting media queries within selectors. This keeps the styles organized.

     Example:
     ```scss
     $small-screen: 600px;
     .container {
       @media (max-width: $small-screen) {
         flex-direction: column;
       }
     }
     ```

9. **What is the role of `@each` in SCSS?**
   - **Expected Answer:** The `@each` directive in SCSS is used to iterate over lists or maps. It allows you to perform operations on every item in a collection.

     Example:
     ```scss
     $colors: red, green, blue;
     @each $color in $colors {
       .#{$color} {
         color: $color;
       }
     }
     ```

10. **How do you use `@use` and `@forward` in SCSS?**
    - **Expected Answer:** 
      - `@use` is used to import a Sass file and gives you the ability to namespace and use its variables, mixins, and functions.
      - `@forward` is used to forward a module's members to another file.

      Example:
      ```scss
      // _colors.scss
      $primary-color: blue;
      @use "colors" as c;

      .button {
        background-color: c.$primary-color;
      }
      ```

---