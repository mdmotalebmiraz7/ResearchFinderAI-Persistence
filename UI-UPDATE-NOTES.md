# Research Finder AI — UI update notes

## Reader experience
- Removed the repeated paper title from the PDF reader's top strip; kept a compact processing/ready status and reader actions.
- Made Chat and Translate mutually exclusive so opening translation does not squeeze the PDF into an unusably narrow column.
- Improved reader panel spacing, responsive layout, focus states, and reduced-motion support.

## AI answer rendering
- Added safe rendering for Markdown tables, headings, emphasis, links, lists, horizontal rules, and fenced code blocks.
- Tables are horizontally scrollable on narrow panels and use clear headers, borders, and alternating row backgrounds.
- Wrapped prose lines are joined into readable paragraphs.

## Logs
- PDF processing logs are collapsed by default.
- The Logs drawer now defaults to warnings/errors and includes a “Clear view” control. This only clears the current view, not server logs.

## Ollama on Windows
- Ollama discovery checks the usual Windows install paths when the packaged app's PATH does not include Ollama.
- Starts Ollama with Windows-friendly detached/no-console process flags and tolerates a service already being started by the desktop app.
- Removed the unnecessary `name` field from the `/api/pull` request.

## Validation
- Python syntax check passed for `backend/providers.py` and `backend/app.py`.
- Frontend production build could not be run in this environment because `npm ci` timed out while fetching dependencies. Build and end-to-end Ollama checks still need to be run on a machine with network access and Ollama installed.
