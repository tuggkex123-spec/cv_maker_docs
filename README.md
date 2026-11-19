# CV Maker

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE) [![Node.js 18+](https://img.shields.io/badge/Node.js-18%2B-339933?logo=node.js&logoColor=white)](https://nodejs.org) [![React](https://img.shields.io/badge/React-61DAFB?logo=react&logoColor=black)](https://react.dev) [![Vite](https://img.shields.io/badge/Vite-646CFF?logo=vite&logoColor=white)](https://vite.dev) [![Live demo](https://img.shields.io/badge/Live%20demo-cvmaker.codepapa.xyz-blue)](https://cvmaker.codepapa.xyz)

CV Maker helps you write and tailor a CV in your browser. Start from scratch or from a backup. An optional AI assistant suggests edits for a specific job, and you accept or reject each one. Export the finished CV as a Word file or a PDF.

**Live demo:** https://cvmaker.codepapa.xyz

The app has no account and no server. Your CV stays in your browser. To use the AI assistant, you supply your own API key. Your CV text then goes directly from your browser to the provider you choose. Read [How the app works](docs/concept.md) for the design behind this.

## Features

- Edit sections and reorder them by drag and drop
- Choose a Classic or With photo template
- Save and restore backups
- Get AI suggestions for a job, and review each one
- Export as Word (.docx) or save as PDF
- Use the interface in English or Polish

## Get started

### Requirements

- Node.js 18 or newer. The project does not declare a version, so this follows the minimum for Vite 5. 
- npm, which comes with Node.js
- A modern browser, such as Chrome, Firefox, Safari or Edge

### Install and run

```bash
git clone https://github.com/krzysztof-durski/cv_maker.git
cd cv_maker
npm install
npm run dev
```

Open the address the terminal shows, usually http://localhost:5173.

### Hello World: check the setup

1. Open the app.
2. Enter a name under **Personal Info**.
3. Click the **⋯ menu**, then **Export as Word (.docx)**.
4. Open the file and check that it shows the name.

If the name appears in the file, the setup works. For a guided walkthrough, follow the [tutorial](docs/tutorial-first-cv.md). For specific tasks, use the [how-to guides](docs/how-to.md).

## Run the tests

```bash
npm test
```

This runs the Node and Vitest test suites. To run Vitest on every change, run `npm run test:watch`.

## Documentation

| Document | For |
|---|---|
| [Tutorial: build your first CV](docs/tutorial-first-cv.md) | New users |
| [How-to guides](docs/how-to.md) | Users with a specific task |
| [Reference](docs/reference.md) | Anyone who looks up a field, a menu item, a limit or an error message |
| [About CV Maker](docs/concept.md) | Anyone who wants the background, including privacy and the AI design |
| [Contributing](CONTRIBUTING.md) | Developers who change the code |

## Privacy and your API key

- The app stores your CV in your browser. It has no server that keeps CV data.
- The AI assistant is optional. You provide your own key, which the app stores in your browser.
- Your CV and any job text you attach go to the provider you choose. Check that provider's data policy before you add personal data.

## Roadmap

The project has no published roadmap. [verify: check the repository for a roadmap or project board, and replace this line if one exists]

## Community and contributions

Contributions are welcome. Read [CONTRIBUTING.md](CONTRIBUTING.md) for the setup, the commands and the steps to open a pull request. Report bugs and suggest changes through the repository's issue tracker. [verify: confirm issues are enabled on the repository]

## License

MIT License. See [LICENSE](LICENSE).
