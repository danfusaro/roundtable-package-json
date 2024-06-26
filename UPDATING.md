
## Update dependencies in package.json


Upgrading the `package.json` file for a component library is essential for maintaining the health and functionality of the project. This process ensures that dependencies are up-to-date, security vulnerabilities are patched, and compatibility with newer standards is maintained.

Benefits:

- Access to New Features: Upgrading allows you to leverage the latest features and improvements offered by libraries and frameworks, enhancing the functionality of your components.
- Improved Security: Keeping dependencies updated helps mitigate security risks by applying patches for known vulnerabilities and maintaining a secure codebase.
- Compatibility and Performance: Updates ensure compatibility with newer versions of Node.js and other dependencies, leading to better performance and optimized resource utilization.
- Future-Proofing: Staying up-to-date with package versions ensures that your component library remains relevant and compatible with evolving web development practices and standards.

## Steps

1. Install NPM Check Updates.
   - It’s often best to just install NPM check updates globally. (Alternatively, you can run it with NPX.)
     ```
     npm install -g npm-check-updates
     ```
   - Note: Access the full docs for NPM Check Updates.

2. Run NPM Check Updates.
   - cd to a directory with your project and run the following command.
     ```
     npx ncu
     ```
   - This will return a list of packages that need to be updated. Here’s what it looks like:
     ```
     [====================] 15/15 100%
     
      @notionhq/client   ^0.4.11  →  ^0.4.13
      node-fetch          ^2.6.6  →   ^3.2.0
      gulp-autoprefixer   ^7.0.1  →   ^8.0.0
      gulp-imagemin       ^7.1.0  →   ^8.0.0
      gulp-sass           ^5.0.0  →   ^5.1.0
      gulp-terser         ^2.0.1  →   ^2.1.0
      sass               ^1.35.2  →  ^1.49.7
     ```
   - The existing version is on the left and the latest version is on the right. NPU maintains semantic versioning policies, so you can quickly identify patches, minor updates, or major updates that need fixing.
   - Note: In semantic versioning, the number on the right stands for patches (bug fixes), the number in the middle stands for minor versions (new features added in a backwards compatible manner), and major versions (new features added in a breaking manner). So … MAJOR.MINOR.PATCH.

3. Update Patches.
   - First, I update all patches. Assuming the package maintainers are following semantic versioning, this shouldn’t break anything.
     ```
     npx ncu -u -t patch
     ```
   - Run npm i, ensure everything is still working, and commit the changes (so I can revert if necessary).

4. Update Minor Versions.
   - Next, I update all minor updates. Again, assuming the package maintainers are following semantic versioning, this shouldn’t break anything.
     ```
     npx ncu -u -t minor
     ```
   - Run npm i, ensure everything is still working, and commit the changes (so I can revert if necessary).

5. Update Major Versions.
   - Finally, I update all major updates. Before you update these, you should read the release note docs to see how the new version will affect your project. Once you know how the updates will affect your code, update each major change in a separate commit.
   - With NCU, you can filter for a specific package by using the --filter or -f flag. So in this case, let’s say I’m starting with node-fetch. I’d type the following command:
     ```
     npx ncu -u -f node-fetch
     ```
   - Run npm i, ensure everything is still working, and commit the changes (so I can revert if necessary).
   - Then proceed to the next package to the next major version.

References: 
- https://chrispennington.blog/blog/how-to-update-npm-packages-safely-with-npm-check-updates/
- https://www.youtube.com/watch?v=0XQXGx3lLaU
