# GitHub Agentic Workflows Workshop

In this workshop, you will create your own copy of this repository, open it in
GitHub Codespaces, and add a pre-built GitHub Agentic Workflow.

## 1. Create Your Workshop Repository

Do not fork or clone this repository. Create a new repository from the template
so you have an independent copy.

1. Select **Use this template**, then **Create a new repository**.

   <p align="center">
      <img src="images/create-from-template-repo.png" width="85%" alt="GitHub repository page with the Use this template menu highlighted">
   </p>

2. For **Owner**, select the organization provided by your instructor. Enter a
   unique repository name, then select **Create repository**.

   <p align="center">
      <img src="images/create-from-template-repo2.png" width="70%" alt="GitHub new repository form with the owner, repository name, and Create repository button highlighted">
   </p>

3. In your new repository, open **Settings → Actions → General** and confirm:
   - **Allow all actions and reusable workflows** is selected.
   - **Allow GitHub Actions to create and approve pull requests** is selected.

   Select **Save** if you changed either setting.

   <p align="center">
      <img src="images/actions-enable1.png" width="85%" alt="GitHub Actions permissions set to allow all actions and reusable workflows">
   </p>

   <p align="center">
      <img src="images/actions-enable2.png" width="75%" alt="Workflow permissions allowing GitHub Actions to create and approve pull requests">
   </p>

## 2. Open Your Repository in GitHub Codespaces

1. Open the Codespaces creation page:

   <p align="center">
      <a href="https://codespaces.new"><img src="https://github.com/codespaces/badge.svg" alt="Open in GitHub Codespaces"></a>
   </p>

2. In the **Repository** field, select the repository you created in the
   previous section. Keep the default settings and select **Create codespace**.

3. Wait for Visual Studio Code to finish loading. Initial setup may take a few
   minutes while the development container installs its dependencies.

### Explore the Project

- In Copilot Chat, try:

  > Briefly explain #codespace

  <p align="center">
     <img src="images/briefly-explain.png" width="75%" alt="GitHub Copilot Chat explaining the Codespace">
  </p>

- To preview the sample application, right-click `index.html` and select
  **Open with Live Server**.

  <p align="center">
     <img src="images/preview.png" width="70%" alt="Preview of the sample web application">
  </p>

The sample application uses HTML, but GitHub Agentic Workflows can run in
projects built with any language, framework, or runtime.

## 3. Add Your First GitHub Agentic Workflow

You will add the
[Daily Repo Status Report](https://github.com/githubnext/agentics/blob/main/workflows/daily-repo-status.md?plain=1),
a pre-built workflow from the GitHub Agentics repository.

### Install and Initialize `gh-aw`

Run these commands in the Codespace terminal:

```bash
gh extension install github/gh-aw
unset GH_TOKEN GITHUB_TOKEN
gh auth login --web --scopes workflow
gh aw init
```

Complete the browser sign-in when prompted, then return to the same terminal.
The `unset` command ensures that GitHub CLI uses your browser-authenticated
session instead of the restricted token provided by Codespaces.

> [!NOTE]
> If you open a new terminal, run `unset GH_TOKEN GITHUB_TOKEN` again before
> using `gh` or `gh aw`. You do not need to sign in again.

Commit and push the generated configuration:

```bash
git add .
git commit -m "initialize GitHub Agentic Workflows"
git push origin main
```

Confirm that `gh-aw` is available:

```bash
gh aw --version
```

### Add the Daily Repo Status Workflow

Start the setup wizard:

```bash
gh aw add-wizard githubnext/agentics/daily-repo-status
```

Use the following selections:

<table>
   <tr>
      <td width="50%" align="center">
         <a href="images/daily-p1.png"><img src="images/daily-p1.png" width="100%" alt="Select GitHub Copilot CLI as the coding agent"></a>
         <br><sub><strong>1. Select GitHub Copilot CLI</strong></sub>
      </td>
      <td width="50%" align="center">
         <a href="images/daily-p2.png"><img src="images/daily-p2.png" width="100%" alt="Select Copilot requests for authentication"></a>
         <br><sub><strong>2. Choose Copilot requests</strong></sub>
      </td>
   </tr>
   <tr>
      <td width="50%" align="center">
         <a href="images/daily-p3.png"><img src="images/daily-p3.png" width="100%" alt="Choose the daily workflow schedule"></a>
         <br><sub><strong>3. Keep the daily schedule</strong></sub>
      </td>
      <td width="50%" align="center">
         <a href="images/daily-p5.png"><img src="images/daily-p5.png" width="100%" alt="Choose to merge the generated pull request"></a>
         <br><sub><strong>4. Merge the generated pull request</strong></sub>
      </td>
   </tr>
</table>

After the wizard merges the pull request, update your Codespace and run the
workflow:

```bash
git pull
gh aw status
gh aw run
```
