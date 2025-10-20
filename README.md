# Quick Guide
---

# JRC-AI Repository Template

This repository was created from the **JRC-AI GitHub Template** for projects by the **SDAIA-KFUPM Joint Research Center for Artificial Intelligence (JRC-AI)**.

> **Audience.** JRC-AI faculty, researchers, students, collaborators, and sponsored projects.

---

## Quick start

1. Click **Use this template** → **Create a new repository** (under the JRC-AI organization).
2. Replace placeholders: `YOUR-PROJECT-NAME`, `YOUR-TEAM` if you are within a team in the organization, and contact emails.
3. Review **License** (below) and adjust if your project needs a different license.
4. Push your code and, if needed, enable GitHub Actions on the first commit.

---

## Join the JRC-AI organization (GitHub)

1. **Create/prepare a GitHub account** (better to enable **2-factor authentication** for further security).
2. **Send your GitHub username** to your project PI/manager or **org admin**
   (`majed.alshaibani@kfupm.edu.sa`), requesting membership and the team(s) you should join (if required).
3. **Accept the invitation** you receive by email/GitHub notifications.
4. In **Settings → Organizations → JRC-AI → People**, set your **organization visibility** to public or private as appropriate.
5. Join the relevant **Teams** for repository access.

> If you need an external collaborator added, ask your PI/manager to request a time-boxed invite.

---

## Transfer an existing repository into JRC-AI

**Prerequisites**

* You are an **Owner** or have **Admin** privileges of the source repository.
* You’ve enabled **2-factor authentication**.
* There are **no pending transfers** or **name conflicts** in the destination org.

**Steps**

1. In the source repo: **Settings → General → Danger Zone → Transfer ownership**.

2. Enter the destination: `KFUPM-JRCAI/<new-repo-name>` and confirm.

3. After transfer, review:

   * **Repo Visibility**: public / internal / private.
   * **Default branch** and **branch protection** rules if needed.
   * **Teams & permissions** (read/write/maintain/admin) if required.
   * **Secrets / variables** (recreate **Actions secrets** under the org repo) for required CI/CD pipelines.
   * **Repository description** and **URL**
   * Make sure to add the primary point of contact (You and your team who worked on research the repo is associated with) in the README.md.

4. Locally, update your remote:

   ```bash
   git remote set-url origin git@github.com:SDAIA-KFUPM-JRC-AI/YOUR-PROJECT-NAME.git
   git push -u origin main
   ```

---

## License (read first)

* **Code**: Licensed under **PolyForm Noncommercial 1.0.0**.
  * Free for **academic, research, and personal** (noncommercial) use.
  * **Commercial / production / monetized** use requires a separate agreement.
  * Keep copyright and license notices.
* **Data and Models**: Default **PolyForm Noncommercial 1.0.0**. It should follow similar constraints to the code.

For commercial licensing or exceptions, contact **[jrc-ai@kfupm.edu.sa](mailto:jrc-ai@kfupm.edu.sa)**.

> **You may build on top of this work** under the above terms. **Please cite it** in academic outputs (see below). Commercial users must contact the center for a license.

---

## Cite this work

For papers, include a BibTeX entry in the README:

```bibtex
@software{YOUR_PROJECT_2025,
  author    = {Your Name and Coauthors},
  title     = {YOUR-PROJECT-NAME},
  year      = {2025},
  publisher = {SDAIA-KFUPM Joint Research Center for Artificial Intelligence (JRC-AI)},
  url       = {https://github.com/SDAIA-KFUPM-JRC-AI/YOUR-PROJECT-NAME},
  note      = {Code licensed PolyForm Noncommercial 1.0.0; contact center for commercial use.}
}
```

If the repository accompanies a **published paper**, include the paper’s BibTeX as well.

---

## Code-sharing practices (minimum standard)

**1) Requirements / dependencies**

* For example, if the project uses Python, provide **Python runtime** requirements in `requirements.txt` and dev tools in `requirements-dev.txt`.
  Example (edit to fit your project):

  ```text
  numpy~=1.26
  scipy~=1.13
  pandas~=2.2
  matplotlib~=3.8
  scikit-learn~=1.5
  jupyterlab~=4.2
  ```
* If you use Conda: add `environment.yml`.
* If you use MATLAB: list toolboxes in `matlab-requirements.txt` and include `setup.m`.
* Record **minimum versions** (Python/Matlab/CUDA/etc.) in the README.

**2) Installation**

Provide one clear path (pick one and verify it works):

```bash
# Option A: venv
python -m venv .venv
source .venv/bin/activate
pip install -U pip
pip install -r requirements.txt
pip install -r requirements-dev.txt  # if developing

# Option B: conda
conda env create -f environment.yml
conda activate jrc-ai-env
```

**3) How to run**

It is highly recommended to include a minimal runnable example for reproduction:

```bash
python -m src.jrc_ai_template   # or: python scripts/train.py --config configs/base.yaml
```

**4) Reproduction**

* Pin seeds / deterministic flags where possible; note any nondeterminism.
* Provide **data access** instructions (do not commit large/raw/PII data).
* Use **sample data** or a **download script** with license/source noted.
* Export environment details:

  ```bash
  python -V
  pip freeze > reproducible-requirements.txt
  ```

**5) Secrets & credentials**

* **Never commit secrets** (passwords, API keys, tokens).
* Use `.env` files locally (already git-ignored) and **GitHub Actions Secrets** for CI. Make sure to ignore this file if you are using a custom .gitignore.
* Rotate/change secret keys that are accidentally exposed.

**6) Data & models**

* Big artefacts → use Git LFS or Hugging Face Repositories.
* Clearly state licenses in for data and for the project.
* If using third-party datasets/models, ensure you have redistribution rights and list them in `THIRD_PARTY_NOTICES.md`.

**7) Testing & CI**

* Add at least one **unit test** in `tests/` and keep CI green.
* This template enables **ruff/flake8/black/pytest**, **CodeQL**, and **Dependabot**.

**8) Structure & docs**

It is recommended to share the repo structure to ease the getting-started phase. You can follow this standard layout:

```
.
├── src/                      # Python package or modules
├── notebooks/                # Experiments (keep deterministic & small)
├── data/                     # (No confidential/PII; see data README)
├── models/                   # Exported/converted artefacts
├── docs/                     # Project documentation
├── .github/                  # CI, issue and PR templates
├── LICENSE / LICENSE-*.      # Licensing files
└── THIRD_PARTY_NOTICES.md
└── README.md                 # Overview
└── requirements.text         # requirements to run the present project
```

Bonus: Add a short **project overview**, **roadmap**, and **limitations** in this README.

---

## Project status

* **Stage**: draft / alpha / beta / stable (choose one).
* **Maintainers**: `@github-handle1`, `@github-handle2` (team: `@JRC-AI/<team>`).
* **Further Contact**: [jrc-ai@kfupm.edu.sa](mailto:jrc-ai@kfupm.edu.sa)

---

## Acknowledgements

This work is part of the **SDAIA-KFUPM Joint Research Center for Artificial Intelligence (JRC-AI)**.
Add funding acknowledgements and grant numbers here.

---

### Legal

© {YEAR} SDAIA-KFUPM JRC-AI. Code under **PolyForm Noncommercial 1.0.0**; data under **CC BY 4.0**; models under **OpenRAIL-M** unless stated otherwise. Commercial use requires a license from the center.
