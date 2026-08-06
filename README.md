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

1. Click **Code** to Open the Codespaces creation page:

   <p align="center">
      <a href="https://codespaces.new"><img src="images/create-codespace.png" width="40%"  alt="Open in GitHub Codespaces"></a>
   </p>

2. Ckick Create Codespaces on Main , no need to change any settings.

3. Wait for Visual Studio Code to finish loading. Initial setup may take a few minutes while the development container installs its dependencies. 

4. Trust Folder and Continue if requested 

 <p align="center">
      <a href="https://codespaces.new"><img src="images/trust-codespaces.png" width="40%"  alt="Open in GitHub Codespaces"></a>
   </p>

### Explore the Project

- In Copilot Chat, try some sample questions such as 

  > Briefly explain #codespace
  > Are there any agentic  workflows used in this repo ? Don't take any action. 

  <p align="center">
     <img src="images/briefly-explain.png" width="40%" alt="GitHub Copilot Chat explaining the Codespace">
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
```

Follow these authentication steps:

| Step | Where | Action |
| :--: | --- | --- |
| **1** | Terminal | For the preferred protocol, select **HTTPS**. |
| **2** | Terminal | When asked to authenticate Git, select **Yes**. |
| **3** | Terminal | Copy the one-time code, then press **Enter** to open GitHub. |
| **4** | Browser | Continue with your signed-in account and enter the one-time code. |
| **5** | Browser | Select **Authorize GitHub CLI**. |
| **6** | Terminal | Wait for the **Congratulations, you're all set!** confirmation. |

After authentication succeeds, return to the same terminal and initialize
`gh-aw`:

```bash
gh aw init
```

> [!TIP]
> If **Agentic Workflows Agent** does not appear in Copilot Chat, open the
> Command Palette and run **Developer: Reload Window**.

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

Follow these five wizard steps:

| Step | When prompted for | Select |
| :--: | --- | --- |
| **1** | Coding agent | **GitHub Copilot CLI** |
| **2** | Authentication method | **Copilot requests** (uses your organization's Copilot billing; no PAT required) |
| **3** | Schedule | **Daily** |
| **4** | Pull request creation | **Yes, create a pull request** |
| **5** | Pull request handling | **Attempt to merge** |

Use the screenshots below as a visual reference:

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
         <a href="images/daily-p5.png"><img src="images/daily-p5.png" width="100%" alt="Choose whether to attempt to merge the generated pull request"></a>
         <br><sub><strong>5. Attempt to merge the pull request</strong></sub>
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

## 4. Create Your First Agentic Workflow

1. In Copilot Chat, select the **Agentic Workflows Agent**.

2. Submit a prompt like this:

   ```text
   Create .github/workflows/new-day.md as an agentic workflow Markdown file.

   - Run the workflow every day or on demand with workflow_dispatch.
   - Give the workflow edit access through the tools configuration.
   - Use safe-outputs with create-pull-request so the agent can propose changes
     without writing directly to main.
   - Add the day of the run to the navbar in index.html.
   - Create a pull request.
   - Check that the agentic workflow configuration syntax is valid.
   - Do not compile the workflow.
   ```

   <p align="center">
      <img src="images/promptToExecution.png" width="100%" alt="Agentic workflow process from prompt to GitHub Actions execution">
   </p>

3. After the agent creates the workflow, compile it in the terminal:

   ```bash
   gh aw compile
   ```

## 5. Create Your 2nd Agentic Workflow

1. In Copilot Chat, select the **Agentic Workflows Agent**.

2. Submit the following prompt:

   ```text
   Create .github/workflows/daily-new-infos.md as an agentic workflow Markdown file.

   Configure the workflow to:

   - Run every six hours and on demand with workflow_dispatch.
   - Use web fetch to read the GitHub Agentic Workflows Frequently Asked
     Questions page:
     https://github.github.com/gh-aw/reference/faq/
   - Select one FAQ that is not already shown in index.html.
   - Add the selected FAQ to index.html as a new popup for the day on which the
     workflow runs. Add that day to the Daily Updates navigation so it opens the
     new popup, and match the existing page structure and styling.
   - Give the workflow edit access through its tools configuration.
   - Use safe-outputs with create-pull-request so the agent can propose changes
     without writing directly to main.
   - Create a pull request for the proposed changes.
   - Check that the agentic workflow configuration syntax is valid.
   - Do not compile the workflow.
   ```

3. After the agent creates the workflow, compile it in the terminal:

   ```bash
   gh aw compile
   ```