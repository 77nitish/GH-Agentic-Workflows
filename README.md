### Step0 How to Start This Exercise

- Please don't fork or don't clone this repository, instead  "Use This Template" button on the right side of this repository :   

<p align="center">
	<img src="images/create-from-template-repo.png" width="90%" alt="GitHub repository page with the Use this template menu highlighted">
	<br>
	<sub><strong>Step 1:</strong> Select <strong>Use this template</strong>, then <strong>Create a new repository</strong>.</sub>
</p>

- For **Owner** select the organization name provided to you by instructor. Give a specific, unique name to your repository so it'll be easier for you to find if needed : ) 

<p align="center">
	<img src="images/create-from-template-repo2.png" width="65%" alt="GitHub new repository form with owner, repository name, and Create repository highlighted">
	<br>
	<sub><strong>Step 2:</strong> Choose an owner, enter a unique repository name, and create the repository.</sub>
</p>

- Cross-check if "Allow all actions and reusable workflows" is enabled in your repository from Settings => Actions => General

<p align="center">
	<img src="images/actions-enable1.png" width="90%" alt="GitHub Actions permissions page with Settings, Actions, General, and Allow all actions and reusable workflows highlighted">
	<br>
	<sub><strong>Step 3:</strong> Confirm that <strong>Allow all actions and reusable workflows</strong> is selected.</sub>
</p>

- Scroll down in settings page and "Allow GitHub Actions to create and approve pull requests"

<p align="center">
	<img src="images/actions-enable2.png" width="70%" alt="GitHub Actions workflow permissions section with Allow GitHub Actions to create and approve pull requests checked">
	<br>
	<sub><strong>Step 4:</strong> Enable <strong>Allow GitHub Actions to create and approve pull requests</strong>, then click <strong>Save</strong>.</sub>
</p>


# Step1  Setup Your Environment

### Highly Recommended: Please use the pre-configured Github Codespace for today's workshop.


1. Right click the button below to open the **Create Codespace** page in a new tab.

   [![Open in GitHub Codespaces](https://github.com/codespaces/badge.svg)](https://codespaces.new/mburakunuvar/skills-agentic-workflows-that-read-the-room?quickstart=1)


   No need to change options, we'll use the default configuration.

2. Confirm the **Repository** field is your copy of the exercise, not the original template, then click the green **Create Codespace** button.
   - ✅ Your copy: `/your-org/skills-agentic-workflows-that-read-the-room`
   - ❌ Original: `/EmileVerbunt/AgenticWorkflows`

3. Wait for Visual Studio Code to load in your browser. The codespace setup may take a few minutes while it installs dependencies. 

4. Get familiar with the project by 

```bash
briefly explain #codespace 

```


# Step2  QuickStart with a pre-defined GitHub Agentic Workflows.

In this guide you will add an existing, pre-baked workflow to an existing GitHub repository where you are a maintainer 

[the automated Daily Repo Status Report](https://github.com/githubnext/agentics/blob/main/workflows/daily-repo-status.md?plain=1) is just one of many useful workflows that you can quickly implement to your repository.
 
 

### Install GitHub Agentic Workflows and Configure Codespaces

```bash
gh extension install github/gh-aw
gh aw init --codespaces
```

The initialization command prepares your repository for agentic workflows and
updates your copy of `.devcontainer/devcontainer.json` with your repository name
and the permissions required to run GitHub Actions workflows.

Commit and push this repository-specific configuration before rebuilding:

```bash
git add .
git commit -m "configure Codespaces for gh-aw"
git push origin main
```

1. Press `Ctrl+Shift+P` and select **Codespaces: Rebuild Container**.
2. Approve the requested repository permissions. Do not continue without
	authorizing them.
3. Wait for the Codespace to reconnect.

After the rebuild, verify that GitHub Agentic Workflows is available:

```bash
gh aw --version
```


### Add Your First Workflow from GitHub Agentics

```bash
$ gh aw add-wizard githubnext/agentics/daily-repo-status
```

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

```bash 
$ gh aw status 
$ git pull
$ git aw status 
```
 