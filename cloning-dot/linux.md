---
description: This is a step by step guide on how to build Dot Browser on Linux.
---

# 🐧 Linux

## First things first...

* Minimum requirements:

  * 8GB of RAM
  * 4 physical CPU cores
  * 20GB of disk space free

* Recommended requirements:

  * 16GB of RAM
  * 8 physical CPU cores
  * 35GB of disk space free

* You'll need to be on a 64-bit operating system to clone and build Dot Browser.

  * If typing `uname -m` into a terminal returns `x86_64` you are on a 64-bit computer.

* The following software and tools are required for the build process:
  * Git \([git-scm.org](https://git-scm.org)\)
  * NodeJS \([nodejs.org](https://nodejs.org)\)
  * yarn \([npmjs.com/package/yarn](https://www.npmjs.com/package/yarn)\)
  * Docker

{% hint style="info" %}
Dot Browser is based on Firefox, which is why it is referenced a lot in the build process.
{% endhint %}

## Clone the repository

We're now going to clone Dot Browser.

```text
git clone https://github.com/dothq/browser-ff
```

Or if you prefer using GitLab:

```text
git clone https://gitlab.com/dothq/browser-ff
```

After the clone is complete, you'll want to enter the `browser-ff` directory.

### Downloading the source code and mounting

Now run `./melon download` This will download the source code.

{% hint style="info" %}
`melon` is a build toolkit for Dot Browser.
{% endhint %}

## Importing the patches

Once you've downloaded the source code, you're going to want to import the patches. You can do this by running the command below.

```bash
./melon import
```

If everything went smoothly with the import, you should see a "success" message.

## Building Dot Browser

Now, we're going to want to build Dot Browser for Linux.

 It's a very resource intensive process so make sure you check the requirements against your computer. It usually takes 30 minutes for computers in the recommended requirements region.

```text
./melon build linux
```

The build runs inside a Docker container so it is separate from your actual machine.

Once the build is done, we need to make sure the build was successful, check to see if something appeared like:

```text
01:00:00 Your build was successful!
```

If you see that message, you can move on to the final step.

## Running Dot Browser

The final step is to run your locally-built version of Dot Browser. 

It's as simple as running:

```text
./melon run
```

And voilà, Dot should appear before your eyes!

![It&apos;s magic! &#x2728;](../.gitbook/assets/tenor.gif)

If you encounter any issues, [open an issue on our GitHub repository](https://github.com/dothq/browser/issues/new/choose).



