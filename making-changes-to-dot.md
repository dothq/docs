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



