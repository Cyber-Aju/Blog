+++
title= "Day 02/01"
date= '2024-01-02'
draft= 'false'
tags= ["github actions"]
categories= ["Errors"]
+++

## GitHub Actions Deployment Issue: README Modifications, Forceful Push, and Persistent Errors

I initially made changes to the README.md file directly on GitHub. Later, I also made modifications to the README file locally. When GitHub Actions automatically triggered a deployment, it encountered an error. To resolve this, I forcefully pushed the changes from my local storage to GitHub using 'git push -f origin main'. The modified README file was successfully uploaded to GitHub. However, despite this, the GitHub Actions deployment continued to show an error, impacting the GitHub Pages hosted through the actions. The Problem is Solved using google and ChatGPT lol!!

If you force pushed to the `main` branch after making changes directly on GitHub, it can cause inconsistencies and potential issues, especially if the GitHub Actions workflow is triggered during or after the force push. Here's a step-by-step guide to resolve this issue:

1. **Backup Local Changes:**
   - If you have local changes that you want to keep, make sure to commit or stash them before proceeding.

2. **Fetch Changes:**
   - Fetch the latest changes from the remote repository to ensure your local repository is up to date.
     ```bash
     git fetch origin
     ```

3. **Revert Force Push Locally:**
   - Revert the force push you did locally. This step is necessary to avoid pushing a forceful history rewrite to the remote.
     ```bash
     git reflog
     ```
     Find the commit hash before the force push and reset to that commit:
     ```bash
     git reset --hard <commit-hash>
     ```
     Replace `<commit-hash>` with the hash you found in the reflog.

4. **Pull Latest Changes:**
   - Pull the latest changes from the remote repository to ensure you have the most up-to-date code.
     ```bash
     git pull origin main
     ```

5. **Reapply Local Changes:**
   - If you stashed changes earlier, apply the stash.
     ```bash
     git stash apply
     ```

6. **Commit and Push:**
   - Commit your changes locally.
     ```bash
     git add .
     git commit -m "Your commit message"
     ```

   - Push the changes to the remote repository.
     ```bash
     git push origin main
     ```

7. **GitHub Actions:**
   - After pushing the changes, GitHub Actions should pick up the new commit and trigger the workflow. Check the GitHub Actions tab to ensure the workflow runs successfully.

8. **GitHub Pages Deployment:**
   - If GitHub Pages deployment is part of your workflow, ensure that it has the correct configuration and is set up to deploy the `main` branch.

By following these steps, you should be able to resolve inconsistencies between your local and remote repositories and avoid force pushing in a way that disrupts GitHub Actions workflows. Always be cautious with force pushes, especially on shared branches and in collaboration scenarios.

After i Make changes to 'deploy.yml' here i rectified ..!