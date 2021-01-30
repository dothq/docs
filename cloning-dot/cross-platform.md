---
description: >-
  Dot Browser supports cross-platform building. For example, you could be on
  Windows and you want to build for Linux.
---

# 🤝 Cross-platform

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

* The following software and tools are required for the build process:
  * Git \([git-scm.org](https://git-scm.org)\)
  * NodeJS \([nodejs.org](https://nodejs.org)\)
  * yarn \([npmjs.com/package/yarn](https://www.npmjs.com/package/yarn)\)
  * Docker

{% hint style="warning" %}
Follow steps 1 \(Cloning Dot Browser\) and 2 \(Importing patches\) on your host machine and then come back here to start step 3
{% endhint %}

## Supported build targets

| Build target | Supported? |
| :--- | :--- |
| Windows 64-bit | ✅ |
| macOS 64-bit | ✅ |
| Linux 64-bit | ✅ |
| Windows 32-bit | ❌ |
| macOS 32-bit | ❌ |
| Linux 32-bit | ❌ |

## Building Dot Browser

Now, we're going to want to build Dot Browser for your target OS.

See [Supported build targets](cross-platform.md#supported-build-targets) for a list of supported build targets.

 It's a very resource intensive process so make sure you check the requirements against your computer. It usually takes 30 minutes for computers in the recommended requirements region.

```bash
./melon build <target-os> # target-os could be: windows, macos or linux
```

Once the build is done, we need to make sure the build was successful, check to see if something appeared like:

```text
01:00:00 Your build was successful!
```

If you see that message, you can move on to the final step.

