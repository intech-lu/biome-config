# InTech Biome Rules

Welcome to the **InTech Biome Rules** repository, your go-to solution for managing and applying consistent code quality and formatting standards across all projects at InTech. This repository hosts a custom **Biome.js** configuration designed to enforce a **unified coding style**, adhere to **coding best practices**, and ensure **accessibility compliance**. By using Biome, we streamline code formatting and maintainability while reducing code quality discrepancies in collaborative projects. This comprehensive toolset helps foster a more efficient and cohesive development environment for all team members.

## 🗂️ Table of Contents

- [⚙️ Installation](#⚙️-installation)
  - [📋 Requirements](#📋-requirements)
  - [1️⃣ Step 1: install the Biome extension for VSCode](#️1️⃣-step-1-install-the-biome-extension-for-vscode)
  - [2️⃣ Step 2: apply fix and format on save with VSCode](#️2️⃣-step-2-apply-fix-and-format-on-save-with-vscode)
  - [3️⃣ Step 3: install InTech Biome Rules](#️3️⃣-step-3-install-intech-biome-rules)
  - [4️⃣ Step 4: create your Biome configuration file](#️4️⃣-step-4-create-your-biome-configuration-file)
  - [5️⃣ Step 5: enjoy 🎉](#️5️⃣-step-5-enjoy-)
- [🔧 Customizing and Managing Your Biome Configuration](#🔧-customizing-and-managing-your-biome-configuration)
  - [🚫 Ignoring Files and Directories](#🚫-ignoring-files-and-directories)
  - [🛠️ Overriding Specific Settings](#🛠️-overriding-specific-settings)
    - [Override Rules Globally](#override-rules-globally)
    - [Override Rules for Specific Files or Directories](#override-rules-for-specific-files-or-directories)
  - [🔄 Version Control System (VCS) Integration with Git](#🔄-version-control-system-vcs-integration-with-git)
- [🛠️ Troubleshooting](#🛠️-troubleshooting)

## ⚙️ Installation

### 📋 Requirements

- **Node.js**: >= `14.21.3` (Fermium)
- npm: make sure you have npm installed

### 1️⃣ Step 1: install the Biome extension for VSCode

- <https://marketplace.visualstudio.com/items?itemName=biomejs.biome>

### 2️⃣ Step 2: apply fix and format on save with VSCode

Create a `.vscode/settings.json` file at the root of your project and add the following configuration:

```json
{
  // Formatting
  "editor.formatOnSave": true,
  "editor.defaultFormatter": "biomejs.biome",

  // Linting
  "editor.codeActionsOnSave": {
    "source.action.useSortedAttributes.biome": "explicit", // Only for JSX files
    "source.action.useSortedKeys.biome": "explicit",
    "source.fixAll.biome": "explicit",
    "source.organizeImports.biome": "explicit"
  }
}
```

**Explanation:**

- `editor.formatOnSave`: Automatically formats the code when saving the file.
- `editor.defaultFormatter`: Sets the default formatter to Biome (the extension you installed in step 1).
- `editor.codeActionsOnSave`: Specifies the actions to take when saving the file.
  - `source.action.useSortedAttributes.biome`: Automatically sorts JSX attributes when saving the file.
  - `source.action.useSortedKeys.biome`: Automatically sorts object keys when saving the file.
  - `source.fixAll.biome`: Automatically fixes linting errors when saving the file.
  - `source.organizeImports.biome`: Automatically organizes imports when saving the file.

### 3️⃣ Step 3: install InTech Biome Rules

Install the InTech Biome Rules package by running the following command in your project's root directory:

```bash
npm install -D @intech.lu/biome-config
```

*Note: you don't have to install the official Biome package, as it is already shipped with the InTech Biome Rules package.*

### 4️⃣ Step 4: create your Biome configuration file

Depending on the technology stack you are using in your project, choose the appropriate Biome configuration. This ensures that the code quality and style rules are tailored to your specific needs.

#### Available configurations

1. **Vanilla JavaScript/TypeScript:**

    Use this configuration for standard JavaScript/TypeScript projects or those not covered by other specific configurations.

    ```jsonc
    {
      "$schema": "node_modules/@biomejs/biome/configuration_schema.json",
      "extends": [
        "@intech.lu/biome-config/vanilla"
      ]
    }
    ```

2. **JSX (Non-React) Projects:**

    For projects that use JSX syntax but are not based on React, use the following configuration:

    ```jsonc
    {
      "$schema": "node_modules/@biomejs/biome/configuration_schema.json",
      "extends": [
        "@intech.lu/biome-config/jsx"
      ]
    }
    ```

3. **React Projects:**

    If you are working on a React project, use the React configuration:

    ```jsonc
    {
      "$schema": "node_modules/@biomejs/biome/configuration_schema.json",
      "extends": [
        "@intech.lu/biome-config/react"
      ]
    }
    ```

#### How to Set Up

1. **Create a `biome.jsonc` File:**

    At the root of your project, create a `biome.jsonc` file if one does not already exist.

2. **Select the Appropriate Configuration:**

    Copy and paste the JSON configuration that matches your project's technology stack from the options above.

3. **Save the File:**

    Make sure to save the `biome.jsonc` file after inserting the correct configuration. You'll maybe need to restart your editor to apply the changes.

### 5️⃣ Step 5: enjoy 🎉

You're all set! Your project is now configured to use the InTech Biome Rules. You can now start coding with confidence, knowing that your code is automatically formatted and linted according to the InTech coding standards.

## 🔧 Customizing and Managing Your Biome Configuration

While the InTech Biome Rules provide a robust default configuration for maintaining consistent code quality, there might be scenarios where your project requires custom adjustments. This section will guide you on how to customize and manage your Biome configuration effectively.

### 🚫 Ignoring Files and Directories

In some cases, you may want to exclude certain files or directories from being processed by Biome. This is particularly useful for files that are automatically generated, third-party libraries, or files that don’t need linting and formatting.

By default, Biome always ignores some files that are said to be **protected files**. This means that no diagnostics will be ever emitted by Biome for those files. At the moment, the following files are protected:

- `composer.lock`
- `npm-shrinkwrap.json`
- `package-lock.json`
- `yarn.lock`

To ignore additional files or directories, you can specify them in the `includes` field of your `biome.jsonc` configuration file by negating the patterns with `!`. Here’s an example:

```jsonc
{
  "$schema": "node_modules/@biomejs/biome/configuration_schema.json",
  "extends": [
    "@intech.lu/biome-config/vanilla"
  ],
  "files": {
    "includes": [
      "!dist/**", // Ignore all files in the dist directory
      "!node_modules/**", // Ignore all files in the node_modules directory
      "!package.json" // Ignore the package.json file
    ]
  }
}
```

### 🛠️ Overriding Specific Settings

Sometimes, certain files or directories in your project require different linting or formatting rules. Biome allows you to define overrides to accommodate these needs.

Note that Biome rules are divided into groups, such as *accessibility*, *complexity*, *correctness*, etc., so you may need to check which group a specific rule belongs to by referring to the [Biome documentation](https://biomejs.dev/linter/rules/).

#### Override Rules Globally

To globally override rules for your entire project, modify the `rules` section of the `linter` object in your `biome.jsonc` configuration file. Here’s how you can change or disable specific rules:

```jsonc
{
  "$schema": "node_modules/@biomejs/biome/configuration_schema.json",
  "extends": [
    "@intech.lu/biome-config/vanilla"
  ],
  "linter": {
    "rules": {
      "complexity": {
        "noForEach": "warn" // Change the noForEach rule to a warning globally
      },
      "suspicious": {
        "noConsoleLog": "off" // Disable the noConsole rule globally
      }
    }
  }
}
```

#### Override Rules for Specific Files or Directories

You can also apply rule overrides only to specific files or directories by using the `overrides` field. You can chose to include or ignore specific files using glob patterns.
This is useful when certain parts of your project, such as test files or configuration scripts, require different rule settings.

- **Define Overrides for Specific Files**

Specify file patterns and their corresponding rules. For example, if you want to allow console statements in test files but not in production code:

```jsonc
{
  "$schema": "node_modules/@biomejs/biome/configuration_schema.json",
  "extends": [
    "@intech.lu/biome-config/vanilla"
  ],
  "overrides": [
    {
      "includes": ["**/*.test.{js,ts}", "**/*.spec.{js,ts}"],
      "linter": {
        "rules": {
          "suspicious": {
            "noConsoleLog": "off" // Disable the noConsole rule for test files
          }
        }
      }
    }
  ]
}
```

- **Define Overrides for Specific Directories**

If you need different formatting settings for certain directories, such as using tabs instead of spaces in configuration files:

```jsonc
{
  "$schema": "node_modules/@biomejs/biome/configuration_schema.json",
  "extends": [
    "@intech.lu/biome-config/vanilla"
  ],
  "overrides": [
    {
      "includes": ["config/**/*.{js,ts}"],
      "formatter": {
        "indentStyle": "tab" // Use tabs for indentation in the config directory
      }
    }
  ]
}
```

### 🔄 Version Control System (VCS) Integration with Git

Integrating Biome with Git helps ensure consistent code quality and formatting across your project by leveraging your existing `.gitignore` file and setting up Git Hooks for automated checks.

#### Using `.gitignore` for File Exclusion

The InTech Biome configuration respects the patterns defined in your `.gitignore` file. This means any files or directories you specify there will automatically be excluded from Biome processing. This integration ensures that generated files, third-party libraries, and other non-essential files are not unnecessarily linted or formatted.

#### Setting Up Git Hooks

For additional automation, such as running Biome formatting and linting on staged files before committing or pushing, you can set up Git Hooks. For detailed instructions on configuring these hooks with Biome, please refer to the [Biome Git Hooks Documentation](https://biomejs.dev/recipes/git-hooks/).

## 🛠️ Troubleshooting

If you encounter issues while using the InTech Biome Rules, this section provides solutions to common problems and helpful tips to ensure a smooth experience.

### Common Issues and Solutions

**Q: I'm using a framework like Angular or NestJS that utilizes decorators and/or the `experimentalDecorators` option in `tsconfig.json`, but it seems Biome is not able to lint or format file with decorators. What should I do?**

**A:** As its name suggests, the `experimentalDecorators` option in TypeScript is still an experimental/unsafe feature and may change over time. As stated in the [Biome documentation](https://biomejs.dev/linter/rules/use-import-type/#caveat-with-typescript-experimental-decorators), since Biome doesn't know how a decorator is implemented, is is unable to check files that use such decorators. To work around this issue, you can turn the `unsafeParameterDecoratorsEnabled` option on within the Biome javascript parser and disable the `useImportType` rule. Here's how you can do it in your `biome.jsonc` configuration file:

```jsonc
{
  "$schema": "node_modules/@biomejs/biome/configuration_schema.json",
  "extends": [
    "@intech.lu/biome-config/vanilla"
  ],
  "javascript": {
    "parser": {
      "unsafeParameterDecoratorsEnabled": true
    },
  },
  "linter": {
    "rules": {
      "style": {
        "useImportType": "off"
      }
    }
  }
}
```
