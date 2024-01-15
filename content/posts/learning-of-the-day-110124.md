+++
title= "Learnings of the Days 11/01"
date= '2023-01-11'
draft= 'false'
tags= ["learning", "html/css"]
categories= ["interview"]
+++

Firstly I gather important questions & Topics of HTML/CSS. i.e.,

### HTML/CSS (Frequently asked questions)
- 1. Difference between ( Display:none visibility:hidden opacity:0 )
- 2. What are ways to hide elements in DOM.
- 3. Pseudo class/ pseudo selector.
- 4. What is a box model?
- 5. Semantic element vs non semantic element.
- 6. Focus on layouts, positioning, responsive design techniques, CSS
preprocessors (e.g., Sass, Less), and any frameworks like Bootstrap or
Material-UI.
- 7. Web accessibility
- 8. SEO
- 9. How rendering works ( Reflow v/s Repaint )
- 10. Centring of div
- 11. Async and defer.

1. **Difference between `display: none`, `visibility: hidden`, `opacity: 0`:**
   - `display: none` removes the element from the document flow, making it completely invisible and taking up no space.
   - `visibility: hidden` hides the element but still occupies space in the layout.
   - `opacity: 0` makes the element transparent but still occupies space in the layout.

2. **Ways to hide elements in the DOM:**
   - Using CSS properties like `display: none`, `visibility: hidden`, or `opacity: 0`.
   - Changing the element's position to be off-screen with properties like `position: absolute` or `transform: translateX(-9999px)`.
   - Applying the `hidden` attribute in HTML.

3. **Pseudo-class/pseudo-selector:**
   - Pseudo-classes select elements based on their state or position (e.g., `:hover`, `:nth-child`).
   - Pseudo-elements select and style a part of an element (e.g., `::before`, `::after`).

4. **Box model:**
   - The box model describes how elements are rendered in HTML, comprising content, padding, border, and margin.
   - Example: `<div style="width: 200px; padding: 20px; border: 2px solid #000; margin: 10px;"></div>`

5. **Semantic element vs. non-semantic element:**
   - Semantic elements convey meaning (e.g., `<article>`, `<nav>`), aiding in document structure and SEO.
   - Non-semantic elements (e.g., `<div>`, `<span>`) are generic containers without inherent meaning.

6. **Layouts, positioning, responsive design, CSS preprocessors, and frameworks:(More detailed in notes)**
   - Discuss strategies for responsive layouts, flexbox, grid, and media queries.
   - Explain positioning techniques like relative, absolute, and fixed.
   - Mention CSS preprocessors (Sass, Less) for variables, nesting, and mixins.
   - Bootstrap and Material-UI are frameworks facilitating responsive and consistent UI.

7. **Web accessibility:(More detailed in notes)**
   - Ensure websites are usable by people with disabilities.
   - Use semantic HTML, provide alternative text for images, and maintain keyboard accessibility.

8. **SEO:(More detailed in notes)**
   - Optimize content, use descriptive titles and meta tags, and ensure a crawlable site structure.

9. **Rendering (Reflow vs. Repaint):(More detailed in notes)**
   - Reflow recalculates layout, impacting the entire page, triggered by changes like resizing or modifying the DOM.
   - Repaint only updates visual aspects, caused by style changes without affecting layout.

10. **Centering of div:**
    - Horizontal: `margin: 0 auto;` or `text-align: center;`
    - Vertical: Flexbox (`align-items: center;`), Grid (`align-items: center;`), or positioning techniques.

11. **Async and defer:(More detailed in notes)**
    - `<script async>` loads the script asynchronously while not blocking HTML parsing.
    - `<script defer>` defers script execution until HTML parsing is complete.

These explanations provide a comprehensive overview of HTML/CSS concepts and practices for an interview setting. Feel free to delve deeper into specific topics as needed.



***Further Reference links:***
- [Flexbox](https://www.w3schools.com/css/css3_flexbox_container.asp)
- [Repaint vs Reflow](https://www.explainthis.io/en/swe/repaint-and-reflow)
- [Async & Defer](https://pagespeedchecklist.com/async-and-defer)
- [Web accessibility](https://blog.hubspot.com/website/web-accessibility)
- [SEO](https://moz.com/beginners-guide-to-seo)