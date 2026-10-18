# Copilot instructions

## Project structure and runtime

The project is a self-contained Spanish-language space-exploration quiz. `index.html` is the entire application: its markup, styles, question data, and browser-side JavaScript are all in that file. Open it directly in a browser (`file://`); no server, build step, package manager, or external dependency is required.

There is no configured build, test, or lint command. For browser behavior changes, verify the actual quiz flow in a browser: answer questions, check score and progress, complete the quiz, and restart.

## Application design and conventions

- Keep the app dependency-free and self-contained in `index.html`; do not introduce a framework, external font, asset, or server requirement.
- The `questions` array is the source of truth for quiz content. Each entry has a Spanish `question`, four `answers`, a zero-based `correct` answer index, and an explanatory `fact`. The quiz length and question counter derive from this array.
- `renderQuestion()` creates the answer buttons from the current question; `chooseAnswer()` locks the choices, updates score/progress, and displays the explanation; `showResults()` selects the score reaction. Keep these state transitions consistent with the restart handler.
- Styling uses CSS custom properties in `:root`, with automatic dark-theme overrides in `@media (prefers-color-scheme: dark)`. Preserve the narrow centered layout, responsive spacing, and reduced-motion handling in `@media (prefers-reduced-motion: reduce)`.
- Keep quiz copy in Spanish. Answer choices and navigation are native buttons; retain keyboard focus visibility, focus movement between questions/results, and live announcements for feedback.
