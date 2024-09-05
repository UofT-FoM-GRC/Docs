# Documentation for GRC Members

This is the documentation for GRC members working on the data analysis part of the project. It contains information on the best practices for version control, data analysis, and other useful tips.


## Project Layout


```bash
.
├── config              # Configuration files
│
├── data                
│   ├── cleaned         # Cleaned output
│   ├── google          # Google Form API output (JSON)
│   ├── misc            # Miscellaneous data
│   └── raw             # Unprocessed data
│
├── docs                # Documentation
├── figures             # Figures for Final Report
│
├── src             
│   ├── api             # Code for interacting with APIs (i.e. Google Forms)
│   ├── models          # Schema definitions
│   ├── notebooks       # Jupyter notebooks
│   ├── R               # R scripts
│   ├── services        # Business logic
│   └── utils           # Utility functions
│
├── tests               # Unit tests
├── mkdocs.yml          # MkDocs configuration
├── poetry.lock         # Poetry lock file
├── pyproject.toml      # Poetry project file
└── README.md           # Project README
```

## Getting Started

### Prerequisites

Ensure you have Python 3.12 installed on your machine. You can download it from the [official website](https://www.python.org/downloads/).

### Installation

1. Clone the repository

```bash
git clone https://github.com/UofT-FoM-GRC/Data_Analysis.git
cd Data_Analysis
```

2. Install the dependencies

```bash
poetry install
```

3. Activate the virtual environment

```bash
poetry shell
```

### VSCode Extensions

- [autoDocstring](https://marketplace.visualstudio.com/items?itemName=njpwerner.autodocstring) - Automatically generates Python docstrings.
- [Better Comments](https://marketplace.visualstudio.com/items?itemName=aaron-bond.better-comments) - Improve your code commenting by annotating with alert, informational, TODOs, and more.
- [Conventional Commits](https://www.conventionalcommits.org/en/v1.0.0/) - A specification for adding human and machine
- [Github Pull Requests and Issues](https://marketplace.visualstudio.com/items?itemName=GitHub.vscode-pull-request-github) - Pull request and issue functionality built into Visual Studio Code.
- [Markdown All in One](https://marketplace.visualstudio.com/items?itemName=yzhang.markdown-all-in-one) - All you need to write Markdown (keyboard shortcuts, table of contents, auto preview and more).
- [Path Intellisense](https://marketplace.visualstudio.com/items?itemName=christian-kohler.path-intellisense) - Autocompletes filenames.
- [Prettier - Code formatter](https://marketplace.visualstudio.com/items?itemName=esbenp.prettier-vscode) - Code formatter using Prettier.
- [Pylance](https://marketplace.visualstudio.com/items?itemName=ms-python.vscode-pylance) - A new language server for Python.
- [Python](https://marketplace.visualstudio.com/items?itemName=ms-python.python) - Linting, debugging, Jupyter Notebooks, and more.
- [Python Indent](https://marketplace.visualstudio.com/items?itemName=KevinRose.vsc-python-indent) - Indentation for Python.
- [R](https://marketplace.visualstudio.com/items?itemName=Ikuyadeu.r) - R language support.
- [R Debugger](https://marketplace.visualstudio.com/items?itemName=Ikuyadeu.r-debugger) - R debugging support.
- [Ruff](https://marketplace.visualstudio.com/items?itemName=npxbr.ruff-vscode) - Python linting.
- [YAML](https://marketplace.visualstudio.com/items?itemName=redhat.vscode-yaml) - YAML language support.

## Previewing these docs

These docs are built using [MkDocs](https://www.mkdocs.org). To preview these docs locally, you will need to install MkDocs and the Material theme.

### Commands

* `mkdocs new [dir-name]` - Create a new project.
* `mkdocs serve` - Start the live-reloading docs server.
* `mkdocs build` - Build the documentation site.
* `mkdocs -h` - Print help message and exit.

