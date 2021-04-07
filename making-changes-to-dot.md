---
description: >-
  Adding features or changing things in the Dot Browser source code can be quite
  complex at first, so this doc should make it easier to understand.
---

# 📝 Making changes to Dot

## Introduction

We will assume you have cloned the source code and imported the patches already. If you haven't please read [🏗 Building Dot Browser](cloning-dot/).

## Understanding the file structure

| Directory | Purpose |
| :--- | :--- |
| src | The src directory is where you should be editing files and making changes. |
| common | The common directory is used for importing files manually. Using the common directory makes more sense for copying new directories and files as you are not able to export a patch for a file that didn't exist to begin with.  |
| patches | The patches directory is where all the .patch files are dumped after you run `./melon export` |
| build | The build directory is where the code for the melon build tool is. It also includes the manual-patches.ts file which is where you declare the manual patches in the common directory. |
| configs | The configs directory contains all the build configs for each build target. You shouldn't need to worry about this directory. |

## Exporting patches for files that have been modified

If you have edited an existing file in the `src` directory you will need to export your file to the `patches` directory so it is available for everyone else as the `src` directory is never committed to source control.

To export the modified file as a patch file, run the following command:

```bash
./melon export

# or if you want to export an individual file
./melon export-file <file>
```

You will notice that the files you changed in the `src` directory will now have their own patch files in the `patches` directory. 

For example, if you edited `src/browser/app/profile/firefox.js` it would create a file in the `patches` directory called `browser-app-profile-firefox-js.patch`. 

You would then commit that patch file, either to your fork to open a PR or directly to the source code if you have the correct permissions.

You are now all done, your modifications to the source code have been saved! ✨

