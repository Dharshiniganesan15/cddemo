# Codebase Documentation

This document provides a comprehensive overview of the codebase, adhering strictly to the provided files and their contents without inferring or inventing features.

## Overview

This codebase consists of a single HTML file that implements a basic, self-contained web application. Its primary function is to allow users to add tasks to an unordered list displayed on the page. The application is designed as an "add-only" task manager, meaning there are no features for editing, deleting, or persisting tasks beyond the current browser session.

## File Structure

-   `taskonlyadd.html`

## File: taskonlyadd.html

This file contains the entire application, including the HTML structure, inline CSS for styling, and inline JavaScript for functionality. It defines a simple web page with a title, a heading, a text input field, an "Add" button, and an empty unordered list (`<ul>`) where tasks will be displayed.

## HTML Structure

The `taskonlyadd.html` file defines a standard HTML5 document structure:

*   **`<!DOCTYPE html>`**: Declares the document type.
*   **`<html lang="en">`**: The root element, specifying the document language as English.
*   **`<head>`**: Contains metadata and styling information:
    *   **`<meta charset="UTF-8">`**: Specifies the character encoding.
    *   **`<title>Task Manager - Add Only</title>`**: Sets the title that appears in the browser tab.
    *   **`<style>`**: Embeds CSS rules directly into the document.
*   **`<body>`**: Contains the visible content of the web page:
    *   **`<h2>Task Manager (Add Only)</h2>`**: A main heading for the application.
    *   **`<input type="text" id="taskInput" placeholder="Enter task">`**: A text input field where users can type tasks. It has an ID `taskInput` for JavaScript access and a placeholder text.
    *   **`<button onclick="addTask()">Add</button>`**: A button labeled "Add". When clicked, it calls the `addTask()` JavaScript function.
    *   **`<ul id="taskList"></ul>`**: An unordered list element where new tasks will be appended. It has an ID `taskList` for JavaScript access.
    *   **`<script>`**: Embeds JavaScript code directly into the document.

## CSS Styling

The embedded `<style>` block defines the following visual styles:

*   **`body`**:
    *   Uses `Arial` as the font family.
    *   Sets a `margin` of `40px` around the body content.
*   **`input`**:
    *   Adds `8px` of `padding`.
    *   Sets a fixed `width` of `200px`.
*   **`button`**:
    *   Adds `8px` of `padding`.
    *   Sets a `margin-left` of `5px` to space it from the input field.
*   **`ul`**:
    *   Sets a `margin-top` of `20px` to space it from the input/button area.
*   **`li`**:
    *   Sets a `margin` of `5px 0` for vertical spacing between list items.

## JavaScript Functionality

The embedded `<script>` block contains a single JavaScript function:

*   **`addTask()`**:
    *   **Retrieves Input**: Gets a reference to the `taskInput` element and its current `value`.
    *   **Trim Whitespace**: Uses `.trim()` to remove leading/trailing whitespace from the task value.
    *   **Empty Task Check**: Checks if the `task` string is empty after trimming. If it is, the function returns immediately, preventing empty tasks from being added.
    *   **Create List Item**: Creates a new `<li>` HTML element using `document.createElement('li')`.
    *   **Set Text Content**: Sets the `textContent` of the newly created `<li>` element to the `task` string.
    *   **Append to List**: Appends the new `<li>` element as a child to the `taskList` (the `<ul>` element).
    *   **Clear Input**: Resets the `value` of the `taskInput` field to an empty string, clearing it for the next task entry.

This function is triggered by the `onclick` event handler of the "Add" button.

## Features
-   Display a title "Task Manager (Add Only)".
-   Provide a text input field for entering tasks.
-   Provide an "Add" button to submit tasks.
-   Display a list where added tasks appear.
-   Add new tasks dynamically to the list on the page.
-   Clear the input field automatically after a task is added.
-   Prevent the addition of empty or whitespace-only tasks to the list.

## How to Use/Run

To use this application:

1.  Save the provided code into a file named `taskonlyadd.html` (or any `.html` extension).
2.  Open the `taskonlyadd.html` file using a web browser (e.g., Chrome, Firefox, Edge, Safari).
3.  In the "Enter task" input field, type your desired task.
4.  Click the "Add" button. The task will appear in the list below the input field, and the input field will clear, ready for the next task.