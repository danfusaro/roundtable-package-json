### Managing package.json Presentation (April 3, 2024)

The `package.json` file is a settings file used by NPM or Yarn that defines your project's configuration. It contains various sections and properties that govern how your project is structured, built, and executed.

#### Name and Version
- **"name"**: Name of the package.
- **"version"**: Current version of the package.
  - Major 1.x.x
  - Minor x.1.x
  - Patch x.x.1

#### Main Entry Point
- **"main"**: Main entry point file for CommonJS modules.
  - Appropriate when authoring a library or utility that is used in CJS, can be both

#### Module Entry Point
- **"module"**: Entry point for ECMAScript modules (ESM).
  - Same as above but with modules

#### Scripts
- **"scripts"**: Custom scripts for tasks like building, testing, and running the package.
  - These run as if being run from the command line but with access to anything that is installed and available in `node_modules`

#### Dependencies
- **"dependencies"**: Production dependencies required for the package to function in a live environment.
- **"devDependencies"**: Dependencies needed only for development and testing purposes, not for the functioning of the production application.

#### Environment Configurations
- **"engines"**: Specifies the required Node.js version, can use strict, or a range.
- **"browserslist"**: Configuration for supported browsers (for frontend packages).
  - This list can get pretty specific and there are rules in place, for example
```
0.2%: All browsers that have at least 0,2% of global market share
not dead: Exclude browsers without official support in the last 24 months
not ie <= 11: Exclude IE 11 and older versions
not op_mini all: Exclude Opera Mini
``` 
  - To check which browsers are supported against your `package.json` config, use `browserslist` (see script)

#### Git Repository
- **"repository"**: Git repository URL and type, also supports svn and hg/mercurial.

#### License
- **"license"**: Specifies the license type.

#### Additional Metadata
- **"description"**: Brief description of the package.
- **"keywords"**: Keywords to describe the package.
- **"author"**: Name of the package author.
- **"contributors"**: List of contributors.
- **"homepage"**: URL of the package's homepage.
- **"bugs"**: URL or email for issue reporting.
- **"publishConfig"**: Configuration for publishing the package to a registry.

#### Others
- **"private"**: Indicates if the package should not be published publicly.
- **"scripts"**: Custom scripts for tasks like building, testing, and running the package.
- **"files"**: List of files to include in the package when publishing.
- **"peerDependencies"**: Dependencies that must be installed by the consumer of the package.
- **"optionalDependencies"**: Dependencies that are not required for the package to function.

### Exercise
1. Run `npm install`
2. Check for vulnerabilities with `npm audit --audit-level=critical`
3. Use `npx npm-check-updates -u` to update package versions
4. Rerun `npm install` to update packages
5. Investigate high vulnerabilities and isolate packages requiring `npm audit fix --force`
6. Test against these packages to ensure compatibility and address breaking changes.
