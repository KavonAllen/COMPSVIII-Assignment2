# Workflow Analysis

**1. What triggers this workflow?**

The workflow is triggered when code is pushed to the `main` branch or when a pull request is created targeting the `main` branch. These triggers allow the project to automatically check changes before they become part of the live website.

**2. What are the four main steps in the build-and-test job?**

The four main steps are:

1. **Checkout code** – Gets the repository files so the workflow can work with the project.
2. **Validate HTML** – Checks the HTML files for errors and problems with the markup.
3. **Check links** – Scans the project for broken links.
4. **Upload artifact** – Uploads the website files so they are available for deployment.

**3. What does "Checkout code" do, and why is it necessary?**

The Checkout code step uses the GitHub Actions checkout action to download the repository's code into the workflow environment. This is necessary because the other steps need access to the website files to validate the HTML, check links, and prepare the site for deployment. Without this step, the workflow would not have the project files to work with.

**4. What is the purpose of the environment configuration?**

The environment configuration identifies the deployment environment as `github-pages`. It also connects the deployment URL to the output from the deployment step. The workflow includes permissions for GitHub Pages deployment and an identity token, which allow GitHub Actions to securely publish the website.

**5. How does automated deployment improve reliability compared to manual deployment?**

Automated deployment improves reliability because the same checks are performed every time the workflow runs. It helps catch HTML errors and identify broken links before changes are deployed. It also reduces the chance of mistakes that can happen when someone manually uploads or publishes files. This makes the deployment process more consistent and saves time.

**6. What happens if you push code to a different branch instead of `main`?**

The workflow will not run when code is pushed to a branch other than `main`, because its push trigger only includes the `main` branch. A pull request targeting `main` from another branch will still trigger the build-and-test job. However, the deployment job will only run after a successful build-and-test job when the event is a push to `main`.