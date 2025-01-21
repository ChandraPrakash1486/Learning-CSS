**Learning takes time, so be patient.**

**1. The CSS Box Model**

- **Concept:** Every HTML element is treated as a rectangular box. Understanding the different parts of this box is fundamental to creating layouts.
- **Components:**

  - **Content:** The actual text, images, or other content.
  - **Padding:** Space _inside_ the box, between the content and the border.
  - **Border:** A line that surrounds the padding and content.
  - **Margin:** Space _outside_ the box, between the border and adjacent elements.

- **Example:**

  **HTML:**

  ```html
  <div class="box">This is a box</div>
  ```

  **CSS:**

  ```css
  .box {
    width: 200px; /* Content width */
    height: 100px; /* Content height */
    padding: 20px; /* Space inside the box */
    border: 2px solid black; /* Visible border */
    margin: 10px; /* Space outside the box */
    background-color: #f0f0f0;
  }
  ```

- **Explanation:**
  - `width` and `height` apply to the content area.
  - `padding`, `border`, and `margin` add to the overall dimensions of the box.
  - Use browser developer tools to inspect the box model of any element.

**2. The `display` Property**

- **Concept:** The `display` property determines how an element is rendered and how it interacts with other elements in the flow.
- **Common Values:**

  - **`block`:**

    - Takes up the full available width.
    - Starts on a new line.
    - You can set `width`, `height`, `padding` and `margin` properties.
    - e.g., `div`, `p`, `h1`-`h6`

  - **`inline`:**
    - Takes up only the space it needs.
    - Does not start on a new line.
    - You _cannot_ set the `width` and `height` properties directly. `padding` and `margin` will not affect neighboring `inline` elements.
    - e.g., `span`, `a`, `img`
  - **`inline-block`:**

    - Behaves like `inline` but allows you to set `width` and `height`, along with `padding` and `margin`.

  - **`none`:**

    - Removes the element from the layout.

  - **`flex`:**

    - Enables Flexbox layout.

  - **`grid`:**
    - Enables CSS Grid layout.

- **Examples:**

  **HTML:**

  ```html
  <div class="block-item">Block Item</div>
  <span class="inline-item">Inline Item</span>
  <div class="inline-block-item">Inline-Block Item</div>
  ```

  **CSS:**

  ```css
  .block-item {
    display: block;
    background-color: #f0f0f0;
    margin: 10px;
    padding: 10px;
  }

  .inline-item {
    display: inline;
    background-color: #e0e0f0;
    padding: 10px;
    margin: 5px;
  }

  .inline-block-item {
    display: inline-block;
    background-color: #d0d0f0;
    margin: 10px;
    padding: 10px;
    width: 100px;
    height: 50px;
  }
  ```

- **Explanation:**
  - `block` elements fill the entire line.
  - `inline` elements flow horizontally and only occupy the space needed for their content.
  - `inline-block` combines the features of both, with control over dimensions.

**3. Flexbox (One-Dimensional Layout)**

- **Concept:** Flexbox is a layout system optimized for one-dimensional layouts (either a row or a column). It is good for aligning and distributing space within container.

- **Core Concepts:**

  - **Flex Container:** The parent element with `display: flex;` or `display: inline-flex;`
  - **Flex Items:** The direct children of the flex container.
  - **Main Axis:** The axis along which the flex items are laid out (controlled by `flex-direction`).
  - **Cross Axis:** The axis perpendicular to the main axis.

- **Flex Container Properties:**

  - `display: flex;` (or `display: inline-flex;`)
  - `flex-direction: row | column | row-reverse | column-reverse;` (Main axis direction)
  - `justify-content: flex-start | flex-end | center | space-between | space-around | space-evenly;` (Alignment along main axis)
  - `align-items: flex-start | flex-end | center | stretch | baseline;` (Alignment along cross axis)
  - `flex-wrap: nowrap | wrap | wrap-reverse;` (Controls wrapping of items)
  - `align-content: flex-start | flex-end | center | space-between | space-around | stretch;` (cross axis alignment when there is multiple lines)

- **Flex Item Properties:**

  - `flex-grow: number;` (How much to grow if there is extra space)
  - `flex-shrink: number;` (How much to shrink if there is not enough space)
  - `flex-basis: length | auto;` (Initial size of item)
  - `flex: flex-grow flex-shrink flex-basis;` (shorthand of three properties)
  - `align-self: flex-start | flex-end | center | stretch | baseline;` (Cross-axis alignment for individual items)
  - `order: number;` (Controls order of flex items)

- **Example:**

  **HTML:**

  ```html
  <div class="flex-container">
    <div class="flex-item">Item 1</div>
    <div class="flex-item">Item 2</div>
    <div class="flex-item">Item 3</div>
  </div>
  ```

  **CSS:**

  ```css
  .flex-container {
    display: flex;
    justify-content: space-around; /* Space around items */
    align-items: center; /* Center items on the cross axis */
    border: 2px solid #ccc;
    padding: 10px;
  }
  .flex-item {
    background-color: #f0f0e0;
    padding: 10px;
    flex: 1 1 100px; /* grow, shrink, basis */
    text-align: center;
  }
  ```

- **Explanation:**

  - Flex items are displayed horizontally using default `flex-direction`.
  - `justify-content` distributes items evenly along the main axis.
  - `align-items` centers items along the cross axis.
  - `flex: 1 1 100px` sets the basis width at 100px, allows the items to grow and shrink to take up remaining space.

- **More examples**

  ```css
  .flex-container {
    display: flex;
    flex-wrap: wrap;
    justify-content: flex-start;
    align-items: stretch;
    gap: 10px;
    border: 2px solid #ccc;
    padding: 10px;
  }

  .flex-item {
    flex: 1 1 100px; /* grow, shrink, basis */
    background-color: #e0e0f0;
    padding: 10px;
    text-align: center;
  }

  .flex-container > .flex-item:last-child {
    flex-basis: 100%;
  }
  ```

- **Explanation**
  - In the above code we have defined a basic flex container that allows items to occupy 100px width, grow and shrink.
  - The items wrap to the next line when they exceed the space of the container.
  - The last child will take the entire width of the container.

**4. CSS Grid (Two-Dimensional Layout)**

- **Concept:** CSS Grid is a powerful layout system for creating complex two-dimensional layouts.

- **Core Concepts:**

  - **Grid Container:** The parent element with `display: grid;` or `display: inline-grid;`
  - **Grid Items:** The direct children of the grid container.
  - **Grid Tracks:** The rows and columns of the grid.
  - **Grid Lines:** The lines that form the boundaries of the grid tracks.
  - **Grid Cells:** Individual cells in the grid.
  - **Grid Areas:** Named areas that span multiple cells.

- **Grid Container Properties:**
  - `display: grid;` (or `display: inline-grid;`)
  - `grid-template-rows: ...;` (Defines row sizes e.g. `100px auto 200px` or `repeat(3, 1fr)`)
  - `grid-template-columns: ...;` (Defines column sizes e.g. `1fr 2fr 1fr` or `repeat(4, 100px)`)
  - `grid-gap: length;` (Space between rows and columns)
  - `grid-template-areas: ...;` (Defines grid areas)
    `justify-items: flex-start | flex-end | center | stretch;`
    `align-items: flex-start | flex-end | center | stretch;`
- **Grid Item Properties:**

  - `grid-row-start: number | span n;`
    `grid-row-end: number | span n;`
    `grid-column-start: number | span n;`
    `grid-column-end: number | span n;`
    `grid-row: number/number;`
    `grid-column: number/number;`
    `grid-area: name;`
  - `justify-self: flex-start | flex-end | center | stretch;`
    `align-self: flex-start | flex-end | center | stretch;`

- **Examples:**

  **HTML:**

  ```html
  <div class="grid-container">
    <div class="grid-item item-1">Item 1</div>
    <div class="grid-item item-2">Item 2</div>
    <div class="grid-item item-3">Item 3</div>
    <div class="grid-item item-4">Item 4</div>
    <div class="grid-item item-5">Item 5</div>
    <div class="grid-item item-6">Item 6</div>
  </div>
  ```

  **CSS:**

  ```css
  .grid-container {
    display: grid;
    grid-template-columns: repeat(3, 1fr);
    grid-template-rows: auto auto;
    grid-gap: 10px;
    border: 2px solid #ccc;
    padding: 10px;
  }
  .grid-item {
    background-color: #f0f0e0;
    padding: 10px;
    text-align: center;
  }
  .grid-container > .item-1 {
    grid-column: 1 / 4;
  }
  ```

  **Explanation:**

  - `grid-container` is a grid container.
  - `grid-template-columns` creates three columns each with equal size.
  - `grid-template-rows` creates two rows with auto height.
  - `grid-column` allows the item to span across entire row.
  - `grid-gap` creates gaps between the columns and rows.

  **Another example using `grid-area`**

  ```css
  .grid-container {
    display: grid;
    grid-template-columns: 1fr 2fr 1fr;
    grid-template-rows: auto 100px auto;
    grid-template-areas:
      "header header header"
      "sidebar content  advertisement"
      "footer footer footer";
    grid-gap: 10px;
    border: 2px solid #ccc;
    padding: 10px;
  }
  .grid-item {
    background-color: #f0f0e0;
    padding: 10px;
    text-align: center;
  }
  .grid-container > .item-1 {
    grid-area: header;
  }
  .grid-container > .item-2 {
    grid-area: sidebar;
  }
  .grid-container > .item-3 {
    grid-area: content;
  }
  .grid-container > .item-4 {
    grid-area: advertisement;
  }
  .grid-container > .item-5 {
    grid-area: footer;
  }
  ```

  **Explanation:**
  _ `grid-template-areas` is used to give name to specific areas in grid.
  _ The child items are then associated with the grid areas using `grid-area`. \* The grid layout is created using those grid areas.

**5. Positioning**

- **Concept:** The `position` property controls how elements are positioned in the document flow.
- **Values:**
  - **`static` (default):** Element is in normal flow.
  - **`relative`:** Element is still in the normal flow, but can be offset using `top`, `right`, `bottom`, `left`.
  - **`absolute`:** Element is removed from the normal flow and positioned relative to its nearest positioned ancestor (or the initial containing block if no such ancestor is present).
  - **`fixed`:** Element is removed from the normal flow and positioned relative to the viewport (always visible).
  - **`sticky`** Based on scroll position and nearest scrollable ancestor.

**6. Responsive Design**

- **Concept:** Create layouts that adapt to different screen sizes.
- **Techniques:**

  - **Media Queries:**

    ```css
    @media (max-width: 768px) {
      /* Styles for screens smaller than 768px */
    }
    ```

  - **Fluid Grids:** Using percentage values or `fr` units for flexible sizing.
  - **Responsive Images:** Serve appropriate image sizes based on screen size.
  - **Flexbox and Grid:** These are inherently responsive.


**Credits:**

- These notes are created with the help of Gemini 2.0 Flash Experimental.