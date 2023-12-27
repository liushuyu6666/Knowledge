- [Overview](#overview)
- [benefits](#benefits)
- [canary](#canary)
  - [overview](#overview-1)


# Overview
CI/CD automates the process of building, testing, and deploying software. Continuous Integration ensures code changes work well together, and Continuous Delivery automates their release to staging. Continuous Deployment takes it a step further by automating deployment to production, making the release process faster, consistent, and reliable.

1. Continuous Integration (CI)
  - Developers regularly merge their code changes into main or development branch.
  - Automated builds are triggered to compile the code and perform basic tests whenever changes are integrated.
  - The goal is to catch integration issues early and ensure that the codebase is always in a consistent and functional state.
2. Continuous Delivery (CD)
   - Once code changes pass the CI process, they are automatically prepared for deployment.
   - Continuous Delivery involves automating the deployment of code changes to a staging or pre-production environment.
   - The code is ready for release at any time, providing a streamlined and reliable process for delivering software updates.
3. Continuous Deployment (CD - an extension of CD)
   - In Continuous Deployment, the final step is automated deployment to the production environment.
   - Code changes that pass all tests are automatically and immediately deployed to production without manual intervention.

# benefits
- Speed: CI/CD automates repetitive tasks, reducing manual effort and speeding up the development and release cycles.
- Quality: Automated testing ensures that code changes are thoroughly tested before reaching production, reducing the risk of bugs.
- Consistency: CI/CD promotes a consistent and reliable process for building, testing, and deploying software.

# canary
## overview
1. Initial Deployment
   - A small percentage of users or servers (the "canary group") receive the new version of the software while the majority continue to use the current version.
2. Monitoring
   - The performance, reliability, and user experience of the canary release are closely monitored in real-time.
   - Various metrics and monitoring tools are used to detect any issues, such as increased error rates or performance degradation.
3. Gradual Expansion or Rollback
   - If the canary release performs well without issues, the deployment is gradually expanded to a larger user base or server pool.
   - If problems are detected, the deployment can be quickly rolled back, preventing widespread impact.
4. Full Deployment or Rollback
   - Once the canary release is deemed successful after careful monitoring, it is deployed to the entire user base.
   - If issues are detected, the deployment can be rolled back to the previous version to minimize the impact on users.