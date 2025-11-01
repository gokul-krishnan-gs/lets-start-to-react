

## Day 1 =  Why React and React Fundamentals

### I. Defining React

React is fundamentally defined as a **declarative, component-based JavaScript library for building user interfaces**. Understanding the key highlighted keywords—**declarative**, **component-based**, and **library for user interfaces**—is essential for building a strong foundation and appreciating the library.

***

### II. Declarative Programming

#### A. The Declarative Approach (React's Focus)

Declarative programming focuses on **what** you are expecting as an output, rather than telling the computer **how** to fulfill that expectation.

*   **Analogy:** If a wife (Mary) asks her husband (John) for a black coffee, she only gives the order (the *what*) but does not explain the steps needed to make the coffee.
*   **In React:** You instruct React on what you want (e.g., "I want a `ul` here, and an `h2` after it, and then iterate through this array to put the items in `li` elements").
*   **Abstraction:** The process of **DOM manipulation** (Document Object Model) is inevitable for rendering the output in the browser, but React abstracts this manipulation away from the developer. The developer can then focus solely on their business logic and presentation logic.

#### B. The Imperative Approach (The Opposite)

The opposite of declarative programming is **imperative programming**.

*   In the imperative approach, you describe **what** you want by specifying the detailed **instructions and steps of how to do it**.
*   **Analogy:** If Mary asks John for coffee, she also gives detailed, step-by-step instructions on preparation (e.g., take the pan, boil water, add coffee powder, don't add milk, add sugar, boil well, and serve hot).
*   **Imperative Code Example (DOM Manipulation):** When coding imperatively using raw JavaScript, the developer manually handles **DOM manipulation**. This involves giving line-by-line instructions to the program, such as:
    1.  Querying a specific HTML element using its ID (`document.getelementbyid`).
    2.  Creating new HTML elements (`document.create element`).
    3.  Setting the inner text and adding classes to the newly created elements.
    4.  Looping through data (an array) to create list items (`li`) for each piece of data.
    5.  Explicitly adding (appending) these newly created elements to the DOM.

#### C. The Document Object Model (DOM)

The DOM is the mechanism that structures and renders everything seen on an HTML page. It serves as a **gap bridging mechanism** from the HTML world to the JavaScript world, allowing JavaScript to query and change the DOM so that changes are reflected in the HTML directly.

***

### III. Component-Based Architecture

React is a **component-based library** that encourages the creation of isolated units.

#### A. Component Definition and Advantages

A component is defined as an **isolated unit** that contains all associated logic within itself. This logic includes:
*   Business logic.
*   Presentation logic.
*   API integrations.

The advantages of this approach are significant:

1.  **Isolation:** Components can be developed and tested completely in isolation from other components.
2.  **Teamwork:** Teams can work on individual components without worrying about dependencies or disturbing others' code bases.
3.  **Integration:** Once individual pieces are complete, they can be integrated with other components to build the entire application.
4.  **Reusability:** Components are highly reusable. If a specific component (like a `Search` bar) is needed elsewhere in the application, the developer does not have to re-implement it but can take the existing component and use it again.

#### B. Component Hierarchy

A user interface (UI) can be broken down into various different independent components. Breaking down a UI is done to any logical level.

*   **Example Hierarchy:** A simple e-results application could be broken down hierarchically: `App` $\rightarrow$ (`NavBar`, `Results`) $\rightarrow$ (`Search`, `Scores`) $\rightarrow$ (`ScoreHeading`, `ScoreList`).

***

### IV. React: Library vs. Framework

The question of why React is considered a library rather than a framework is a famous interview question.

#### A. Distinction

*   **Frameworks** typically perform multiple functions and often define a comprehensive structure.
*   **Libraries** typically focus on just **one thing** and aim to execute it very well.

#### B. React’s Scope

React is a **user interface library** because it was designed, invented, and coded solely to solve the problem of **user interface development**. It does not provide many features that a framework would typically have.

#### C. Reliance on External Tools

Because React is only focused on UI development, developers must bring in practically anything else they want to do in a React application from outside as additional libraries. Examples of tools not built into React include:
*   Routing.
*   Testing frameworks (e.g., Jest or React Test Library).
*   Data fetching (e.g., Axios or Fetch API).
*   State management (e.g., Redux or other tools).
*   Building infrastructure (e.g., Parcel or Webpack).
*   Localization, theming, or notification systems.

#### D. The Advantage of Flexibility

While this lack of built-in features might seem like a disadvantage, it is considered a **great advantage**. React gives developers the **liberty** and **flexibility** to choose the specific tools and infrastructure that best suit their project needs (e.g., choosing Cypress versus React Test Library for testing, or Fetch versus Axios for data fetching).

***
*In short, React is like a precision-engineered chef’s knife; it performs its core job (UI creation) perfectly, but you must bring your own cutting board (building infrastructure), pots (state management), and spices (routing) to complete the entire meal (application).*
