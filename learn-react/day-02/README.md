# Day 2

## React Development Setup & Workflow Notes

### I. Video Objectives and Importance of Workflow

The primary goals are to learn how to prepare the **development environment for a React application** and to establish a **workflow pipeline**. This workflow ensures that incremental application changes can be made **publicly available** quickly. This is vital for **public learning** and showcasing projects.

The discussed workflow should be set up at the beginning of the course, not just at the end of a project, to ensure code works correctly in **production** as it is being written.

### II. The Standard Deployment Workflow

This process ensures that code tested locally is also tested publicly in production mode.

1.  **Development:** The application developer (you) builds and tests the application **locally**.
2.  **Commit/Push:** The developer commits and pushes the code to a **repository**. This repository is typically a Git-based version control system like **GitHub** or **Bitbucket**.
3.  **Integration & Build:** Specific cloud vendors (SaaS, PaaS, or IaaS) are integrated with the repository (e.g., GitHub).
    *   Examples of such vendors include **Vercel**, **Netlify**, and **Heroku**.
    *   The moment code is pushed to GitHub, a **build kicks off** automatically.
4.  **Deployment:** Once the build is complete, the build artifacts are automatically deployed to a **CDN** (Content Delivery Network).
5.  **Access:** The application becomes **publicly and securely available**, providing a URL for access. This URL can be shared with customers/users or used by the developer for testing in a production environment.

### III. Setting up the Development Environment

#### A. Basic Method (Not Recommended)

React development can technically start by pointing to publicly hosted scripts on a CDN using the `<script>` tag.

*   **Required Files:** You need to point to `react.js` and `react-dom.js`. These are often available as development versions (e.g., `react.development.js`) and minified production files (e.g., `react.production.min.js`).

#### B. The Challenge: JSX and Transpilation

*   React uses a specific syntax format called **JSX**.
*   Browsers understand only **HTML and JavaScript**, not JSX.
*   All JSX written must be **transpiled** (translated) into browser-understandable code.
*   Manually handling transpilation requires learning tools like **Babel** and configuration libraries such as **Webpack** or **Parcel**.
*   *Conclusion:* To focus on learning React, this complex setup is avoided initially.

#### C. Recommended Method: Create React App (CRA)

The recommended approach is to use the famous tool **Create React App (CRA)**.

*   CRA handles all building and transpilation, allowing the developer to focus exclusively on writing React code.
*   Documentation is available at `create-react-app.dev`.

**Prerequisites:**
*   **Node.js** must be installed.
*   Basic knowledge of **npm** (Node Package Manager) is assumed.

**CRA Execution Methods:**

1.  **Global Install (Less Recommended):** Use `npm install -g create-react-app`. Then run `create-react-app [app name]`.
2.  **Execute Directly (Recommended):** Use **npx** (Node Package Executor).
    *   `npx` executes the command without permanently installing the CRA tool globally, preventing unnecessary files on the disk.
    *   **Command:** `npx create-react-app my-app` (where `my-app` is your desired application name).

### IV. Project Structure and Anatomy (CRA)

CRA resolves and installs all required packages (including React, React DOM, Babel, and Webpack) for the specific application.

*   **`node_modules`:** This folder contains all dependencies and libraries, which are installed and configured automatically by CRA.
*   **`package.json`:** This file holds all the library definitions.
*   **`public` folder:** This is where static assets are kept, such as the `favicon`, logo, and `index.html`.
*   **`src` folder:** This is where most of the active coding is done (e.g., `app.css`, JavaScript files).

**Key Files:**

*   **`index.html`:** This is the **entry point** of the application. Developers will rarely touch it, except potentially to change the application title or include external fonts.
    *   It contains a crucial `div` element with the attribute **`id="root"`**.
*   **`index.js`:** This file retrieves the entry point `div` using `document.getElementById('root')`. All application code written dynamically appears inside this root `div`.

**Cleanup Note:** After bootstrapping a project with CRA, developers can ideally delete most files generated (JS and HTML files) except for **`index.js`** and **`index.html`** to start coding completely in their own way. Required files like `package.json` should not be deleted.

### V. Running the Application Locally

The project will come bootstrapped with default React components (e.g., `app.js` is a React component).

*   **Commands to Run:** Use `yarn start` or `npm run start`.
*   **Process:** This command bootstraps a local server.
*   **Access:** The application runs on a local server, typically accessed via **`localhost:3000`** by default.
*   **Features:**
    *   The command automatically launches the browser.
    *   It performs **hot reloading**, meaning changes made and saved in the application code automatically refresh the browser without manual intervention.

### VI. Public Hosting and Deployment (Vercel Example)

Once local development is satisfactory, the code is integrated into the public workflow.

**Tool Used:** Vercel, a popular platform that hosts applications publicly on a CDN. Netlify is an alternative service.

**Vercel Integration Steps:**

1.  **Push Code:** Commit and push the written code to the Git repository (e.g., GitHub).
2.  **Vercel Login:** Register and log into Vercel.
3.  **New Project:** Click "New Project".
4.  **Import Repository:** Import the specific repository (e.g., the "youtube" project).
5.  **Configuration:**
    *   Vercel usually intelligently selects the **Framework Preset** (like React).
    *   **Crucially:** If the application code is nested within subfolders (not at the root of the repository), the specific **root directory** must be selected so the build runs correctly (e.g., selecting the `hello world` folder inside `03-react-environment`).
6.  **Deployment:** Click "Deploy".
    *   The first build may take longer as dependencies are downloaded, but subsequent builds are faster due to caching.
7.  **Result:** Vercel provides a dashboard with a **public domain/URL** (e.g., `youtube.vercel.app`) and a preview of the app.

**Continuous Deployment Benefit:** After this initial setup, every commit and push to the repository automatically triggers a new build, and the public URL is updated. This automation eliminates the pain of manually verifying production readiness and allows immediate notification if production failures occur.

***

The entire workflow, from local coding using CRA to continuous public deployment using services like Vercel, creates a seamless pipeline. This integrated process is like having a perfectly tuned assembly line: the moment you finish designing a part (your code) on your workbench (local server), it automatically gets packaged and delivered to the showroom (the public URL) for inspection and use.
