# Pau-Repo

A test repository for working with Codex through local files and Git.

## Our current workflow

We are using Codex on this computer without installing the GitHub connector in ChatGPT. Codex works with a local clone of this repository: it reads and edits files and runs Git commands in that folder.

The README was committed and pushed using Git's existing GitHub authentication on this computer. The browser could be signed out of GitHub while those Git commands still worked.

There are three separate connections:

| Connection | What it does | Needed for this workflow? |
| --- | --- | --- |
| Codex sign-in | Lets us use Codex | Yes |
| Local Git authentication with GitHub | Lets Git push changes to this repository | Yes, when pushing |
| GitHub connector in ChatGPT | Gives supported ChatGPT tools access to GitHub | No, for this local workflow |

We are connected to GitHub through Git when pushing, even though the ChatGPT GitHub connector is not installed. Making a repository public allows anyone to read it; pushing still requires an authorized GitHub account.

## Open this repository in Codex

1. Install Git if it is not already available.
2. Clone the repository into a folder on your computer:

   ```powershell
   git clone https://github.com/pauventic/Pau-Repo.git
   cd Pau-Repo
   ```

3. Open the cloned `Pau-Repo` folder as a local project in the desktop app and use Codex with that project.
4. Ask Codex to inspect or change files. Review its changes before committing and pushing.

If you already have a clone, open that folder instead of cloning it again. Codex needs access to the local folder; pasting a repository link alone does not set up a local project.

[Official OpenAI guide to local projects](https://learn.chatgpt.com/docs/projects)

## What you can ask Codex to do

With access to the local repository and the required tools, Codex can:

- Create and edit files, including a simple web page.
- Explain code and help fix bugs.
- Run the project's build or tests when those tools are installed.
- Check the current branch and list local and fetched remote branches.
- Inspect changed files, compare branches, and explain commit history.
- Create a branch, commit changes, and push when Git has the required access.

The desktop app also provides Git review and commit controls. Available actions depend on the project's setup and permissions.

[Official OpenAI guide to built-in Git tools](https://learn.chatgpt.com/docs/environments/local-environment)

## Check branches and changes

Run these commands inside the repository folder, or ask Codex to run them:

| Command | What it shows |
| --- | --- |
| `git branch --show-current` | Current branch |
| `git branch` | Local branches; `*` marks the current one |
| `git branch -a` | Local branches and remote branches known to this clone |
| `git status` | Changed files and staging status |
| `git diff` | Unstaged changes to tracked files |
| `git diff --staged` | Changes staged for the next commit |
| `git log --oneline --graph --decorate -10` | Recent commits and branch labels |
| `git diff main...HEAD` | Committed changes on this branch since its common ancestor with `main` |

Remote branch information can be out of date. Run `git fetch origin` to refresh it; fetching does not merge changes into your current branch.

## Example prompts

> Check the current branch, list all known branches, and explain any uncommitted changes. Do not change files.

> Fetch the latest branch information from origin, then show which remote branches are available.

> Compare my current branch with main and summarize the committed changes.

> Create a branch named demo-page and add a simple responsive index.html welcome page. Show me the changes before committing.

> Review the README changes, commit them, and push the current branch to origin.

## A simple branch workflow

A branch lets you develop a change separately from `main`:

```powershell
git switch -c demo-page
```

After editing and reviewing `index.html`, save and publish that change:

```powershell
git add index.html
git commit -m "Add demo welcome page"
git push -u origin demo-page
```

These commands are examples to run after the file exists. A local commit saves a version on your computer; pushing sends those commits to GitHub. Review and merge the branch when the change is ready.

## About "Disabled by admin"

If the GitHub installation dialog says **Disabled by admin**, the current ChatGPT workspace has blocked that connector. It does not indicate a problem with this repository. Ask the workspace admin to enable the connector if you need it.

This local workflow has already worked without that connector. It does not set up a Codex Cloud environment, which has its own repository and access configuration.

- [Official OpenAI guidance on plugin controls](https://learn.chatgpt.com/docs/enterprise/apps-and-connectors)
- [Codex Cloud setup, for future cloud work](https://learn.chatgpt.com/docs/cloud)

Documentation checked on October 2, 2026. Interface labels may change.
