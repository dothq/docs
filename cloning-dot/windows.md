---
description: >-
  This is a step by step guide on how to build Dot Browser on the world's most
  popular operating system, Windows.
---

# 🏁 Windows

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
	* Don't know if your computer is 64-bit? \(You can [check here](https://superuser.com/a/1225322/1083268)\).
	* Optionally, The Windows 10 ISO is downloadable through the [Installation Media tool](https://www.microsoft.com/en-us/software-download/windows10)

* The following software and tools are required for the build process:
  * Git \([git-scm.org](https://git-scm.org)\)
  * MozillaBuild CLI \([mozilla.org](https://ftp.mozilla.org/pub/mozilla.org/mozilla/libraries/win32/MozillaBuildSetup-Latest.exe))
  * Visual Studio \([visualstudio.microsoft.com](https://visualstudio.microsoft.com/downloads/)\)
  * Docker \([docker.com](https://www.docker.com))
  * Python 2.7 and 3.9 \([python.org](https://www.python.org/))
  * Rust \([rust-lang.org](https://www.rust-lang.org/tools/install))
  * Node.JS \([nodejs.org](https://nodejs.org))
    * Yarn (`npm i -g yarn`)
    * Typescript (`npm i -g typescript`)
    
* Select the following settings in Visual Studio Installer:
  * Desktop development with C++
  * Game development with C++
  * Windows 10 SDK \(version **10.0.17134.0 or higher**\)

{% hint style="info" %}
Dot Browser is based on Firefox, which is why it is referenced a lot in the build process.
{% endhint %}

## Clone the repository

We're now going to clone Dot Browser.

{% tabs %} {% tab title="HTTPS" %}

```text
git clone https://github.com/dothq/browser-ff
```

{% endtab %}

{% tab title="SSH" %}

```text
git clone git@github.com:/dothq/browser-ff
```
{% endtab %} {% endtabs %}

Or if you prefer using GitLab:

{% tabs %} {% tab title="HTTPS" %}

```text
git clone https://gitlab.com/dothq/browser-ff
```
{% endtab %}

{% tab title="SSH" %}

```text
git clone  git@gitlab.com:dothq/browser-ff.git
```
{% endtab %} {% endtabs %}

After the clone is complete, you'll want to enter the `browser-ff` directory in Git Bash.

### Downloading the source code and mounting

To download and set up the source code, run the following commands in Git Bash:
```bash
./melon download
./windows-init.sh
```

{% hint style="info" %}
`melon` is a build toolkit for Dot Browser.
{% endhint %}

## Importing the patches

Next, you're going to want to import the patches. You can do this by running the command below in Git Bash.

```bash
./melon import
```

If everything went smoothly with the import, you should see a "success" message.

{% hint style="tip" %}
If you see an error saying that a patch failed due to different line endings, run `./melon fix-le` in Git Bash and try again.
{% endhint %}

## Building Dot Browser

Now, we're going to want to build Dot Browser for Windows.

 It's a very resource intensive process so make sure you check the requirements against your computer. It usually takes between 30 minutes and an hour for computers meeting the recommended requirements.

To start the build, open a MozillaBuild terminal and `cd` into `browser-ff`. To start the build, run these commands in MozillaBuild:

```bash
cd src
MOZCONFIG=../configs/windows/mozconfig ./mach build
```

{% hint style="tip" %}
If you get an error about missing required dependencies, you can install them by running `./melon download-artifacts` in Git Bash.
{% endhint %}

Once the build is done, we need to make sure the build was successful. Check to see if something appeared like:

```text
01:00:00 Your build was successful!
```

If you see that message, you can move on to the final step.

## Running Dot Browser

The final step is to run your locally-built version of Dot Browser. 

It's as simple as entering the `src` folder and running:

```bash
./mach run
```

And voilà, Dot should appear before your eyes!

![It&apos;s magic! &#x2728;](../.gitbook/assets/tenor.gif)

{% hint style="info" %}
The Windows build process is still a work-in-progress. If you encounter any issues, please [open an issue on our GitHub repository](https://github.com/dothq/browser/issues/new/choose).
{% endhint %}
