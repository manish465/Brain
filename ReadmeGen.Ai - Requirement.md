## Description
An application that automatically generates detailed, professional-quality `README.md` files for GitHub repositories by analyzing their structure, content, and metadata.  
The application leverages a Large Language Model (LLM) to create human-readable documentation based on repository data (file trees, code snippets, and existing metadata).

The goal is to save developers time, improve project onboarding, and ensure that even minimal or undocumented repositories have presentable, informative README files.
## Scope
- Generator Service : Will take a link to repository and return a `Readme.md`
- Prompt Service : Will take a link to repository and return a prompt for it
### Minimum requirement for generating `Readme.md`
- Project Name
	- **Source:** Often derivable directly from the repository's name itself. Sometimes also explicitly stated in configuration files (like `name` in `package.json` or `setup.py`).
- Project Description
	- **Source:** This is often the hardest part to automate well. Ideally, it comes from
		- A description field in configuration files (`description` in `package.json`, `summary` or `long_description` in `setup.py`)
		- The top-level comment or docstring in the main script/module
		- The repository's description field on platforms like GitHub/GitLab
- Language/Framework Used
	- **Source:** Determined by analyzing file extensions (`.py`, `.js`, `.java`, `.go`, etc.) and identifying key framework-specific files or dependencies (e.g., `pom.xml` for Maven/Java, `package.json` for Node.js, `requirements.txt` or `pyproject.toml` for Python)
- Installation Instructions
	- **Source:** Inferred from dependency management files:
	    - `requirements.txt` / `pyproject.toml` (Python) -> Suggests `pip install` commands.
	    - `package.json` (Node.js) -> Suggests `npm install` or `yarn install`.
	    - `pom.xml` / `build.gradle` (Java) -> Suggests `mvn install` or `gradle build`.
	    - `Gemfile` (Ruby) -> Suggests `bundle install`.
	    - `Dockerfile` -> Suggests `docker build`.
	    - `setup.py` (Python) -> Suggests `pip install .` or `python setup.py install`.
- Basic Usage / How to Run
	- **Source:** This can also be tricky to automate perfectly. Hints come from
		- `scripts` section in `package.json`.
	    - Presence of common entry point files (`main.py`, `app.js`, `index.html`).
	    - `entry_points` in `setup.py`.
	    - Executable permissions on files.
	    - Presence of a `tests` or `examples` directory.
- License Information
	- **Source:**
	    - Presence and content of a `LICENSE` or `LICENSE.md` file.
	    - `license` field in configuration files (`package.json`, `setup.py`, etc.).
