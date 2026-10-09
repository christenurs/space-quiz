# Copilot instructions for space-quiz

## Project snapshot

This repository is a lightweight static web app for a space-themed quiz. The entire application is contained in `index.html`, including the markup, styling, quiz data, state management, and browser logic.

There is no framework, bundler, package manager, or build pipeline configured in this repo.

## Build, test, and lint commands

No automated build, lint, or test commands are configured in this project.

For local verification, use a simple static server from the repo root:

```bash
python -m http.server 8000
```

Then open `http://localhost:8000` in a browser and manually verify:
- the first question renders correctly
- answer selection updates score and feedback
- the next-question flow advances correctly
- the final results screen shows the score and restart behavior

If the project gains automated tests later, prefer the repo’s actual runner and keep commands focused on the specific test or file being changed instead of the full suite.

## High-level architecture

- `index.html` is the single source of truth for the app.
- The `quizData` array defines each question, its answer options, and the correct answer.
- `renderQuestion()` builds the current question UI and answer buttons from the active data item.
- `renderResults()` handles the end-of-quiz summary and restart behavior.
- Application state is tracked with `currentIndex`, `score`, and `answered` variables.
- CSS custom properties and media queries drive the light/dark theme and card styling.
- Keyboard support is handled inline with document-level event listeners so users can navigate answers and continue with the quiz without a mouse.

## Key conventions

- Keep the app dependency-free unless a clear requirement makes tooling necessary.
- Prefer native HTML, CSS, and JavaScript patterns already used in this repo instead of introducing frameworks or build tooling for small UI changes.
- Preserve the existing accessibility behavior: focusable answer buttons, keyboard arrows/Enter support, and descriptive labels.
- Keep new quiz content in the `quizData` array rather than creating separate data files or a new state model unless the feature clearly outgrows the single-file structure.
- Maintain the current style of small, self-contained DOM updates via template strings and event listeners rather than splitting into a larger component architecture without justification.
