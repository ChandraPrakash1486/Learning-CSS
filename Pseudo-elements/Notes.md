**CSS Pseudo-Elements: Detailed Notes**

- **Concept:** Pseudo-elements are CSS selectors that allow you to style specific parts of an element or insert content without modifying the HTML structure. They extend the capabilities of CSS by enabling targeted styling within elements.

- **Key Ideas:**

  - **Target Parts, Not Whole Elements:** Pseudo-elements let you style a particular part of an element, such as the first line, first letter, before or after content, or selected content.
  - **Enhance Layout and Design:** Pseudo-elements provide more flexibility in styling and layout options.
  - **Separate Structure from Style:** They help keep HTML clean by separating content from styling.
  - **Content Insertion:** Can be used to insert content before or after the content of elements using `content` property.
  - **Styling:** Can be used for styling specific parts of the element, such as first-letter, first-line or selected part.

- **Syntax:**
  - Double colon `::` (e.g., `::before`, `::after`).
  - Single colon `:` was used in older browsers, but use double colon for consistency.

**Common Pseudo-Elements**

1.  **`::before`**

    - **Purpose:** Inserts content _before_ the content of an element (within its padding).
    - **Requirement:** The `content` property is required. It needs to have a value, even if it is an empty string (`content:""`)
    - **Default `display`:** Default is `inline`, which may need to be adjusted based on requirements.
    - **Positioning:** The `::before` element is positioned before all the content of the element and after padding, within the content box.
    - **Uses:**
      - Add icons.
      - Add decoration.
      - Add text or other content.
    - Can use for styling with empty content.

    - **Example:**

      ```css
      .element::before {
        content: ">> "; /* Insert text content */
        color: blue;
        margin-right: 5px;
      }
      ```

2.  **`::after`**

    - **Purpose:** Inserts content _after_ the content of an element.
    - **Requirement:** Requires the `content` property.
    - **Default `display`:** Default is `inline`.
    - **Positioning:** The `::after` element is positioned after all the content of the element, within the content box.
    - **Uses:**

      - Add a visual indicator or decoration.
      - Add custom styling to the end of an element.

    - **Example:**

      ```css
      .element::after {
        content: ""; /*  No Content, just styling */
        display: block;
        width: 10px;
        height: 10px;
        background-color: red;
      }
      ```

3.  **`::first-line`**

    - **Purpose:** Styles the first line of a block-level element.
    - **Usage:** Only applies to block-level elements (e.g., `p`, `div`).
    - **Limited Properties:** Not all CSS properties can be used on `::first-line`.
    - **Uses:** Customizing the font of the first line of paragraph.

    - **Example:**

      ```css
      p::first-line {
        font-weight: bold;
      }
      ```

4.  **`::first-letter`**

    - **Purpose:** Styles the first letter of the content of a block-level element.
    - **Usage:** Only applies to block-level elements.
    - **Limited Properties:** Not all CSS properties can be used on `::first-letter`.
    - **Uses:** Add custom styling to the first letter such as font-size.

    - **Example:**

      ```css
      p::first-letter {
        font-size: 2em;
        color: purple;
      }
      ```

5.  **`::placeholder`**

    - **Purpose:** Styles the placeholder text of form inputs.
    - **Usage:** Applies to `<input>`, `<textarea>`, etc.
    - **Uses:** Customize the placeholder text color, font, and other styling.

    - **Example:**

      ```css
      input::placeholder {
        color: grey;
        font-style: italic;
      }
      ```

6.  **`::selection`**

    - **Purpose:** Styles the text that is selected by the user.
    - **Usage**: Applies to the selected text of an element.
    - **Uses**: Use this for custom style of text highlight.

    - **Example:**
      ```css
      ::selection {
        background-color: yellow;
        color: black;
      }
      ```

**Best Practices**

- **Use for Styling and Content Insertion:** Use for styling parts of element, and adding content before or after the element.
- **Use Content for `::before` and `::after`:** Must have content, even if it is an empty string for styling purposes, when using `::before` and `::after`.
- **Limit Use for Semantics:** Do not add important content or critical information with `::before` or `::after`, as they will not be accessible with screen readers. Use for styling and adding icons.
- **Positioning:** If you are using `::before` and `::after` for decorations, you often need to set `position: relative;` on the parent and `position: absolute` or `position: fixed` on the pseudo element for precise positioning.
- **Avoid Overuse:** Use them only when it makes the code cleaner. Do not use them just because you can. Always remember less CSS is better.
- **Browser compatibility:** Check MDN for browser compatibility.

**Key Takeaways**

- Pseudo-elements select _specific parts_ of elements.
- `::before` and `::after` insert content or decorations, which always need a `content` property.
- `::first-line` and `::first-letter` style the first parts of the text content.
- `::placeholder` styles placeholder text of the input forms.
- `::selection` styles the selected text by user.
- Pseudo-elements can make layouts more concise and less cluttered.
- Use them responsibly, and use them when you need them.
- Always check for browser compatibility

**Credits:**

- These notes are created with the help of Gemini 2.0 Flash Experimental.