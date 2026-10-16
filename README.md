# StudyOS — Personal Study Dashboard

A beginner-friendly, responsive study dashboard built with plain HTML, CSS, and JavaScript. It runs entirely in your browser and does not require an API key, server, or installation.

## Run it

1. Download and extract `studyos.zip` (or open `index.html` directly).
2. Open `index.html` in Chrome, Edge, Firefox, or another modern browser.
3. Add subjects and chapters, create tasks, set a daily goal, and use the Pomodoro timer.

## Features in this MVP

- Add/edit/delete subjects and add chapters under each subject.
- Mark chapters complete and see subject-wide progress.
- Create, edit, filter, sort, and complete study tasks.
- 25-minute focus, 5-minute short break, and 15-minute long break timer.
- Daily goal tracking and a last-seven-days focus chart.
- Responsive sidebar/dashboard layout.
- Automatic saving with `localStorage`; refreshing the page keeps your data.

## Important storage note

Data is stored in the browser on the device where you use the app. It is not automatically synced between devices. Clearing browser site data can delete it, so do not clear storage if you need your study records.

## Project structure

- `index.html` — the complete first MVP (markup, styles, and browser-side logic).

Keeping the first version in one file makes it easier to run and understand. As the project grows, split it into `css/style.css` and `js/app.js`.

## Current limitations / next steps

- AI study assistant is intentionally not included yet; the core app works without any API key.
- Weekly chart uses completed focus sessions.
- A focus session is recorded when the 25-minute timer finishes; pausing or resetting does not record a session.
- Before public deployment, add data export/import and test on multiple browsers.
- If you later add an AI backend, keep API keys on the server (for example, in FastAPI environment variables), never in frontend JavaScript.
