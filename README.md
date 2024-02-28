# (new) Project.mgmt

project.mgmt is a simplified project manager aimed at project and task management for single users. You can add your clients, projects, and tasks easily. It offers easy project and task tracking via a sleek widget interface. This is a reboot based upon the [original project](https://github.com/tverderesi/project-mgmt-app).

## Why Reboot the Project?

The first version was developed as a tutorial to better understand the MERN+GraphQL stack. It was actually the first project I have developed in that stack, using the monorepo approach. It had no project management whatsoever. The back-end has gone through three refactorings. The front-end had even more refactorings, five. I got lost in it. The project was a mess. So I had decided to start with a clean slate, using feature planning and issue tracking from the get go, this way I'll be able to complete the project without losing my sanity.

## Project Structure

### Current

The current repository uses [turborepo](https://turbo.build/) as its build system. The project is divided into two apps:

- **Back-end:** The back-end for the project. It was built using express, mongoose, and Apollo Server. It contains entity modeling, the GraphQL schema and resolvers, the server definitions, configuration, routing, authentication, and validation.
- **Front-end:** The front-end for the project. It contains the GraphQL client (Relay) and the user interface (shadcn/ui) for the app and the landing page.

### Proposed

Since the [Current Structure](#current) condenses too much logic into each app, the idea is to break those into packages, ensuring re-usability and maintainability. If this proposition works, the made packages can be further developed into npm packages that can be imported and reused into current and future projects. Testing will be implemented in each package and app. The proposed Structure will be as it follows:

#### Packages

##### From front-end app:

- **ui**: It will contain shadcnui, as well the component extensions I've built, along with react-hook-form and tanstack/table.

##### From back-end app:

- **authentication**: It will contain the authentication logic and handling, using passport.
- **graphql**: It will contain the schema, since it is needed both on front and back-end. The resolvers will remain in the **back-end** package.
- **validation:** Since the idea is to use zod for validation, the validation objects can be extracted to their own package.
- **logging**: extract logger configuration.

#### Apps

- **front-end**: It will contain the app and the landing page.
- **back-end**: It will contain the server.
- **database**: It will contain a dockerfile to build the database.

### Repo Management

The repository will contain a [Task List](https://github.com/tverderesi/mgmt-dot-app-new/issues/1) which will track the development of each feature and bug that may arise. The respository will have n+1 branches, where n is the number of features being currently developed. Once a feature is successfully developed and tested, it will be merged into the main brach. Each package and app will have their own tag in GitHub, and each issue shall be categorized according to its type (feature/bug/issue/etc) and the packages/apps it will affect.

### Project Phases:

1. **Revision**

   - Redefine MVP.
   - Redraw entities.
   - Replan features and check the progress in the old project.
   - Recategorize features according to their proposed structure.
   - Plan the implementation of incomplete features.
   - Plan the implementation of new features.

2. **Scaffolding**
   - Init each package.
   - Decide testing, linting and building rules.
3. **Transferring**

   - Port over each existing feature into its respective package app.
   - Write tests for each feature.

4. **Coding**

   - Code and test incomplete features.
   - Code and test new features.

5. Deployment
   - Ensure correct deployment for the proposed structure.
   - Find beta testers.
6. Release
   - Release MVP.

### Proposed Iteration Cycle for Feature Development

1. Open an issue with the tag `feature` and the affected packages and apps.
2. Create a branch related to the `feature`.
3. Code and test the feature.
4. Open a PR to integrate the feature.

### Proposed Iteration Cycle for Bug Correction

1. Report bug using `bug` and which package, app, or feature it is related to.
2. Evaluate bug criticality.
3. If the bug is critical, open a `hotfix` branch to solve it ASAP.
4. If the bug is non-critical, evalute position into development cycle.
5. Code and test a solution.
6. Open a PR to integrate the bugfix.
7. Once the PR is approved, report into the bug issue what caused it and how it was fixed.

### Contributing

Feel free to contribute to the project by opening an issue.
