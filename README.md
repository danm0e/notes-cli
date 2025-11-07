# notes-cli

A small command-line notes app that uses `yargs` to manage notes stored in a local JSON file (`db.json`).

## Summary

`notes-cli` is a minimal Node.js CLI that parses commands with `yargs`. Notes are persisted to `db.json` in the project root. The CLI exposes commands to create, list, find, and remove notes, plus a small web viewer.

## Main features

- Create a new note with optional tags.
- List all saved notes.
- Search notes by text.
- Remove a single note by id or remove all notes.
- Start a tiny web UI to view notes.

## Usage

Install dependencies in the project folder:

    npm install

Make the CLI command available for local running (recommended), in your project directory:

    npm link

After running `npm link` you can use the global `note` command from your shell:

Commands (after `npm link`):

- Create a note (positional content). Optional tags with `--tags` or `-t` as a comma-separated list:

  `note new "Buy milk and eggs" --tags=shopping,groceries`

- List all notes:

  `note all`

- Find notes that match a filter string (applies to note content):

  `note find "milk"`

- Remove a note by numeric id:

  `note remove 3`

- Remove all notes (clean):

  `note clean`

- Start the web viewer (default port 5000):

  `note web`

Or specify a port:

    note web 8080

Notes on tags

Use `--tags` (or `-t`) with `new` to add comma-separated tags. Example:

    note new "Call Alice" --tags=personal,phone`

## Data storage

Notes are persisted to `db.json` in the project root as a simple JSON structure. This keeps the app dependency-free for storage and easy to inspect or edit.

## Files of interest

- `index.js` — CLI entry point
- `src/commands.js` — wiring for `yargs` commands (`new`, `all`, `find`, `remove`, `web`, `clean`)
- `src/notes.js`, `src/db.js` — note and persistence helpers
- `db.json` — local data store

## Development / Tests

Run tests if you want to verify behavior (project includes a small test):

    npm test
