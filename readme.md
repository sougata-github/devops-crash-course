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
- System continues to run reliably under real world conditions
- Monitoring Server health
- Applying security patches
- Managing infrastructure configs
- Scaling resources when traffic spikes

Monitoring
- Gathering data about system's performance
- Uptime, error rates and business metrics (Sentry)

And the cycle continues...






