# Codebase Documentation

This document provides a comprehensive overview of the codebase, adhering strictly to the provided files and their contents without inferring or inventing features.

## Overview

This codebase consists of a single HTML file that implements a client-side Task Manager application. It utilizes standard web technologies: HTML for structuring the content, CSS for styling, and JavaScript for interactive functionality and data persistence. The application allows users to add, edit, mark as complete, delete, and clear tasks, with all tasks being saved and loaded from the browser's local storage.

## File Structure

```
.
└── taskonlyadd.html
```

## File: taskonlyadd.html

This file is a complete HTML document that includes embedded CSS within a `<style>` tag and embedded JavaScript within a `<script>` tag. It defines the structure of the Task Manager interface, applies styles to its elements, and implements all the interactive logic and data persistence using browser's local storage.

## HTML Structure

The `taskonlyadd.html` file defines a standard HTML5 document. The `<body>` contains a single `div` with the class `container`.

Inside the `.container`:
*   An `<h2>` heading displays "Task Manager".
*   An `<input>` field with `type="text"` and `id="taskInput"` is provided for entering new tasks.
*   Two `<button>` elements are present:
    *   An "Add" button, which calls the `addTask()` JavaScript function when clicked.
    *   A "Clear All" button, which calls the `clearTasks()` JavaScript function when clicked.
*   An empty `<ul>` with `id="taskList"` serves as the container for dynamically added task list items.

## CSS Styling

The embedded CSS in `taskonlyadd.html` provides styling for the Task Manager application:

*   **`body`**: Sets a global font (`Arial, sans-serif`), a light gray background color (`#f2f2f2`), and uses flexbox (`display:flex`, `justify-content:center`, `align-items:center`, `height:100vh`) to center the content vertically and horizontally on the page.
*   **`.container`**: Styles the main application box with a white background, padding, fixed width, rounded borders, and a subtle box shadow. It also centers its text content.
*   **`h2`**: Adds bottom margin to the main heading.
*   **`input`**: Styles the text input field with padding and a fixed width.
*   **`button`**: Provides consistent padding, margins, and a pointer cursor for all buttons.
*   **`ul`**: Removes default list styling (`list-style:none`), padding, and adds top margin.
*   **`li`**: Styles individual task items with flexbox (`display:flex`, `justify-content:space-between`, `align-items:center`), a light gray background, padding, vertical margins, and rounded borders.
*   **`.task-text`**: Styles the text portion of a task, allowing it to take available space (`flex:1`) and indicating it's clickable with a pointer cursor.
*   **`.completed`**: A class that applies a strikethrough text decoration and changes the text color to gray, typically used to indicate a completed task.

## JavaScript Functionality

The embedded JavaScript in `taskonlyadd.html` provides the interactive logic for the Task Manager:

*   **`window.onload`**: This event handler ensures that the `loadTasks()` function is called immediately when the page finishes loading, populating the task list from local storage.
*   **`addTask()`**:
    *   Retrieves the value from the `taskInput` field.
    *   Trims whitespace from the input.
    *   If the input is empty, an `alert` message is displayed, and the function returns.
    *   Calls `createTask()` to add the new task to the DOM (initially not completed).
    *   Clears the `taskInput` field.
    *   Calls `saveTasks()` to persist the updated list to local storage.
*   **`createTask(text, completed)`**:
    *   Dynamically creates an `<li>` element.
    *   Creates a `<span>` element for the task text, assigns it the class `task-text`, and sets its `textContent`.
    *   If the `completed` parameter is `true`, it adds the `completed` class to the `span`.
    *   Assigns an `onclick` handler to the `span` that toggles the `completed` class and then calls `saveTasks()`.
    *   Creates an "Edit" button:
        *   Sets its `textContent` to "Edit".
        *   Assigns an `onclick` handler that prompts the user for new task text. If valid text is entered, it updates the `span`'s `textContent` and calls `saveTasks()`.
    *   Creates a "Delete" button:
        *   Sets its `textContent` to "Delete".
        *   Assigns an `onclick` handler that removes the `<li>` element from the DOM and calls `saveTasks()`.
    *   Appends the `span`, "Edit" button, and "Delete" button to the `<li>`.
    *   Appends the newly created `<li>` to the `ul#taskList`.
*   **`clearTasks()`**:
    *   Clears the `innerHTML` of the `ul#taskList` element, effectively removing all tasks from the display.
    *   Removes the "tasks" item from `localStorage`, deleting all persisted tasks.
*   **`saveTasks()`**:
    *   Initializes an empty array `tasks`.
    *   Iterates through all `<li>` elements within `ul#taskList`.
    *   For each `<li>`, it extracts the `textContent` and `completed` status (by checking for the `completed` class) from the `.task-text` span.
    *   Pushes an object `{text: text, completed: completed}` into the `tasks` array.
    *   Saves the `tasks` array, serialized as a JSON string, into `localStorage` under the key "tasks".
*   **`loadTasks()`**:
    *   Retrieves the "tasks" item from `localStorage`.
    *   Parses the JSON string back into an array of task objects, or initializes an empty array if no tasks are found.
    *   Iterates through each task object in the array and calls `createTask()` for each, effectively rebuilding the task list in the DOM.

## Features

-   Displaying a task manager interface with an input field and buttons.
-   Adding new tasks to a list from an input field.
-   Persisting tasks across browser sessions using `localStorage`.
-   Loading previously saved tasks automatically on page load.
-   Marking tasks as complete/incomplete by clicking on the task text, which applies a strikethrough style.
-   Editing individual tasks via a prompt box.
-   Deleting individual tasks from the list.
-   Clearing all tasks from the list and from local storage.
-   Basic input validation to prevent adding empty tasks.

## How to Use/Run

To use this Task Manager application:

1.  Save the provided code into a file named `taskonlyadd.html` (or any other name with a `.html` extension).
2.  Open the `taskonlyadd.html` file in any modern web browser (e.g., Chrome, Firefox, Safari, Edge).
3.  The application will load, displaying any tasks previously saved in your browser's local storage.
4.  Enter a task in the input field and click "Add" to add it to the list.
5.  Click on a task's text to toggle its completion status.
6.  Click the "Edit" button next to a task to modify its text.
7.  Click the "Delete" button next to a task to remove it.
8.  Click "Clear All" to remove all tasks from the list and storage.