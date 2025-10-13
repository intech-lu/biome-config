# InTech Biome Rules Changelog

## Versioning

InTech Biome Rules follows the [Semantic Versioning](https://semver.org/) standard. Due to the nature of this project as a ruleset, it can be unclear what changes are considered major, minor or patch. That's why we have a few guidelines to help you understand the versioning of this project:

### Patch Release

- Changes to the configuration that won't affect the user's configuration
- Changing the options of a rule
- Improvements of the documentation
- Re-releases after a failed release
- Biome patch version update

### Minor Release

- Adding a new rule to the ruleset
- Changing the behavior of a rule
- Removing a rule from the ruleset
- Adding linting and formatting support for a recently introduced language feature by Biome
- Changes to the configuration that result in the user having to update their configuration on their projects
- Biome minor version update

### Major Release

- Biome major version update

## v1.0.1 (2025-10-13)

### Dependencies

- Bump Biome.js version (`@biomejs/biome`) from `2.1.3` to `2.2.5`. See the [Biome.js 2.2.5 release](https://github.com/biomejs/biome/releases/tag/%40biomejs%2Fbiome%402.2.5) and [Biome.js 2.2.0 release](https://github.com/biomejs/biome/releases/tag/%40biomejs%2Fbiome%402.2.0) for more information.

### Configuration

#### New features

- Add new rules introduced in Biome `2.2.0` (except for the GraphQL, Solid and Next.js ones). See [Biome.js 2.2.0 release](https://github.com/biomejs/biome/releases/tag/%40biomejs%2Fbiome%402.2.0) for more information

### Documentation

#### New features

- Add a `CHANGELOG.md` file to keep track of the changes in the project.

## v1.0.0 (2025-10-11)

### Configuration

#### New features

- Create a **vanilla** Biome configuration that covers the most common rules for a project.
- Create a **JSX** Biome configuration that replicates the **vanilla** configuration and covers additional rules for a project using JSX, such as accessibility.
- Create a **React** Biome configuration that replicates the **JSX** configuration and covers additional rules specific to React projects.

### Documentation

#### New features

- Add a `README.md` file with a description of the project and how to use it.
