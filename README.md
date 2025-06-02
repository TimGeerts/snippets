# Contributing to Ignite

First off, thanks for taking the time to contribute! ❤️

The following is a set of guidelines and information for contributing to Ignite and its libraries which are hosted in the [ignite repository](https://sdworx.visualstudio.com/CoE%20UX/_git/ignite) on Azure Devops.

> Should you not have access to this repository, feel free to reach out to [Tim Geerts](mailto:tim.geerts@sdworx.com) and he'll try to get it sorted asap.

All types of contributions are encouraged and valued. See the [Table of contents](#table-of-contents) for different ways to help and details about how this project handles them. Please make sure to read the relevant section before making your contribution. It will make it a lot easier for us maintainers and smooth out the experience for all involved. The community looks forward to your contributions.

## Table of contents

[What should I know before I get started?](#what-should-i-know-before-i-get-started)

- [Monorepository](#monorepository)
- [Directory structure](#directory-structure)

[How can I contribute?](#how-can-i-contribute)

- [Reporting bugs](#reporting-bugs)
- [Suggesting enhancements](#suggesting-enhancements)
- [Submitting pull requests](#submitting-pull-requests)
  - [Clone the repository](#clone-the-repository)
  - [Create a branch](#create-a-branch)
  - [Pull Request and code guidelines](#pull-request-and-code-guidelines)
  - [Commit message guidelines](#commit-message-guidelines)
  - [Pull Request approval](#pull-request-approval)

[Tools](#tools)

- [Ignite component generator](#ignite-component-generator)

## What should I know before I get started?

### Monorepository

The code repository for the Ignite project is based on [the monorepo principle](https://www.animaapp.com/blog/code/what-is-a-monorepo-a-practical-guide-for-developers/), utilizing [Nx](https://nx.dev/) as its open-source build system.  
A monorepo &mdash; short for “monolithic repository” &mdash; is a single repository that houses the code for multiple projects within an organization. Unlike a multi-repo approach, where each project has its own repository, a monorepo keeps everything in one place.  
This setup makes it easier to share code, manage dependencies, and maintain consistency across projects.

#### Benefits of a monorepo

- **Single repository**: All projects are stored together in a single version-controlled repository.
- **Shared code and dependencies**: Easily share code and dependencies between projects.
- **Unified versioning**: Everything is versioned together, meaning each “snapshot” of the codebase is consistent.
- **Consistent build and deployment pipelines**: Centralized tooling makes it easier to standardize how code gets built and deployed.

### Directory structure

Nx structures the code into two main directories, `apps` and `libs` that can be used to house several different applications (in the apps directory) and shareable libraries (in the libs) directory.

#### Ignite applications (`apps/`)

- `ignite-color-scheme`  
  An internal application used by our designers to play around with different colourschemes and define palettes that comply with the SD Worx brand.

- `ignite-docs`  
  The main documentation application that documents all of our assets, styling and components.

#### Ignite libraries (`libs/`)

- `ignite-docs` (_internal_)  
  Contains all the shared libraries/features that are used in our documentation application (`apps/ignite-docs`). It mainly consists of different feature libraries and shared components that are used as building blocks for our documentation application.

- `ignite-styling` (_published_)  
  Contains all the styling rules (`.scss`) for the Ignite design system. You'll find utility classes, base styles, different layouts and styles for each Ignite component in this library.  
  _A more in depth breakdown on how this library is structured and how it all bundles together can be found [here](./libs/ignite-styling/README.md)._
- `ignite-tokens` (_internal_)  
  Contains the configuration of all design tokens used in the design system. These tokens are created and maintained by our designers in a tool called [Tokens Studio](https://tokens.studio/) and are exported as json files into this library so they can be transformed and be used as css variables in our styling library.
- `ignite-visuals` (_published_)  
  Contains all the visual assets (empty states, logos, favicons, icon fonts, ...) for the Ignite design system.  
  _A more in depth breakdown on how this library is structured and how it all bundles together can be found [here](./libs/ignite-visuals/README.md)._
- `ng-ignite` (_published_)  
  Contains all the Angular components that the Ignite design system provides.  
   _A more in depth breakdown on how this library is structured and built can be found [here](./libs/ng-ignite/README.md)._

## How can I contribute?

### Reporting bugs

A great way to contribute to the project is to send a detailed issue when you encounter a problem. We always appreciate a well-written, thorough bug report.

> [TODO] This section will be finalized when we have decided on a tool/ui to make it easier to report bugs.

### Suggesting enhancements

Feature requests are welcome! However, while we will consider all requests, we cannot guarantee your request will be accepted.  
As a design system with components that are used throughout several different fields of applications, we have to make sure that features don't become to specialized and become unusable by the majority of our users.  
Your idea may be great, but it might be out-of-scope for the project.  
If accepted, we cannot make any commitments regarding the timeline for implementation and release. However, you are welcome to submit a pull request to help!

> [TODO] This section will be finalized when we have decided on a tool/ui to make it easier to suggest enhancements.

### Submitting pull requests

> This section assumes that you have a working IDE and GIT configuration.  
> (_all examples here will use VS Code_)

If you want to contribute actual code in stead of reporting a bug or suggesting an enhancement, there's a few steps you'll have to do first.

#### Clone the repository

Go to the [ignite repository](https://sdworx.visualstudio.com/CoE%20UX/_git/ignite) on Azure Devops and press the `Clone` button in the top right corner.  
Here you can choose to clone the repository to your local machine by either using the command line _(copy the path from the popup you get by pressing the Clone button)_ or using the `Clone in VS Code` button.

```bash
git clone <path to the repository>
```

If everything goes well, you should now have all the folders locally on your machine and after running `npm install` in the home directory, everything should be ready to go.

```bash
npm install
```

> **Optional global installs**  
> It's useful to have `nx` installed globally since many of the commands used throughout the repository use the Nx CLI instead of the Angular one (ng)  
> `npm i -g nx`

You can test your cloned repository by running `npm start` which builds and starts the `ignite-docs` application.

```bash
npm start
```

#### Create a branch

Working directly in the main or develop branch isn't allowed, or rather, there are policies in place that force the use of pull requests to contribute code. So please make a custom branch for your code that you can pull request into the develop branch when it's finished.

> We don't really enforce a specific naming convention, but some simple common sense semantics go a long way.  
> Use `feature/...` to indicate the branch is a new feature, or an addition to an existing feature.  
> Use `fix/...` if your branch will be used for a bugfix.  
> Use `chore/...` or `refactor/...` or whatever word makes semantic sense for anything that isn't a feature or a bugfix.
>
> Examples:
>
> - `feature/accordion-component` (indicates a new feature, the accordion component)
> - `feature/avatar-image-variant` (clearly says it's a feature that will add a variant to the avatar component)
> - `fix/button-primary-hover-state` (shows that it's a fix for a bug on the primary button's hover state)
> - `chore/ng-42-upgrade` (a branch used to upgrade the Angular version to version 42)

#### Pull Request and code guidelines

- **Smaller is better**  
  Submit one pull request per bug fix or feature. A pull request should contain isolated changes pertaining to a single bug fix or feature implementation. Do not refactor or reformat code that is unrelated to your change. It is better to submit many small pull requests rather than a single large one. Enormous pull requests will take enormous amounts of time to review, or may be rejected altogether.

- **Coordinate bigger changes**  
  For large and non-trivial changes, open an issue to discuss a strategy with the maintainers. Otherwise, you risk doing a lot of work for nothing!

- **Prioritize understanding over cleverness**  
  Write code clearly and concisely. Remember that source code usually gets written once and read often. Ensure the code is clear to the reader. The purpose and logic should be obvious to a reasonably skilled developer, otherwise you should add a comment that explains it.

- **Follow existing coding style and conventions**  
  Keep your code consistent with the style, formatting, and conventions in the rest of the code base. When possible, these will be enforced with a linter, but it's often a good idea to just check already existing code to see how we generally structure our source. This consistency makes it easier to understand for everyone as well as making it easier to review and modify in the future.

- **Add documentation**  
  If your pull request requires documentation (added a new component, added a new variant, ...), make sure you add documentation to our `ignite-docs` application as well as providing meaningful code comments where needed.  
  When you are making any changes to existing Angular components, or adding new Angular components, you can also provide updates to our Storybook code (though this is not required and we will can handle that part ourselves if needed).

- **Update the CHANGELOG**  
  For all enhancements and bug fixes, you should add meaningful (concise) entries in the respective `CHANGELOG.md` files (newest entries at the top of the file).  
  There's no need to be specific on version numbers in these files, just use `vNext` as a placeholder and make sure there's a record in there detailing (again, concise) the changes you've made to that library with your pull request.  
  The changelog files will be cleaned up and corrected to an actual version number once we merge `develop` to `main` to get ready for a release.

  _For example:_

  ```markdown
  ## vNext::26/04/2025

  - add pink variant for the button component
  ```

#### Commit message guidelines

[How to write good commit messages](https://cbea.ms/git-commit/)

> [TODO] This section will be finalized when we have implemented commitizen and can provide better info on this subject.

#### Pull Request approval

Every pull request requires approval, this will usually be done by a UX Central team member, but every contributor is free to leave comments on any pull request.

> When reviewing pull requests remember that you are reviewing the code, not the author.  
>  Always provide actionable feedback and explain your reasoning.

> When reading reviews on your pull requests remember that you are not your code!  
> If your code is critiqued, questioned, or constructively criticized, do not take code review personally.

## Tools

### Ignite component generator

Creating a new component requires a fair amount of code changes:

- Create styling files for the component
- Create a documentation page for the html/css version of the component
- Create an angular component
- Create documentation for the angular component (Storybook)

To make this creation easier, we provide a specific generator in the ignite repository that scaffolds all of these files for you.

_Execute the following command to start creating a new component:_

```bash
nx generate @sdworx/ignite-workspace:ig-component
```

_The generator will ask for a componentname:_  
![ignite-component-generator-name](https://placehold.co/600x50)

> Provide this name in PascalCase as it will be used to generate the names of several Angular components.  
> For example: `MySpecialLittleButton` or `SuperSideNavigationItem`

_And then it will ask you which files you want to generate:_  
![ignite-component-generator-files](https://placehold.co/600x50)

> Usually you'll just want to select 'All files' when creating a new component, the other options exist just in case they're ever needed to fix something.

_After it's finished, the following files will have been created:_  
![ignite-component-generator-result](https://placehold.co/600x250)

> All of the files will already contain some basic code following our best practices and guidelines.  
> The component is obviously not ready, but you should no longer have to worry about "connecting all the dots" in the repository and can focus solely on creating and documenting the actual component.
