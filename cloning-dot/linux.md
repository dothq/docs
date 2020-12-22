---
description: This is a step by step guide on how to build Dot Browser on Linux.
---

# 🐧 Linux

## First things first...

* Make sure you have at least 20 GB of space free on your hard drive.
* You'll need to be on a 64-bit operating system to clone and build Dot Browser.
  * If typing `uname -m` into a terminal returns `x86_64` you are on a 64-bit computer.
* The following software and tools are required for the build process:
  * Git \([git-scm.org](https://git-scm.org)\)
  * Mercurial \([mercurial-scm.org](https://www.mercurial-scm.org/)\)
  * python3 \([python.org](https://www.python.org/downloads/)\)
  * python2 \([python.org](https://python.org)\)
  * git-cinnabar \([github.com/glandium/git-cinnabar/\#setup](https://github.com/glandium/git-cinnabar/#setup)\)

{% hint style="info" %}
Dot Browser is based on Firefox, which is why it is referenced a lot in the build process.
{% endhint %}

## Downloading the bootstrapper

We're now going to install the tool to clone and bootstrap Dot Browser.

```text
curl https://raw.githubusercontent.com/dothq/browser-ff/master/python/mozboot/bin/bootstrap.py -o bootstrap.py
```

This will download the `bootstrap.py` Python script from GitHub.

Now we want to run the bootstrapper by typing the command below. The bootstrap will take around 10 minutes up to a couple hours.

```bash
python3 bootstrap.py
```

After the clone is complete the bootstrapper will ask you what version you want to build. This table will demonstrate the differences between an artifact build and a generic build.

|  | Artifact builds | Generic builds |
| :--- | :--- | :--- |
| Time to build | ~10 seconds | ~1 hour |
| Can build on low-end computers | ✅ | ❌ |
| Can build front-end \(HTML, CSS, JS\) | ✅ | ✅ |
| Can build C++ code | ❌ | ✅ |
| Can build Rust code | ❌ | ✅ |
| Modify build system | ❌ | ✅ |

## Building Dot Browser

It's time to build the browser! Start by entering the repo directory.

```bash
cd dot # or the name of the repo you chose in the bootstrapper
```

Now we can start building.

```text
./mach build
```

If everything went smoothly with the build you should see the following text:

```jsx
1:03.56 Your build was successful!
To take your build for a test drive, run: |mach run|
```

## Running Dot Browser

You've made it! You have successfully built Dot Browser. Now it's time to our build for a test drive. We can do that by running:

```text
./mach run
```

If everything went according to plan, you should see Dot Browser appear before your eyes!

![It&apos;s magic! &#x2728;](../.gitbook/assets/tenor.gif)



