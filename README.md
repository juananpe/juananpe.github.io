# Hugo + GitHub Pages + GitHub Actions = ❤️

This repository is a self-contained template for how to deploy a
Hugo static site, hosted on GitHub, and deployed to GitHub Pages hosting,
using the continuous integration available through GitHub Actions.

## Local Development & Testing

To run this Hugo site locally:

### Prerequisites

- [Hugo](https://gohugo.io/getting-started/installing/) (install with `brew install hugo` on macOS)
- [Git](https://git-scm.com/)

### 1. Clone the repository (with submodules)

```sh
git clone --recurse-submodules <repo-url>
cd <repo-directory>
```

If you already cloned without `--recurse-submodules`, run:

```sh
git submodule update --init --recursive
```

### 2. Start the Hugo development server

```sh
hugo server -D
```

- The `-D` flag includes draft content in the preview.
- By default, the site will be available at: [http://localhost:1313/genai-crew/](http://localhost:1313/genai-crew/)

### 3. View your site

Open your browser and go to: [http://localhost:1313/genai-crew/](http://localhost:1313/genai-crew/)

---

- The site will automatically reload as you edit content.
- To stop the server, press `Ctrl+C` in the terminal.

---

For deployment instructions, see the GitHub Actions workflow and documentation.
