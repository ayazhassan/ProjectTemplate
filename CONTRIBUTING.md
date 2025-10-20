# Contributing to JRC-AI Projects

Thanks for your interest in contributing to the **SDAIA-KFUPM Joint Research Center for Artificial Intelligence (JRC-AI)** projects! This guide explains how to get set up, propose changes, and meet our quality, security, and licensing standards.

---

## 1) How to ask questions or propose work

* **Bugs / features** → open a GitHub Issue using the appropriate template.
* **Small fixes** → open a Pull Request (PR) directly; mark it **Draft** if still in progress.
* **Large changes / design work** → open an Issue first and propose an approach (optionally add a short “RFC” doc in `docs/`).



---

## 2) Development setup

### Python

1. Use **Python ≥ 3.11**.
2. Create an environment and install deps:

   ```bash
   python -m venv .venv && source .venv/bin/activate
   pip install -U pip
   pip install -r requirements.txt
   pip install -r requirements-dev.txt
   ```
3. (Optional) With Conda:

   ```bash
   conda env create -f environment.yml
   conda activate jrc-ai-env
   ```

### MATLAB

* Ensure the required toolboxes in `matlab-requirements.txt` are installed.
* Run `setup.m` once to check toolboxes and add paths.

---

## 3) Workflow & branching

* Default branch: **`main`**.
* Create feature branches: `feature/<short-desc>`, `fix/<short-desc>`, `docs/<short-desc>`.
* Keep PRs focused and small; link the Issue they address.

### Commits

* Follow **Conventional Commits** where possible:

  * `feat:`, `fix:`, `docs:`, `test:`, `refactor:`, `chore:`, `build:`, `ci:`
* Sign every commit with the **DCO**:

  ```bash
  git commit -s -m "feat: add fault classifier"
  ```

  The sign-off line is automatically added and asserts the *Developer Certificate of Origin*.

---

## 4) Quality bar (what CI expects)

* **Formatting & linting:** `make fmt` and `make lint` (uses `black`, `ruff`, `flake8`).
* **Tests:** add/maintain **pytest** unit tests; run `make test`. Target **>=80%** coverage for changed code.
* **Type hints:** for new/changed modules, add Python type hints where practical.
* **No prints in libraries:** use `logging` with sensible levels.

A PR is ready when:

* CI is **green** (unit tests + linters).
* New code is **documented** (docstrings, README/docs update).
* You’ve added **at least one test** per new feature or bug fix.
* You’ve updated `THIRD_PARTY_NOTICES.md` if you added dependencies.

---

## 5) Style guides

### Python

* PEP-8; **snake\_case** for functions/variables, **CamelCase** for classes, **UPPER\_CASE** for constants.
* One module = one purpose; keep functions short and cohesive.
* Public APIs documented with docstrings (`"""Summary\n\nArgs:\nReturns:\nRaises:\n"""`).
* Prefer **pure Python** and vectorized NumPy/Pandas; isolate heavy I/O.

### MATLAB

* One function per file; add help text and examples at the top.
* Use `matlab.unittest` for tests in `tests_matlab/`.
* Avoid modifying the MATLAB path globally; rely on `setup.m`.

### Notebooks

* Keep notebooks **deterministic** (set seeds, fixed versions).
* Clear large outputs before committing; keep outputs small.
* Move long-running experiments to scripts in `scripts/` with CLI flags.

---

## 6) Documentation

* Keep **README** up to date: overview, quick start, dependencies, how to run, reproduction notes, and license.
* Add any detailed docs to `docs/` and link from the README.
* If related to a **paper**, include its **BibTeX** in the README and `CITATION.cff`.

---

## 7) Data, models, and large files

* **Do not commit** confidential, proprietary, or personal data.
* Use **Git LFS** or external storage for large artefacts; provide a small sample or a download script.
* Document the **source and license** of any dataset/model you use.
* Code, data, and models must each have clear **license files** (`LICENSE`, `LICENSE-DATA`, `LICENSE-MODEL`).

---

## 8) Security & privacy

* **Never commit secrets** (API keys, tokens, passwords).

  * Use `.env` locally (already in `.gitignore`) and **GitHub Actions Secrets** in CI.
* Remove or anonymize PII; follow institutional/contractual data handling rules.
* Report vulnerabilities privately to **[security@jrc-ai.example](mailto:security@jrc-ai.example)** (see `SECURITY.md`).
* Avoid introducing dependencies with known high-severity CVEs; Dependabot is enabled.

---

## 9) Licensing & intellectual property

* **Inbound license (default):** By contributing, you agree your contribution is licensed under **PolyForm Noncommercial 1.0.0** (for code) unless the maintainers agree otherwise in writing **before** the PR.
* Add an **SPDX header** at the top of source files:

  ```
  SPDX-License-Identifier: PolyForm-Noncommercial-1.0.0
  Copyright (c) <YEAR> SDAIA-KFUPM JRC-AI
  ```
* If you bring in third-party code or data:

  * Ensure its license **permits** our use and redistribution.
  * **Preserve** original LICENSE/NOTICE files and add entries to `THIRD_PARTY_NOTICES.md`.
  * Avoid GPL/AGPL libraries unless explicitly approved (they may conflict with our main license).
* **Commercial use:** our default code license is **Noncommercial**. Commercial users must obtain a separate license from the center (**[licensing@jrc-ai.example](mailto:licensing@jrc-ai.example)**).

---

## 10) Versioning & releases

* We follow **SemVer** (MAJOR.MINOR.PATCH).
* Tag releases, generate release notes, and update `CITATION.cff`.
* If you mint a DOI (e.g., Zenodo), add the badge to the README.

---

## 11) Contribution checklist (for PRs)

* [ ] Issue linked and scope agreed (for non-trivial changes)
* [ ] Code formatted & linted (`make fmt && make lint`)
* [ ] Tests added/updated and passing (`make test`)
* [ ] Docs/README updated; examples reproducible
* [ ] No secrets, PII, or licensed content without permission
* [ ] `THIRD_PARTY_NOTICES.md` updated (if applicable)
* [ ] Commits signed with **`-s`** (DCO) and use conventional messages
* [ ] CI green and reviewers requested

---

## 12) Maintainers

* Ensure branch protections and required checks are enabled.
* Enforce license and security policies during review.
* Merge with **squash** or **rebase**; keep history tidy.
* Close stale issues after reasonable follow-up.

---

## 13) Contact

* General/project questions: **[majed.alshaibani@kfupm.edu.sa](mailto:majed.alshaibani@kfupm.edu.sa)**
* Licensing: **[majed.alshaibani@kfupm.edu.sa](mailto:majed.alshaibani@kfupm.edu.sa)**
* Security: **[majed.alshaibani@kfupm.edu.sa](mailto:majed.alshaibani@kfupm.edu.sa)**

Thank you for helping us build reliable, reproducible, and responsibly licensed AI research at **JRC-AI**!
