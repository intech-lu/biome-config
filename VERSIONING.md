# InTech Biome Rules - Versioning

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
