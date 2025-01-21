**CSS Pseudo-Classes: Detailed Notes**

- **Concept:** Pseudo-classes are CSS selectors that target elements based on specific _states_, _positions_, _relationships_, or _user interactions_. They allow dynamic styling without modifying the HTML structure, enhancing interactivity and responsiveness.

- **Key Ideas:**

  - **Dynamic Styling:** Pseudo-classes enable styles to change based on user actions or element states.
  - **Contextual Styling:** They can target elements based on their position or relationships within the document tree.
  - **No HTML Modifications:** Pseudo-classes allow you to style elements based on criteria without adding extra classes or IDs to HTML, which keeps the HTML clean.
  - **Accessibility:** Use pseudo-classes wisely to improve accessibility.

- **Syntax:**
  - Single colon `:` (e.g., `:hover`, `:first-child`).

**Common Pseudo-Classes**

We'll categorize them for clarity:

**1. User Action Pseudo-Classes**

- **`:hover`**

  - **Purpose:** Styles elements when the mouse cursor hovers over them.
  - **Usage:** Commonly used for links, buttons, or interactive elements.
  - **Example:**

    ```css
    a:hover {
      color: red;
      text-decoration: underline;
    }
    ```

- **`:focus`**

  - **Purpose:** Styles elements when they are focused (e.g., selected via keyboard tab or mouse click).
  - **Usage:** Essential for accessibility, particularly for keyboard navigation.
  - **Example:**

    ```css
    input:focus,
    textarea:focus {
      outline: 2px solid blue;
    }
    ```

- **`:active`**

  - **Purpose:** Styles elements when they are being activated (e.g., the moment a mouse button is pressed).
  - **Usage:** Commonly used for buttons and links.
  - **Example:**

    ```css
    button:active {
      background-color: green;
    }
    ```

**2. Structural Pseudo-Classes**

- **`:first-child`**

  - **Purpose:** Targets the _first child_ element of its parent.
  - **Usage:** Selecting first element in a list.
  - **Example:**

    ```css
    ul li:first-child {
      font-weight: bold;
    }
    ```

- **`:last-child`**

  - **Purpose:** Targets the _last child_ element of its parent.
  - **Usage:** Selecting the last item in a list, where you don't want to add border at bottom.
  - **Example:**

    ```css
    ul li:last-child {
      border-bottom: none;
    }
    ```

- **`:nth-child(an + b)`**

  - **Purpose:** Selects elements based on their position among _all_ siblings (counts all elements).
  - **Usage:** Selecting every second, third, or nth element.
  - **Example:**

    ```css
    .container *:nth-child(2n) {
      background-color: #f0f0f0;
    }
    ```

- **`:nth-of-type(an + b)`**

  - **Purpose:** Selects elements based on their position among _siblings of the same type_.
  - **Usage:** Selecting the first, third or fifth paragraph in a set of paragraph tags.
  - **Example:**

    ```css
    p:nth-of-type(odd) {
      color: blue;
    }
    ```

- **`:first-of-type`**

  - **Purpose:** Selects the first element of a specific type among siblings.
  - **Usage:** To style the first paragraph in a group.
  - **Example:**

    ```css
    .container p:first-of-type {
      font-size: 1.2em;
    }
    ```

- **`:last-of-type`**

  - **Purpose:** Selects the last element of a specific type among siblings.
  - **Usage:** To remove the bottom border of the last list item.
  - **Example:**

    ```css
    li:last-of-type {
      border-bottom: none;
    }
    ```

- **`:only-child`**

  - **Purpose**: Selects an element when it is the only child of its parent.
  - **Usage**: When an element is the only one in a container.
  - **Example:**

    ```css
    ul li:only-child {
      font-weight: bold;
    }
    ```

- **`:only-of-type`**

  - **Purpose**: Selects an element when it is the only one of its type among siblings.
  - **Usage**: When you want to style one specific item, when the only one of its type.
  - **Example:**

  ```css
  p:only-of-type {
    font-size: 1.5em;
  }
  ```

**3. Form Pseudo-Classes**

- **`:checked`**

  - **Purpose:** Selects checked checkboxes or radio buttons.
  - **Usage:** To style the selected options in forms.
  - **Example:**

    ```css
    input[type="radio"]:checked + label {
      color: blue;
    }
    ```

- **`:disabled`**

  - **Purpose:** Selects disabled form elements.
  - **Usage:** To change the appearance of disabled form elements.
  - **Example:**

    ```css
    input:disabled {
      background-color: #eee;
    }
    ```

- **`:enabled`**

  - **Purpose:** Selects enabled form elements.
  - **Usage:** To target specifically enabled elements.
  - **Example:**

    ```css
    input:enabled {
      border-color: green;
    }
    ```

- **`:required`**

  - **Purpose:** Selects required form elements.
  - **Usage:** To style required form fields.
  - **Example:**

    ```css
    input:required {
      border-color: red;
    }
    ```

- **`:optional`**

  - **Purpose:** Selects optional form elements.
  - **Usage:** To style optional fields.
  - **Example:**

    ```css
    input:optional {
      border-color: blue;
    }
    ```

- **`:valid`**

  - **Purpose:** Styles an input element with valid value.
  - **Usage** To provide feedback to users about valid input.
  - **Example:**

    ```css
    input:valid {
      border-color: green;
      background-color: lightgreen;
    }
    ```

- **`:invalid`**

  - **Purpose:** Styles an input element with an invalid value.
  - **Usage** To provide feedback to users about invalid input.
  - **Example:**


      ```css
        input:invalid {
           border-color: red;
           background-color: lightcoral;
        }
      ```

**4. Negation Pseudo-Class**

- **`:not(selector)`**

  - **Purpose:** Selects elements that do _not_ match the provided selector.
  - **Usage:** To select all elements except for certain ones.
  - **Example:**

    ```css
    ul li:not(:first-child) {
      border-top: 1px solid #ccc;
    }
    ```

**5. Language Pseudo-Class**

- **`:lang(language-code)`**
  - **Purpose**: Select elements based on language.
  - **Usage**: To change the styling of specific language content.
  - **Example:**
    ```css
    :lang(fr) {
      quotes: "«" "»";
    }
    ```

**Best Practices**

- **Accessibility:** Always consider accessibility when using pseudo-classes, especially `:focus`.
- **Specificity:** Pseudo-classes increase the specificity of a selector.
- **Combinations:** You can combine pseudo-classes and other selectors for better targeting.
- **Browser Support:** Check for browser compatibility, especially for newer pseudo-classes.
- **Test:** Always test your pseudo classes on all browsers, and on different screen sizes.

**Key Takeaways**

- Pseudo-classes enhance CSS with dynamic styling based on conditions or states.
- Use `:hover`, `:focus`, `:active` to improve user experience.
- Use structural pseudo-classes to target elements based on their position.
- Use form pseudo-classes to style form states.
- Use negation class to select the items that do not match your specific criteria.
- Use the `:lang()` pseudo-class to apply styles to specific language content.
- Use pseudo-classes thoughtfully to build robust and flexible CSS layouts and styles.
- Use MDN to look for the properties, behaviors and examples.
- Practice using them regularly.

**Credits:**

- These notes are created with the help of Gemini 2.0 Flash Experimental.