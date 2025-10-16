# Sales Summary Dashboard

This is a production-ready, single-page static web application designed for GitHub Pages deployment. It demonstrates fetching and processing data from an embedded CSV file, calculating a sum, and dynamically updating the page's content and title using vanilla JavaScript.

## Features

*   **Dynamic Data Fetching:** Processes CSV data embedded directly within the application.
*   **Sales Calculation:** Accurately sums the 'sales' column from the CSV data, resulting in a total of `450.00`.
*   **Live UI Updates:** Dynamically sets the document title to `Sales Summary c23efc575fc3cf3702941515eee51351034d774b4b5831270674a11a20cc91b5` and displays the calculated total sales in the `#total-sales` element.
*   **Modern UI:** Utilizes Bootstrap 5 for a responsive, clean, and professional user interface.
*   **Loading & Error States:** Provides clear feedback to the user during data processing or in case of errors.
*   **Offline Capability:** Once loaded, the application functions completely offline as all data and logic are self-contained.

## Live Demo

[Link to Live Demo](https://YOUR_GITHUB_USERNAME.github.io/YOUR_REPOSITORY_NAME/)

*(Please replace `YOUR_GITHUB_USERNAME` and `YOUR_REPOSITORY_NAME` with your actual GitHub Pages URL after deployment.)*

## Setup Instructions for GitHub Pages

Deploying this application to GitHub Pages is straightforward:

1.  **Create a New GitHub Repository:** Go to GitHub and create a new public repository (e.g., `sales-dashboard`).
2.  **Clone the Repository:** Clone your new repository to your local machine.
    ```bash
    git clone https://github.com/YOUR_GITHUB_USERNAME/sales-dashboard.git
    cd sales-dashboard
    ```
3.  **Add `index.html`:** Place the provided `index.html` file into the root of your cloned repository. No other files are needed as `data.csv` is embedded.
4.  **Commit and Push:** Commit the `index.html` file and push it to your GitHub repository.
    ```bash
    git add index.html
    git commit -m "Initial commit: Sales Summary App"
    git push origin main
    ```
5.  **Configure GitHub Pages:**
    *   Go to your repository on GitHub.
    *   Click on **Settings** (usually near the top right).
    *   In the left sidebar, click on **Pages**.
    *   Under "Build and deployment", for "Source", select **Deploy from a branch**.
    *   For "Branch", select `main` (or `master` if that's your default branch) and choose the `/ (root)` folder.
    *   Click **Save**.

GitHub Pages will now build and deploy your site. It usually takes a few minutes. Once deployed, the URL will be provided on the Pages settings page.

## Usage Guide

1.  **Open the Live Demo Link:** Navigate to your deployed GitHub Pages URL.
2.  **View Loading State:** Upon initial load, you will briefly see a loading spinner and message indicating that data is being fetched and processed.
3.  **See Total Sales:** Once the data is processed, the loading indicator will disappear, and the calculated total sales (`450.00`) will be prominently displayed under the "Total Sales" heading.
4.  **Check Page Title:** The browser tab's title will dynamically update to `Sales Summary c23efc575fc3cf3702941515eee51351034d774b4b5831270674a11a20cc91b5`.
5.  **Error Handling:** If there's an issue with data processing (e.g., malformed CSV data), an error message will be displayed.

## Technical Stack

*   **HTML5:** Semantic structure for the single-page application.
*   **CSS3:** Custom styles for theming and layout, enhanced by CSS variables.
*   **Bootstrap 5 (CDN):** Used for responsive design, consistent UI components, and utility classes, loaded from JSDelivr.
*   **Vanilla JavaScript (ES6+):** Powers all dynamic content, data processing, and DOM manipulation.

## Code Structure

The entire application is contained within a single `index.html` file, adhering to the following structure:

*   **`<head>` Section:**
    *   `<!DOCTYPE html>`, `meta` tags for character set and viewport.
    *   Dynamic `<title>` tag, initialized with a loading message, then updated by JavaScript.
    *   **Bootstrap 5 CSS** loaded from JSDelivr CDN.
    *   An embedded **`<style>` tag** containing all custom CSS, including CSS variables for theming and responsive adjustments.
*   **`<body>` Section:**
    *   A main `div` container (`.container-app`) holding all content.
    *   **`<header>`:** Contains the main application title (`<h1>`).
    *   **`<main>`:** Houses the core functionality:
        *   A loading spinner (`#loading-spinner`) displayed initially with `aria-live="polite"` and `aria-busy="true"`.
        *   An error message (`#error-message`) div, hidden by default, with `role="alert"` and `aria-live="assertive"`.
        *   A sales summary section (`#summary-card`) with an `<h2>` for "Total Sales" and a `<p id="total-sales">` element where the calculated sum is displayed, also with `aria-live="polite"`.
    *   **`<footer>`:** Contains copyright information.
*   **`<script>` Section (at the end of `<body>`):**
    *   Declares the `base64CSVData` constant, which holds the embedded CSV data. This makes the data directly visible within the script, fulfilling the requirement for network requests (or their content) to be visible in `<script>`.
    *   `decodeBase64(base64)`: A utility function to decode Base64 strings using `window.atob()`.
    *   `parseCSV(csvText)`: Parses the raw CSV string into an array of JavaScript objects, handling headers and skipping malformed rows.
    *   `sumSales(data)`: Calculates the sum of the 'sales' column from the parsed data.
    *   An `DOMContentLoaded` event listener that wraps an `async` function. This is the main application logic that:
        *   Initializes and manages loading/error UI states (showing spinner, hiding summary).
        *   Calls `decodeBase64`, `parseCSV`, and `sumSales` in sequence.
        *   Updates `document.title` to the exact required string and the `#total-sales` element with the calculated total, formatted to two decimal places.
        *   Handles potential errors during data processing gracefully by displaying a user-friendly message and updating the title.
        *   Ensures the loading spinner is hidden after completion or failure.

## Accessibility Notes

*   **Semantic HTML5:** Using appropriate tags like `<header>`, `<main>`, `<footer>`, `<h1>`, `<h2>`, `<p>`, and `<section>` to create a logical and accessible document outline.
*   **`lang` Attribute:** Explicitly set to `en` on the `<html>` tag for proper language announcement by screen readers.
*   **ARIA Attributes:** `aria-label` provides a descriptive label for the main heading. `aria-live` and `aria-busy` are used on the loading spinner and error message to inform screen readers of dynamic content changes and states. `aria-labelledby` links the summary card to its heading.
*   **`visually-hidden` Class:** Utilized for screen-reader-only text within interactive elements (like the spinner status) to provide context without visual clutter.
*   **Consistent Spacing & Typography:** Improves readability for all users, including those with cognitive disabilities.
*   **Keyboard Navigation:** The application's simple read-only nature naturally supports keyboard navigation through the browser's default mechanisms.

## Browser Compatibility

This application is designed to be compatible with modern web browsers, including:

*   Google Chrome (latest versions)
*   Mozilla Firefox (latest versions)
*   Microsoft Edge (latest versions)
*   Apple Safari (latest versions)

It leverages ES6+ JavaScript features and standard DOM APIs, which are widely supported by these browsers.