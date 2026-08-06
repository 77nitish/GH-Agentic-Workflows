## APPENDIX

### Creating a Personal Access Token (PAT) for Personal Repositories

1. Set up the `COPILOT_GITHUB_TOKEN` repository secret that the Copilot engine will use later in the exercise.

   1. [Create a fine-grained personal access token](https://github.com/settings/personal-access-tokens/new?name=COPILOT_GITHUB_TOKEN&description=GitHub+Agentic+Workflows+-+Copilot+engine+authentication&user_copilot_requests=read) with **Copilot Requests** set to **Read**.
      <details>
        <summary>Token permissions details</summary><br/>
        <img width="30%" alt="Fine-grained token permissions 1" src="https://github.com/mburakunuvar/skills-agentic-workflows-that-read-the-room/blob/main/.github/images/fine-grained-token-1.png?raw=true" />
        <img width="30%" alt="Fine-grained token permissions 2" src="https://github.com/mburakunuvar/skills-agentic-workflows-that-read-the-room/blob/main/.github/images/fine-grained-token-2.png?raw=true" />
      </details>
   2. Copy the token value.
   3. In your copied exercise repository, go to **Settings** > **Secrets and variables** > **Actions**.
   4. Select **New repository secret**.
   5. Name the secret `COPILOT_GITHUB_TOKEN`, paste the token value, and save it.
      <details>
        <summary>Repository Action secrets details</summary><br/>

        <img width="30%" alt="Repository actions secrets 1" src="https://github.com/mburakunuvar/skills-agentic-workflows-that-read-the-room/blob/main/.github/images/repo-secrets-1.png?raw=true" />
        <img width="30%" alt="Repository actions secrets 2" src="https://github.com/mburakunuvar/skills-agentic-workflows-that-read-the-room/blob/main/.github/images/repo-secrets-2.png?raw=true" />
        <img width="30%" alt="Repository actions secrets 3" src="https://github.com/mburakunuvar/skills-agentic-workflows-that-read-the-room/blob/main/.github/images/repo-secrets-3.png?raw=true" />
      </details>

> [!CAUTION]
> Never paste a real token into a comment, markdown file, pull request, or Copilot Chat message. Only add it through the repository secrets UI.

2. Set the Actions workflow permissions to **Read and write permissions** so the agent can propose changes to the website content.

   1. In your copied exercise repository, go to **Settings** > **Actions** > **General**.
   2. Under **Workflow permissions**, select **Read and write permissions**.
   3. Check **Allow GitHub Actions to create and approve pull requests**.
   4. Save the changes.

   <details>
     <summary>Actions workflow permissions details</summary><br/>

     <img width="40%" alt="Actions workflow permissions 1" src="https://github.com/mburakunuvar/skills-agentic-workflows-that-read-the-room/blob/main/.github/images/actions-permissions-1.png?raw=true" />

  </details>


     <p align="center">
     <img src="images/actions-enable1.png" width="85%" alt="GitHub Actions permissions set to allow all actions and reusable workflows">
     </p>

## Resources
- [Agentic workflows no longer need a personal access token](https://github.blog/changelog/2026-06-11-agentic-workflows-no-longer-need-a-personal-access-token/)
