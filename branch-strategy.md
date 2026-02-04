# Git-Flow Workflow
<img width="956" height="442" alt="image" src="https://github.com/user-attachments/assets/63541dd7-a2e3-4d00-a482-a705b32b0832" />


The Git-Flow model introduces a structured branching strategy optimized for projects with scheduled releases. It maintains distinct branches for different stages of development:

- **main**: Stores production-ready releases and serves as the source for tags.
- **develop**: Acts as the integration branch where features converge before a release.

Supporting branches help manage various workflows:
- **feature/**: Created from `develop` to develop enhancements, then merged back into `develop`.
- **release/**: Spawned from `develop` to fine-tune new versions; merges into both `main` and `develop` upon completion.
- **hotfix/**: Revives `main` for urgent production fixes; merges into both `main` and `develop`.

This workflow helps manage complexity between development, release preparation, and production.

---

## Git Commands

### Initialize (manual setup)
``` bash
git checkout -b main
git checkout -b develop
```

### Initialize via Git-Flow
```bash
git flow init
```


Creates main and develop branches.

## Features
``` bash
git checkout -b feature/<feature_name> develop   # start feature
git checkout develop
git merge feature/<feature_name>                 # finish feature
git branch -d feature/<feature_name>
```

## Releases and hotfix are rarely used but here they are:
### Releases
``` bash
git checkout -b release/<version> develop        # start release
git checkout main
git merge release/<version>                      # merge into main
git tag -a <version> -m "Release <version>"      # tag release
git checkout develop
git merge release/<version>                      # merge back into develop
git branch -d release/<version>
```
### Hotfix
``` bash
git checkout -b hotfix/<version> main            # start hotfix
git commit -am "Fix: <description>"
git checkout main
git merge hotfix/<version>                       # merge into main
git tag -a <version> -m "Hotfix <version>"       # tag hotfix
git checkout develop
git merge hotfix/<version>                       # merge back into develop
git branch -d hotfix/<version>
```

For more details: https://www.atlassian.com/git/tutorials/comparing-workflows/gitflow-workflow
