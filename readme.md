## DevOps is the process of how an idea becomes software in user's hands and gets better with feedback.

Stages in Dev + Ops:

Plan:

- What to Build
- When to Ship
- Who owns what
- Measure success
- Page Speed
- User Growth
- Revenue

Use tools like Jira, Linear, Github projects, Notion, etc.

Code:

- Clean, Modular and Testable code
- Use Git for version control

Build:

- Preparing code for production
- Compiling or Transpiling source code
- Bundled or packaged (like in Docker)
- Check for linting or security mistakes

Test:

- To catch bugs early
- Unit, Integration and End to end tests

Example: Payment system: Unit tests verify math for totals, Integration tests ensure checkout works with DB and End to end tests simulate customer completing a purchase

By the time code passes the above stages, team can be confident that app won't break in production. All of these run in automation pipelines. When all the tests pass, the build is marked ready for release.

Release:

- Versioning
- Tagging Artifacts
- Pushing them into a release repo (Docker Hub, Nexus)

This ensures the exact same build that was tested will be deployed later on.

Deployment:

- In Devops, deployments are automated and repeatable
- Pipelines handle the process, tools like Kubernetes orchestrate deployments at scale

Operate:

- To ensure system continues to run reliably under real world conditions
- Monitoring Server health
- Applying security patches
- Managing infrastructure configs
- Scaling resources when traffic spikes

Monitoring:

- Gathering data about system's performance
- Uptime, error rates and business metrics (Sentry)

And the cycle continues...

## CI/CD

Coding -> Building -> Testing -> Deployment. It's an automated conveyer belt for software.

CI -> Continuous Integration. Everytime a dev pushes code, tests run automatically and if something breaks, the pipeline stops and we fix it before moving forward.

CD -> Continuous Depployment. Once all the tests are passed, app is automatically deployed to staging or production.

These pipelines are written using tools like github actions, jenkins, etc.

Containers eliminate versioning conflicts by packaging applications along with all their dependencies, ensuring consistency across environments. Most popular tool is Docker.

Container orchestration is the process of managing and running containers at scale. Go to tool here is Kubernetes.

Infrastructure as Code (IaC) is the practice of provisioning and managing infrastructure through code instead of manual processes, with Terraform being one of the most popular tools.

Scripting to automate processes.

A pipeline is a set of automated steps that takes your code from the moment you push it all the way to production.

Tools: Jenkins, GitLab CI/CD, Circle CI, Travis CI, Azure DevOps.
Most devs prefer Github Actions.

Github Actions pipeline is a workflow. Workflows live inside your repo (.github/workflows) Each Workflow is a `.yaml` file (triggers, events and jobs)

Important YAML keywords:

- `name`: Workflow/job title
- `on`: Defines triggers (push, PR, schedule)
- `jobs`: Define jobs, their OS, and steps
- `steps`: Sequential commands or actions
- `run`: Shell commands to exexute
- `uses`: Use prebuilt actions
- `with`: Set environment variables
- `needs`: Make on job depend on another

## Version Control (Git)

Git is a distributed version control system. The version control part helps you track and manage code changes over time. Distributed means every developer's computer has a complete copy of the codebase, including the entire history of changes and information about who changed what and when. It eases our worflow.

A repo is where git tracks everything in your project.

Github is a cloud platform that allows you to store your repositories online and collaborate with others.

```yaml
name: CI Pipeline

on:
  push:
    branches: [main]

jobs:
  build:
    runs-on: ubuntu-latest

    steps:
      - name: Checkout code
        uses: actions/checkout@v5
      - name: Set up Node.jobs
        uses: actions/setup-node@v3
        with:
          node-version: 20
      - name: Install dependecies
        run: npm install
      - name: Run tests
        run: npm test
```

| **Part**                                                          | **Explanation**                                                                 |
| ----------------------------------------------------------------- | ------------------------------------------------------------------------------- |
| `name: CI Pipeline`                                               | The name of the workflow, visible in the GitHub Actions tab.                    |
| `on:` → `push:` → `branches: [main]`                              | Defines the trigger. Runs only when code is pushed to the `main` branch.        |
| `jobs:` → `build:`                                                | A job is a set of steps. Here we define a single job named `build`.             |
| `runs-on: ubuntu-latest`                                          | The virtual machine (runner) environment. Uses the latest Ubuntu Linux image.   |
| `steps:`                                                          | Sequence of tasks the job will run.                                             |
| **Step 1:** `uses: actions/checkout@v5`                           | Checks out your repository’s code into the runner so other steps can access it. |
| **Step 2:** `uses: actions/setup-node@v3` with `node-version: 20` | Installs and configures Node.js (version 20) on the runner.                     |
| **Step 3:** `run: npm install`                                    | Installs project dependencies from `package.json`.                              |
| **Step 4:** `run: npm test`                                       | Executes your project’s test suite.                                             |
