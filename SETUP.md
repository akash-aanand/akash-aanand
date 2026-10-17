# Setup guide — GitHub profile README

This kit is written for macOS and uses the GitHub username `akash-aanand` as the best-known value from previous project URLs. **Verify the exact username shown on your GitHub profile first.** Your profile repository must be named exactly that username.

## 1. Create the profile repository

1. Open https://github.com/new
2. Set **Repository name** to your exact GitHub username (for example, `akash-aanand`).
3. Select **Public**.
4. You may check **Add a README file**; the commands below will replace it.
5. Create the repository.

GitHub only displays the profile README when the repository name matches your username, the repo is public, and a non-empty `README.md` exists at the root.

## 2. Download and unzip the kit

Download `github-profile-readme-kit.zip` and extract it. If it is in Downloads, this usually creates `~/Downloads/github-profile-readme-kit`.

## 3. Clone your profile repository

In Terminal, replace `akash-aanand` in these commands if your actual username is different:

```bash
mkdir -p ~/Developer
cd ~/Developer
git clone https://github.com/akash-aanand/akash-aanand.git
cd akash-aanand
```

If Git prompts you to authenticate, follow the GitHub sign-in/browser prompt or your configured Git credential workflow. Do not paste a password or token into chat.

## 4. Copy the kit into the cloned repo

If you extracted the ZIP to Downloads exactly as above:

```bash
cp -R ~/Downloads/github-profile-readme-kit/. .
```

If your extraction folder is somewhere else, adjust the source path. The trailing `/.` copies hidden files such as `.github` too.

## 5. Personalize the README before pushing

Open the folder in VS Code:

```bash
code .
```

Edit `README.md`. Search for `EDIT ME`, `TODO`, `PLACEHOLDER`, and `Check repo URL`. Specifically:

- Click each project URL and confirm it opens the correct public repository.
- Replace LinkedIn, email, and portfolio placeholders.
- Remove technologies you would not yet feel confident discussing in an interview.
- If your GitHub handle is not `akash-aanand`, update all links and the optional raw SVG URLs.

The SVG assets are local files, so the main banner and terminal card do not rely on a third-party image service. The `<picture>` markup follows GitHub's documented light/dark image technique.

## 6. Commit and push

```bash
git status
git add README.md assets .github/workflows/snake.yml SETUP.md SOURCES.md
git commit -m "Build GitHub profile README"
git push
```

If the repository already had a README, the copy command overwrites the local file; review `git diff` before committing if you need to keep anything from the old README.

## 7. Enable and run the snake workflow (optional)

1. Open your repository on GitHub and click **Actions**.
2. If prompted, enable workflows for the repository.
3. Choose **Generate contribution snake** in the left sidebar.
4. Click **Run workflow** and run it on `main`.
5. Open the run and wait for it to finish successfully. No extra API key or GitHub secret is required; the workflow uses the repository's automatic `GITHUB_TOKEN` with only `contents: write` permission.
6. Open the branch dropdown and select `output`. Confirm `github-snake.svg` and `github-snake-dark.svg` exist.
7. Only then edit `README.md` and uncomment the optional snake `<picture>` block near the bottom. Update its username/repository path if needed, then commit and push again.

If the workflow cannot push to `output`, open **Settings → Actions → General → Workflow permissions** and check whether repository/organization policy restricts write access. The workflow explicitly requests `contents: write`, but an organization policy may still prevent it.

## 8. Verify the finished profile

- Open `https://github.com/YOUR_USERNAME` in a private/incognito window.
- Preview the repository's `README.md` directly and confirm the header/terminal panels render.
- Switch GitHub between light and dark themes and confirm the SVG version changes.
- Test every project/social link and check the README on a narrow mobile viewport.
- Check Actions logs if the optional snake fails. The base README should work even if the snake workflow is never enabled.

## Common Git issues

- **`remote origin already exists`:** run `git remote -v`; don't add a second `origin` without inspecting the existing URL.
- **`rejected (fetch first)`:** your GitHub repository contains commits not in the local branch. Don't force-push; inspect `git status` and `git log --oneline --decorate -5`, then pull/reconcile as appropriate.
- **`nothing to commit`:** run `git status`; the files may not have copied into the cloned repo or may be unchanged.
