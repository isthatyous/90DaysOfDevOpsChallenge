# Git Commands for Tasks 1 to 5

## Task 1: Clone Repository
```sh
git clone https://github.com/isthatyous/90DaysOfDevOpsChallenge.git
cd 2025/git/01_Git_and_Github_Basics
```

## Task 2: Initialize Repository & Add File
```sh
mkdir week-4-challenge
cd week-4-challenge
git init
touch info.txt  # or use vim info.txt
git add info.txt
git commit -m "Initial commit: Add info.txt with introductory content"
```

## Task 3: Set Remote & Push Changes
```sh
git remote add origin https://github.com/isthatyous/90DaysOfDevopsChallenge.git
git remote set-url origin https://<pat-token>@github.com/isthatyous/90DaysOfDevopsChallenge.git
git push -u origin main
git pull origin main
```

## Task 4: View Commit History
```sh
git log
git log --oneline  # Shows commit history in short format
```

## Task 5: Create & Push Feature Branch
```sh
git checkout -b feature-update
git add info.txt
git commit -m "Feature update: Enhance info.txt with additional details"
git push origin feature-update
```

### Merging Feature Branch
Merging can be done using two methods:

1. **GitHub GUI:**
   - Create a Pull Request (PR) on GitHub.
   - Merge the PR.

2. **CLI Method:**
   ```sh
   git switch main  # Switch to main branch
   git merge feature-update  # Merge feature-update into main
   
