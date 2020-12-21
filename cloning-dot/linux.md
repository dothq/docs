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

## Downloading the bootstrapper

We're now going to install the tool to clone and bootstrap Dot Browser.

```text
curl https://raw.githubusercontent.com/dothq/browser-ff/master/python/mozboot/bin/bootstrap.py -o bootstrap.py
```

This will download the `bootstrap.py` Python script from GitHub.

Now we want to run the bootstrapper. You can do this by typing:

```text
python3 bootstrap.py
```

## Step 1: Getting the source code

If a `clone.sh` file appeared in your `browser/tools` directory from the last step, everything went smoothly.

You are now ready to get the source code by typing the following commands in Git Bash:

```bash
cd browser
./tools/clone.sh
```

{% hint style="info" %}
This will take up to 30 minutes to complete and will take up ~3 GB of storage. It's just enough time for you grab a coffee while you wait.
{% endhint %}

Once it's complete it should give you a success message, if you did not see a success message then something has gone wrong with the clone.

To verify that all the files were cloned by typing `ls`. You should see something like this:

```text
dot   firefox   tools
```

You can now progress to step 2.

## Step 2: Bootstrapping the project

You've almost made it! The next step is to bootstrap the project, this is as simple as typing the command in the `browser/firefox` directory:

```text
./mach bootstrap
```

The bootstrapper will ask you how you want to build Firefox. 

{% hint style="info" %}
Dot Browser is based on Firefox source code, which is why it is referenced a lot in the build process.
{% endhint %}

For _speedy builds_, you're going to want to use artifact mode "Firefox for Desktop Artifact Mode" by typing the number one into the terminal.

For **full-fat** builds, you're going want to select option two "Firefox for Desktop" by typing the number two into the terminal.

There are many differences between speedy builds \(artifact builds\) and full fat builds.

|  | Artifact builds | Full fat builds |
| :--- | :--- | :--- |
| Time to build | ~10 seconds | ~1 hour |
| Can build on low-end computers | ✅ | ❌ |
| Can build front-end | ✅ | ✅ |
| Can build C++ | ❌ | ✅ |
| Can build Rust | ❌ | ✅ |
| Modify build system | ❌ | ✅ |

When the bootstrapped asks, make sure you setup Git so it is "optimally configured".

If you get no errors, then you have successfully bootstrapped the browser. You can now progress to step 3.

## Step 3: Synchronising the project

WIP

Becoming a super hero is a fairly straight forward process:

```
$ give me super-powers
```

{% hint style="info" %}
 Super-powers are granted randomly so please submit an issue if you're not happy with yours.
{% endhint %}

Once you're strong enough, save the world:

{% code title="hello.sh" %}
```bash
# Ain't no code for that yet, sorry
echo 'You got to trust me on this, I saved the world'
```
{% endcode %}



