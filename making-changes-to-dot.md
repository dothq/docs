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

## Creating manual patches for more advanced operations

You are not able to create a patch file for files that did not exist in the `src` directory to begin with.

An example of this is creating a new file or directory in `src` that didn't exist before. We can, however, use manual patches for this kind of thing.

If you open up `build/manual-patches.ts` in your code editor of choice you should see something like this:

```typescript
import { IPatch } from "./interfaces/patch";

const manualPatches: IPatch[] = [
    {
        name: "branding", // name of the manual patch
        action: "copy", // what action we want to do
        src: "browser/branding/dot" // this will copy common/browser/branding/dot to src/browser/branding/dot
    },
    {
        name: "dotui",
        action: "copy",
        src: [
            "browser/themes/shared/dotui",
            "browser/themes/windows/dotui",
            "browser/themes/osx/dotui",
            "browser/themes/linux/dotui"
        ]
    },
    ...
];

export default manualPatches;
```

These are all manual patches that are being applied to the source code. If we take a look at the first manual patch we can see it is copying `common/browser/branding/dot` to `src/browser/branding/dot`. This is where the common directory comes in.

If we created a file in the `common` directory at the path `browser/testing.txt` and made a manual patch for this:

```typescript
{
    name: "my new manual patch",
    action: "copy",
    src: "browser/testing.txt"
},
```

And then we ran `./melon rebuild` to rebuild the manual patches structure.

And then `./melon import` to import our patch files and our manual patches, you should see your `my new manual patch` appearing in the logs.

If you then went to `src/browser` in your file explorer, you should see `testing.txt` has been copied from `common/browser/testing.txt` to `src/browser/testing.txt`!

Now what happens if you want to edit `src/browser/testing.txt`? Would you have to update `common/browser/testing.txt` too? Nope!

When you edit `src/browser/testing.txt` if you run `./melon export` it will automatically export the manual patches too and it copies your changes in `src/browser/testing.txt` to `common/browser/testing.txt` so everything is up to date.

And that is how manual patches work!

