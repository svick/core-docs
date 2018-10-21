---
title: Prerequisites for .NET Core on Linux
description: Supported Linux versions and .NET Core dependencies to develop, deploy, and run .NET Core applications on Linux machines.
author: jralexander
ms.author: johalex
ms.date: 08/20/2018
---
# Prerequisites for .NET Core on Linux

This article shows the dependencies needed to develop .NET Core applications on Linux. The supported Linux distributions/versions, and dependencies that follow apply to the two ways of developing .NET Core apps on Linux:

* [Command-line with your favorite editor](tutorials/using-with-xplat-cli.md)
* [Visual Studio Code](https://code.visualstudio.com/)

> [!NOTE]
> The .NET Core SDK package is not required for production servers/environments. Only the .NET Core runtime package is needed for apps deployed to production environments. The .NET Core runtime is deployed with apps as part of a self-contained deployment, however, it must be deployed for Framework-dependent deployed apps separately. For more information about framework-dependent and self-contained deployment types, see [.NET Core application deployment](./deploying/index.md). Also see [Self-contained Linux applications](https://github.com/dotnet/core/blob/master/Documentation/self-contained-linux-apps.md) for specific guidelines.

## Supported Linux versions

# [.NET Core 2.x](#tab/netcore2x)

.NET Core 2.x treats Linux as a single operating system. There is a single Linux build (per chip architecture) for supported Linux distributions.

**NET Core 2.1**

NET Core 2.1 is supported on the following Linux distributions/versions:

* Red Hat Enterprise Linux 7, 6 - 64-bit (`x86_64` or `amd64`)
* CentOS 7  - 64-bit (`x86_64` or `amd64`) 
* Oracle Linux 7 - 64-bit (`x86_64` or `amd64`) 
* Fedora 28, 27 - 64-bit (`x86_64` or `amd64`) 
* Debian 9 (64-bit, `arm32`), 8.7 or later versions - 64-bit (`x86_64` or `amd64`)
* Ubuntu 18.04 (64-bit, `arm32`), 16.04, 14.04 - 64-bit (`x86_64` or `amd64`)
* Linux Mint 18, 17 - 64-bit (`x86_64` or `amd64`)
* openSUSE 42.3 or later versions - 64-bit (`x86_64` or `amd64`)
* SUSE Enterprise Linux (SLES) 12 Service Pack 2 or later - 64-bit (`x86_64` or `amd64`)
* Alpine Linux 3.7 or later versions - 64-bit (`x86_64` or `amd64`)

See [.NET Core 2.1 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md) for the complete list of .NET Core 2.1 supported operating systems, distributions and versions, out of support OS versions, and lifecycle policy links.

**NET Core 2.0**

NET Core 2.0 is supported on the following Linux 64-bit (`x86_64` or `amd64`) distributions/versions:

* Red Hat Enterprise Linux 7, 6
* CentOS 7
* Oracle Linux 7
* Fedora 27
* Debian 9, 8.7 or later versions
* Ubuntu 18.04, 16.04, 14.04
* Linux Mint 18, 17
* openSUSE 42.3 or later versions
* SUSE Enterprise Linux (SLES) 12 Service Pack 2 or later

See [.NET Core 2.0 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/2.0/2.0-supported-os.md) for the complete list of .NET Core 2.0 supported operating systems, distributions and versions, out of support OS versions, and lifecycle policy links.

# [.NET Core 1.x](#tab/netcore1x)

.NET Core 1.x is supported on the following Linux 64-bit (`x86_64` or `amd64`) distributions/versions:

* Red Hat Enterprise Linux 7
* CentOS 7
* Oracle Linux 7
* Fedora 28 (.NET Core 1.1), 27
* Debian 8.2 or later versions
* Ubuntu 18.04 (.NET Core 1.1), 16.04, 14.04
* Linux Mint 17
* openSUSE 42.3 or later versions (.NET Core 1.1)

See [.NET Core 1.x Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0-supported-os.md) for the complete list of .NET Core 1.x supported operating systems, out of support OS versions, and lifecycle policy links.

---

## Linux distribution dependencies

The following are intended to be examples. The exact versions and names may vary slightly on your Linux distribution of choice.

### Ubuntu

Ubuntu distributions require the following libraries installed:

* liblttng-ust0
* libcurl3
* libssl1.0.0
* libkrb5-3
* zlib1g
* libicu52 (for 14.x)
* libicu55 (for 16.x)
* libicu57 (for 17.x)
* libicu60 (for 18.x)

For versions earlier than .NET Core 2.1, following dependencies are also required:

* libunwind8
* libuuid1

### CentOS and Fedora

CentOS distributions require the following libraries installed:

* lttng-ust
* libcurl
* openssl-libs
* krb5-libs
* libicu
* zlib

Fedora users: If your openssl's version >= 1.1, you'll need to install compat-openssl10.

For versions earlier than .NET Core 2.1, following dependencies are also required:

* libunwind
* libuuid

For more information about the dependencies, see [Self-contained Linux applications](https://github.com/dotnet/core/blob/master/Documentation/self-contained-linux-apps.md).

## Installing .NET Core dependencies with the native installers

.NET Core native installers are available for supported Linux distributions/versions. The native installers require admin (sudo) access to the server. The advantage of using a native installer is that all of the .NET Core native dependencies are installed. Native installers also install the .NET Core SDK system-wide.

On Linux, there are two installer package choices:

* Using a feed-based package manager, such as apt-get for Ubuntu, or yum for CentOS/RHEL.
* Using the packages themselves, DEB or RPM.

### Scripting Installs with the .NET Core installer script

The [dotnet-install scripts](./tools/dotnet-install-script.md) are used to perform a non-admin install of the CLI toolchain and the shared runtime. You can download the script from [https://dot.net/v1/dotnet-install.sh](https://dot.net/v1/dotnet-install.sh).

The script defaults to installing the latest "LTS" version, which is currently .NET Core 1.1. To install .NET Core 2.x, run the script with the following switch:

```console
./dotnet-install.sh -c Current
```

The installer bash script is used in automation scenarios and non-admin installations. This script also reads PowerShell switches, so they can be used with the script on Linux/OS X systems.

## Install .NET Core for supported Red Hat Enterprise Linux (RHEL) versions

To install .NET Core on supported RHEL versions:

# [.NET Core 2.x](#tab/netcore2x)

**.NET Core 2.1**

1. Remove any **previous preview** versions of .NET Core from your system.

2. For the latest .NET Core 2.1 on Red Hat Enterprise Linux installation information, see [the .NET Core 2.1 Getting Started Guide](https://access.redhat.com/documentation/en-us/net_core/2.1/html/getting_started_guide/)

**.NET Core 2.0**

1. Remove any **previous preview** versions of .NET Core from your system.

2. For the latest .NET Core 2.0 on Red Hat Enterprise Linux installation information, see [the .NET Core 2.0 Getting Started Guide](https://access.redhat.com/documentation/en-us/net_core/2.0/html/getting_started_guide/) 

# [.NET Core 1.x](#tab/netcore1x)

**.NET Core 1.1**

1. Remove any **previous preview** versions of .NET Core from your system.

2.  For the latest .NET Core 1.1 on Red Hat Enterprise Linux installation information, see [the .NET Core 1.1 Getting Started Guide](https://access.redhat.com/documentation/en-us/net_core/1.1/html/getting_started_guide/)
     
**.NET Core 1.0**

1. Remove any **previous preview** versions of .NET Core from your system.

2.  For the latest .NET Core 1.0 on Red Hat Enterprise Linux installation information, see [the .NET Core 1.0 Getting Started Guide](https://access.redhat.com/documentation/en-us/net_core/1.0/html/getting_started_guide/)

For Red Hat .NET channel access registration help, see [Chapter 1 of the .NET Core 1.1 Getting Started Guide](https://access.redhat.com/documentation/en/net-core/1.1/paged/getting-started-guide/) at Red Hat.

---

## Install .NET Core for supported Ubuntu and Linux Mint distributions/versions (64 bit)

# [.NET Core 2.x](#tab/netcore2x)

1. Remove any **previous preview** versions of .NET Core from your system.

2. Install .NET Core 2.x on supported Ubuntu and Linux Mint distributions/versions (64 bit):

**.NET Core 2.0**

|Runtimes / SDKs          |Ubuntu 18.04    |Ubuntu 17.10    |Ubuntu 16.04 / Linux Mint 18|Ubuntu 14.04 / Linux Mint 17|
|-------------------------|----------------|----------------|----------------------------|----------------------------|
|.NET Core Runtime 2.0.9  |[Install link](https://www.microsoft.com/net/download/linux-package-manager/ubuntu18-04/runtime-2.0.9)|[Install link](https://www.microsoft.com/net/download/linux-package-manager/ubuntu17-10/runtime-2.0.9)|[Install link](https://www.microsoft.com/net/download/linux-package-manager/ubuntu16-04/runtime-2.0.9)          |[Install link](https://www.microsoft.com/net/download/linux-package-manager/ubuntu14-04/runtime-2.0.9)            |
|.NET Core Runtime 2.0.8  |[Install link](https://www.microsoft.com/net/download/linux-package-manager/ubuntu18-04/runtime-2.0.8)|[Install link](https://www.microsoft.com/net/download/linux-package-manager/ubuntu17-10/runtime-2.0.8)|[Install link](https://www.microsoft.com/net/download/linux-package-manager/ubuntu16-04/runtime-2.0.8)          |[Install link](https://www.microsoft.com/net/download/linux-package-manager/ubuntu14-04/runtime-2.0.8)            |
|.NET Core Runtime 2.0.7  |[Install link](https://www.microsoft.com/net/download/linux-package-manager/ubuntu18-04/runtime-2.0.7)|[Install link](https://www.microsoft.com/net/download/linux-package-manager/ubuntu17-10/runtime-2.0.7)|[Install link](https://www.microsoft.com/net/download/linux-package-manager/ubuntu16-04/runtime-2.0.7)          |[Install link](https://www.microsoft.com/net/download/linux-package-manager/ubuntu14-04/runtime-2.0.7)            |
|.NET Core Runtime 2.0.6  |[Install link](https://www.microsoft.com/net/download/linux-package-manager/ubuntu18-04/runtime-2.0.6)|[Install link](https://www.microsoft.com/net/download/linux-package-manager/ubuntu17-10/runtime-2.0.6)|[Install link](https://www.microsoft.com/net/download/linux-package-manager/ubuntu16-04/runtime-2.0.6)          |[Install link](https://www.microsoft.com/net/download/linux-package-manager/ubuntu14-04/runtime-2.0.6)            |
|.NET Core Runtime 2.0.5  |[Install link](https://www.microsoft.com/net/download/linux-package-manager/ubuntu18-04/runtime-2.0.5)|[Install link](https://www.microsoft.com/net/download/linux-package-manager/ubuntu17-10/runtime-2.0.5)|[Install link](https://www.microsoft.com/net/download/linux-package-manager/ubuntu16-04/runtime-2.0.5)          |[Install link](https://www.microsoft.com/net/download/linux-package-manager/ubuntu14-04/runtime-2.0.5)            |
|.NET Core SDK 2.1.202    |[Install link](https://www.microsoft.com/net/download/linux-package-manager/ubuntu18-04/sdk-2.1.202)|[Install link](https://www.microsoft.com/net/download/linux-package-manager/ubuntu17-10/sdk-2.1.202)|[Install link](https://www.microsoft.com/net/download/linux-package-manager/ubuntu16-04/sdk-2.1.202)            |[Install link](https://www.microsoft.com/net/download/linux-package-manager/ubuntu14-04/sdk-2.1.202)            |
|.NET Core SDK 2.1.201    |[Install link](https://www.microsoft.com/net/download/linux-package-manager/ubuntu18-04/sdk-2.1.201)|[Install link](https://www.microsoft.com/net/download/linux-package-manager/ubuntu17-10/sdk-2.1.201)|[Install link](https://www.microsoft.com/net/download/linux-package-manager/ubuntu16-04/sdk-2.1.201)            |[Install link](https://www.microsoft.com/net/download/linux-package-manager/ubuntu14-04/sdk-2.1.201)            |
|.NET Core SDK 2.1.200    |[Install link](https://www.microsoft.com/net/download/linux-package-manager/ubuntu18-04/sdk-2.1.200)|[Install link](https://www.microsoft.com/net/download/linux-package-manager/ubuntu17-10/sdk-2.1.200)|[Install link](https://www.microsoft.com/net/download/linux-package-manager/ubuntu16-04/sdk-2.1.200)            |[Install link](https://www.microsoft.com/net/download/linux-package-manager/ubuntu14-04/sdk-2.1.200)            |
|.NET Core SDK 2.1.105    |[Install link](https://www.microsoft.com/net/download/linux-package-manager/ubuntu18-04/sdk-2.1.105)|[Install link](https://www.microsoft.com/net/download/linux-package-manager/ubuntu17-10/sdk-2.1.105)|[Install link](https://www.microsoft.com/net/download/linux-package-manager/ubuntu16-04/sdk-2.1.105)            |[Install link](https://www.microsoft.com/net/download/linux-package-manager/ubuntu14-04/sdk-2.1.105)            |
|.NET Core SDK 2.1.103    |[Install link](https://www.microsoft.com/net/download/linux-package-manager/ubuntu18-04/sdk-2.1.103)|[Install link](https://www.microsoft.com/net/download/linux-package-manager/ubuntu17-10/sdk-2.1.103)|[Install link](https://www.microsoft.com/net/download/linux-package-manager/ubuntu16-04/sdk-2.1.103)            |[Install link](https://www.microsoft.com/net/download/linux-package-manager/ubuntu14-04/sdk-2.1.103)            |
|.NET Core SDK 2.0.3      |[Install link](https://www.microsoft.com/net/download/linux-package-manager/ubuntu18-04/sdk-2.0.3)|[Install link](https://www.microsoft.com/net/download/linux-package-manager/ubuntu17-10/sdk-2.0.3)|[Install link](https://www.microsoft.com/net/download/linux-package-manager/ubuntu16-04/sdk-2.0.3)          |[Install link](https://www.microsoft.com/net/download/linux-package-manager/ubuntu14-04/sdk-2.0.3)            |
|.NET Core SDK 2.0.0      |[Install link](https://www.microsoft.com/net/download/linux-package-manager/ubuntu18-04/sdk-2.0.0)|[Install link](https://www.microsoft.com/net/download/linux-package-manager/ubuntu17-10/sdk-2.0.0)|[Install link](https://www.microsoft.com/net/download/linux-package-manager/ubuntu16-04/sdk-2.0.0)          |[Install link](https://www.microsoft.com/net/download/linux-package-manager/ubuntu14-04/sdk-2.0.0)            |

**.NET Core 2.1**

>[!IMPORTANT]
> To use .NET Core 2.1 with Visual Studio, you need to [install Visual Studio 2017 15.7 or newer](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017).

|Runtimes / SDKs          |Ubuntu 18.04    |Ubuntu 17.10    |Ubuntu 16.04 / Linux Mint 18|Ubuntu 14.04 / Linux Mint 17|
|-------------------------|----------------|----------------|----------------------------|----------------------------|
|.NET Core Runtime 2.1.2          |[Install link](https://www.microsoft.com/net/download/linux-package-manager/ubuntu18-04/runtime-2.1.2)|[Install link](https://www.microsoft.com/net/download/linux-package-manager/ubuntu17-10/runtime-2.1.2)            |[Install link](https://www.microsoft.com/net/download/linux-package-manager/ubuntu16-04/runtime-2.1.2)            |[Install link](https://www.microsoft.com/net/download/linux-package-manager/ubuntu14-04/runtime-2.1.2)            |
|.NET Core SDK 2.1.400     |[Install link](https://www.microsoft.com/net/download/linux-package-manager/ubuntu18-04/sdk-2.1.400)|[Install link](https://www.microsoft.com/net/download/linux-package-manager/ubuntu17-10/sdk-2.1.400)            |[Install link](https://www.microsoft.com/net/download/linux-package-manager/ubuntu16-04/sdk-2.1.400)            |[Install link](https://www.microsoft.com/net/download/linux-package-manager/ubuntu14-04/sdk-2.1.400)            |
|.NET Core SDK 2.1.302     |[Install link](https://www.microsoft.com/net/download/linux-package-manager/ubuntu18-04/sdk-2.1.302)|[Install link](https://www.microsoft.com/net/download/linux-package-manager/ubuntu17-10/sdk-2.1.302)            |[Install link](https://www.microsoft.com/net/download/linux-package-manager/ubuntu16-04/sdk-2.1.302)            |[Install link](https://www.microsoft.com/net/download/linux-package-manager/ubuntu14-04/sdk-2.1.302)            |
|.NET Core Runtime 2.1.1          |[Install link](https://www.microsoft.com/net/download/linux-package-manager/ubuntu18-04/runtime-2.1.1)|[Install link](https://www.microsoft.com/net/download/linux-package-manager/ubuntu17-10/runtime-2.1.1)            |[Install link](https://www.microsoft.com/net/download/linux-package-manager/ubuntu16-04/runtime-2.1.1)            |[Install link](https://www.microsoft.com/net/download/linux-package-manager/ubuntu14-04/runtime-2.1.1)            |
|.NET Core SDK 2.1.301     |[Install link](https://www.microsoft.com/net/download/linux-package-manager/ubuntu18-04/sdk-2.1.301)|[Install link](https://www.microsoft.com/net/download/linux-package-manager/ubuntu17-10/sdk-2.1.301)            |[Install link](https://www.microsoft.com/net/download/linux-package-manager/ubuntu16-04/sdk-2.1.301)            |[Install link](https://www.microsoft.com/net/download/linux-package-manager/ubuntu14-04/sdk-2.1.301)            |
|.NET Core Runtime 2.1.0          |[Install link](https://www.microsoft.com/net/download/linux-package-manager/ubuntu18-04/runtime-2.1.0)|[Install link](https://www.microsoft.com/net/download/linux-package-manager/ubuntu17-10/runtime-2.1.0)|[Install link](https://www.microsoft.com/net/download/linux-package-manager/ubuntu16-04/runtime-2.1.0)            |[Install link](https://www.microsoft.com/net/download/linux-package-manager/ubuntu14-04/runtime-2.1.0)            |
|.NET Core SDK 2.1.300     |[Install link](https://www.microsoft.com/net/download/linux-package-manager/ubuntu18-04/sdk-2.1.300)|[Install link](https://www.microsoft.com/net/download/linux-package-manager/ubuntu17-10/sdk-2.1.300)|[Install link](https://www.microsoft.com/net/download/linux-package-manager/ubuntu16-04/sdk-2.1.300)            |[Install link](https://www.microsoft.com/net/download/linux-package-manager/ubuntu14-04/sdk-2.1.300)            |

# [.NET Core 1.x](#tab/netcore1x)

1. Remove any **previous preview** versions of .NET Core from your system.

2. Install .NET Core 1.x on supported Ubuntu and Linux Mint distributions/versions (64 bit):

| Runtimes / SDKs         |Ubuntu 16.04 / Linux Mint 18|Ubuntu 14.04 / Linux Mint 17|
|-------------------------|----------------------------|----------------------------|
|.NET Core Runtime 1.1.9  |[Install link](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.1.9-linux-ubuntu-16.04-x64-binaries)            |[Install link](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.1.8-linux-ubuntu-14.04-x64-binaries)            |
|.NET Core Runtime 1.1.8  |[Install link](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.1.7-linux-ubuntu-16.04-x64-binaries)            |[Install link](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.1.7-linux-ubuntu-14.04-x64-binaries)            |
|.NET Core Runtime 1.1.7  |[Install link](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.1.7-linux-ubuntu-16.04-x64-binaries)            |[Install link](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.1.7-linux-ubuntu-14.04-x64-binaries)            |
|.NET Core Runtime 1.1.6  |[Install link](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.1.6-linux-ubuntu-16.04-x64-binaries)            |[Install link](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.1.6-linux-ubuntu-14.04-x64-binaries)            |
|.NET Core Runtime 1.1.5  |[Install link](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.1.5-linux-ubuntu-16.04-x64-binaries)            |[Install link](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.1.5-linux-ubuntu-14.04-x64-binaries)            |
|.NET Core Runtime 1.1.4  |[Install link](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.1.4-linux-ubuntu-16.04-x64-binaries)            |[Install link](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.1.4-linux-ubuntu-14.04-x64-binaries)            |
|.NET Core Runtime 1.0.10 |[Install link](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.0.10-linux-ubuntu-16.04-x64-binaries)            |[Install link](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.0.10-linux-ubuntu-14.04-x64-binaries)            |
|.NET Core Runtime 1.0.9  |[Install link](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.0.9-linux-ubuntu-16.04-x64-binaries)            |[Install link](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.0.9-linux-ubuntu-14.04-x64-binaries)            |
|.NET Core Runtime 1.0.8  |[Install link](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.0.8-linux-ubuntu-16.04-x64-binaries)            |[Install link](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.0.8-linux-ubuntu-14.04-x64-binaries)            |
|.NET Core Runtime 1.0.7  |[Install link](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.0.7-linux-ubuntu-16.04-x64-binaries)            |[Install link](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.0.7-linux-ubuntu-14.04-x64-binaries)            |
|.NET Core Runtime 1.0.5  |[Install link](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.0.5-linux-ubuntu-16.04-x64-binaries)            |[Install link](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.0.5-linux-ubuntu-14.04-x64-binaries)            |
|.NET Core Runtime 1.0.4  |[Install link](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.0.4-linux-ubuntu-16.04-x64-binaries)            |[Install link](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.0.4-linux-ubuntu-14.04-x64-binaries)            |
|.NET Core SDK 1.1.10     |[Install link](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.1.10-linux-ubuntu-16.04-x64-binaries)            |[Install link](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.1.10-linux-ubuntu-14.04-x64-binaries)            |
|.NET Core SDK 1.1.9      |[Install link](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.1.9-linux-ubuntu-16.04-x64-binaries)            |[Install link](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.1.9-linux-ubuntu-14.04-x64-binaries)            |
|.NET Core SDK 1.1.8      |[Install link](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.1.8-linux-ubuntu-16.04-x64-binaries)            |[Install link](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.1.8-linux-ubuntu-14.04-x64-binaries)            |
|.NET Core SDK 1.1.7      |[Install link](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.1.7-linux-ubuntu-16.04-x64-binaries)            |[Install link](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.1.7-linux-ubuntu-14.04-x64-binaries)            |
|.NET Core SDK 1.1.5      |[Install link](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.1.5-linux-ubuntu-16.04-x64-binaries)            |[Install link](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.1.5-linux-ubuntu-14.04-x64-binaries)            |
|.NET Core SDK 1.1.4      |[Install link](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.1.4-linux-ubuntu-16.04-x64-binaries)            |[Install link](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.1.4-linux-ubuntu-14.04-x64-binaries)            |
|.NET Core SDK 1.0.4      |[Install link](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.0.4-linux-ubuntu-16.04-x64-binaries)            |[Install link](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.0.4-linux-ubuntu-14.04-x64-binaries)            |
|.NET Core SDK 1.0.1      |[Install link](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.0.1-linux-ubuntu-16.04-x64-binaries)            |[Install link](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.0.1-linux-ubuntu-14.04-x64-binaries)            |

---

## Install .NET Core for supported Debian versions (64 bit)

To install .NET Core on supported Debian versions (64 bit):

> [!NOTE]
> A user-controlled directory is required for Linux system installs from tar.gz.

# [.NET Core 2.x](#tab/netcore2x)

1. Remove any **previous preview** versions of .NET Core from your system.

2. Install .NET Core 2.x on supported Debian versions (64 bit):

**.NET Core 2.0**

|Runtimes / SDKs          |Debian 9       |Debian 8       |
|-------------------------|---------------|---------------|
|.NET Core Runtime 2.0.9  |[Install link](https://www.microsoft.com/net/download/linux-package-manager/debian9/runtime-2.0.9)   |[Install link](https://www.microsoft.com/net/download/linux-package-manager/debian8/runtime-2.0.9)   |
|.NET Core Runtime 2.0.8  |[Install link](https://www.microsoft.com/net/download/linux-package-manager/debian9/runtime-2.0.8)   |[Install link](https://www.microsoft.com/net/download/linux-package-manager/debian8/runtime-2.0.8)   |
|.NET Core Runtime 2.0.7  |[Install link](https://www.microsoft.com/net/download/linux-package-manager/debian9/runtime-2.0.7)   |[Install link](https://www.microsoft.com/net/download/linux-package-manager/debian8/runtime-2.0.7)   |
|.NET Core Runtime 2.0.6  |[Install link](https://www.microsoft.com/net/download/linux-package-manager/debian9/runtime-2.0.6)   |[Install link](https://www.microsoft.com/net/download/linux-package-manager/debian8/runtime-2.0.6)   |
|.NET Core Runtime 2.0.5  |[Install link](https://www.microsoft.com/net/download/linux-package-manager/debian9/runtime-2.0.5)   |[Install link](https://www.microsoft.com/net/download/linux-package-manager/debian8/runtime-2.0.5)   |
|.NET Core Runtime 2.0.3  |[Install link](https://www.microsoft.com/net/download/linux-package-manager/debian9/runtime-2.0.3)   |[Install link](https://www.microsoft.com/net/download/linux-package-manager/debian8/runtime-2.0.3)   |
|.NET Core Runtime 2.0.0  |[Install link](https://www.microsoft.com/net/download/linux-package-manager/debian9/runtime-2.0.0)   |[Install link](https://www.microsoft.com/net/download/linux-package-manager/debian8/runtime-2.0.0)   |
|.NET Core SDK 2.1.202    |[Install link](https://www.microsoft.com/net/download/linux-package-manager/debian9/sdk-2.1.202)   |[Install link](https://www.microsoft.com/net/download/linux-package-manager/debian8/sdk-2.1.202)   |
|.NET Core SDK 2.1.201    |[Install link](https://www.microsoft.com/net/download/linux-package-manager/debian9/sdk-2.1.201)   |[Install link](https://www.microsoft.com/net/download/linux-package-manager/debian8/sdk-2.1.201)   |
|.NET Core SDK 2.1.200    |[Install link](https://www.microsoft.com/net/download/linux-package-manager/debian9/sdk-2.1.200)   |[Install link](https://www.microsoft.com/net/download/linux-package-manager/debian8/sdk-2.1.200)   |
|.NET Core SDK 2.1.105    |[Install link](https://www.microsoft.com/net/download/linux-package-manager/debian9/sdk-2.1.105)   |[Install link](https://www.microsoft.com/net/download/linux-package-manager/debian8/sdk-2.1.105)   |
|.NET Core SDK 2.1.105    |[Install link](https://www.microsoft.com/net/download/linux-package-manager/debian9/sdk-2.1.105)   |[Install link](https://www.microsoft.com/net/download/linux-package-manager/debian8/sdk-2.1.105)   |
|.NET Core SDK 2.1.104    |[Install link](https://www.microsoft.com/net/download/linux-package-manager/debian9/sdk-2.1.104)   |[Install link](https://www.microsoft.com/net/download/linux-package-manager/debian8/sdk-2.1.104)   |
|.NET Core SDK 2.1.103    |[Install link](https://www.microsoft.com/net/download/linux-package-manager/debian9/sdk-2.1.103)   |[Install link](https://www.microsoft.com/net/download/linux-package-manager/debian8/sdk-2.1.103)   |
|.NET Core SDK 2.1.102    |[Install link](https://www.microsoft.com/net/download/linux-package-manager/debian9/sdk-2.1.102)   |[Install link](https://www.microsoft.com/net/download/linux-package-manager/debian8/sdk-2.1.102)   |
|.NET Core SDK 2.1.101    |[Install link](https://www.microsoft.com/net/download/linux-package-manager/debian9/sdk-2.1.101)   |[Install link](https://www.microsoft.com/net/download/linux-package-manager/debian8/sdk-2.1.101)   |
|.NET Core SDK 2.0.3      |[Install link](https://www.microsoft.com/net/download/linux-package-manager/debian9/sdk-2.0.3)   |[Install link](https://www.microsoft.com/net/download/linux-package-manager/debian8/sdk-2.0.3)   |
|.NET Core SDK 2.0.0      |[Install link](https://www.microsoft.com/net/download/linux-package-manager/debian9/sdk-2.0.0)   |[Install link](https://www.microsoft.com/net/download/linux-package-manager/debian8/sdk-2.0.0)   |

**.NET Core 2.1**

>[!IMPORTANT]
> To use .NET Core 2.1 with Visual Studio, you need to [install Visual Studio 2017 15.7 or newer](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017).

|Runtimes / SDKs                  |Debian 9       |Debian 8       |
|---------------------------------|---------------|---------------|
|.NET Core Runtime 2.1.2          |[Install link](https://www.microsoft.com/net/download/linux-package-manager/debian9/runtime-2.1.2)   |[Install link](https://www.microsoft.com/net/download/linux-package-manager/debian8/runtime-2.1.2)   |
|.NET Core SDK 2.1.400        |[Install link](https://www.microsoft.com/net/download/linux-package-manager/debian9/sdk-2.1.400)   |[Install link](https://www.microsoft.com/net/download/linux-package-manager/debian8/sdk-2.1.400)        |
|.NET Core SDK 2.1.302        |[Install link](https://www.microsoft.com/net/download/linux-package-manager/debian9/sdk-2.1.302)   |[Install link](https://www.microsoft.com/net/download/linux-package-manager/debian8/sdk-2.1.302)        |
|.NET Core Runtime 2.1.1          |[Install link](https://www.microsoft.com/net/download/linux-package-manager/debian9/runtime-2.1.1)   |[Install link](https://www.microsoft.com/net/download/linux-package-manager/debian8/runtime-2.1.1)   |
|.NET Core SDK 2.1.301        |[Install link](https://www.microsoft.com/net/download/linux-package-manager/debian9/sdk-2.1.301)   |[Install link](https://www.microsoft.com/net/download/linux-package-manager/debian8/sdk-2.1.301)        |
|.NET Core Runtime 2.1.0          |[Install link](https://www.microsoft.com/net/download/linux-package-manager/debian9/runtime-2.1.0)   |[Install link](https://www.microsoft.com/net/download/linux-package-manager/debian8/runtime-2.1.0)   |
|.NET Core SDK 2.1.300        |[Install link](https://www.microsoft.com/net/download/linux-package-manager/debian9/sdk-2.1.300)   |[Install link](https://www.microsoft.com/net/download/linux-package-manager/debian8/sdk-2.1.300)        |

# [.NET Core 1.x](#tab/netcore1x)

1. Remove any **previous preview** versions of .NET Core from your system.

2. Install .NET Core 1.x on Debian 9 or Debian 8:

* .NET Core Runtime 1.1.9 [install link](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.1.9-linux-debian-x64-binaries)
* .NET Core Runtime 1.1.8 [install link](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.1.8-linux-debian-x64-binaries)
* .NET Core Runtime 1.1.7 [install link](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.1.7-linux-debian-x64-binaries)
* .NET Core Runtime 1.1.6 [install link](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.1.6-linux-debian-x64-binaries)
* .NET Core Runtime 1.1.5 [install link](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.1.5-linux-debian-x64-binaries)
* .NET Core Runtime 1.1.4 [install link](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.1.4-linux-debian-x64-binaries)
* .NET Core Runtime 1.1.2 [install link](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.1.2-linux-debian-x64-binaries)
* .NET Core Runtime 1.1.1 [install link](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.1.1-linux-debian-x64-binaries)
* .NET Core Runtime 1.1.0 [install link](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.1.0-linux-debian-x64-binaries)
* .NET Core Runtime 1.0.10 [install link](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.0.10-linux-debian-x64-binaries)
* .NET Core Runtime 1.0.9 [install link](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.0.9-linux-debian-x64-binaries)
* .NET Core Runtime 1.0.8 [install link](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.0.8-linux-debian-x64-binaries)
* .NET Core Runtime 1.0.7 [install link](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.0.7-linux-debian-x64-binaries)
* .NET Core Runtime 1.0.5 [install link](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.0.5-linux-debian-x64-binaries)
* .NET Core Runtime 1.0.4 [install link](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.0.4-linux-debian-x64-binaries)
* .NET Core SDK 1.1.10 [install link](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.1.10-linux-debian-x64-binaries)
* .NET Core SDK 1.1.9 [install link](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.1.9-linux-debian-x64-binaries)
* .NET Core SDK 1.1.8 [install link](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.1.8-linux-debian-x64-binaries)
* .NET Core SDK 1.1.7 [install link](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.1.7-linux-debian-x64-binaries)
* .NET Core SDK 1.1.5 [install link](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.1.5-linux-debian-x64-binaries)
* .NET Core SDK 1.1.4 [install link](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.1.4-linux-debian-x64-binaries)
* .NET Core SDK 1.0.4 [install link](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.0.4-linux-debian-x64-binaries)
* .NET Core SDK 1.0.1 [install link](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.0.1-linux-debian-x64-binaries)

---

## Install .NET Core for supported Fedora versions (64 bit)

To install .NET Core on supported Fedora versions:

> [!NOTE]
> A user-controlled directory is required for Linux system installs from tar.gz.

# [.NET Core 2.x](#tab/netcore2x)

1. Remove any **previous preview** versions of .NET Core from your system.

2. Install .NET Core 2.x on supported Fedora versions (64 bit):

**.NET Core 2.0**

|Runtimes / SDKs          |Fedora 26 or later |Fedora 25 or previous |
|-------------------------|-------------------|----------------------|
|.NET Core Runtime 2.0.9  |[Install link](https://www.microsoft.com/net/download/linux-package-manager/fedora26/runtime-2.0.9)       |[Install link](https://www.microsoft.com/net/download/linux-package-manager/fedora25/runtime-2.0.9)           |
|.NET Core Runtime 2.0.8  |[Install link](https://www.microsoft.com/net/download/linux-package-manager/fedora26/runtime-2.0.8)       |[Install link](https://www.microsoft.com/net/download/linux-package-manager/fedora25/runtime-2.0.8)           |
|.NET Core Runtime 2.0.7  |[Install link](https://www.microsoft.com/net/download/linux-package-manager/fedora26/runtime-2.0.7)       |[Install link](https://www.microsoft.com/net/download/linux-package-manager/fedora25/runtime-2.0.7)           |
|.NET Core Runtime 2.0.6  |[Install link](https://www.microsoft.com/net/download/linux-package-manager/fedora26/runtime-2.0.6)       |[Install link](https://www.microsoft.com/net/download/linux-package-manager/fedora25/runtime-2.0.6)           |
|.NET Core Runtime 2.0.5  |[Install link](https://www.microsoft.com/net/download/linux-package-manager/fedora26/runtime-2.0.5)       |[Install link](https://www.microsoft.com/net/download/linux-package-manager/fedora25/runtime-2.0.5)           |
|.NET Core Runtime 2.0.3  |[Install link](https://www.microsoft.com/net/download/linux-package-manager/fedora26/runtime-2.0.3)       |[Install link](https://www.microsoft.com/net/download/linux-package-manager/fedora25/runtime-2.0.3)           |
|.NET Core Runtime 2.0.0  |[Install link](https://www.microsoft.com/net/download/linux-package-manager/fedora26/runtime-2.0.0)       |[Install link](https://www.microsoft.com/net/download/linux-package-manager/fedora25/runtime-2.0.0)           |
|.NET Core SDK 2.1.200    |[Install link](https://www.microsoft.com/net/download/linux-package-manager/fedora26/sdk-2.1.200)       |[Install link](https://www.microsoft.com/net/download/linux-package-manager/fedora25/sdk-2.1.200)           |
|.NET Core SDK 2.1.105    |[Install link](https://www.microsoft.com/net/download/linux-package-manager/fedora26/sdk-2.1.105)       |[Install link](https://www.microsoft.com/net/download/linux-package-manager/fedora25/sdk-2.1.105)           |
|.NET Core SDK 2.1.103    |[Install link](https://www.microsoft.com/net/download/linux-package-manager/fedora26/sdk-2.1.103)       |[Install link](https://www.microsoft.com/net/download/linux-package-manager/fedora25/sdk-2.1.103)           |
|.NET Core SDK 2.0.3      |[Install link](https://www.microsoft.com/net/download/linux-package-manager/fedora26/sdk-2.0.3)       |[Install link](https://www.microsoft.com/net/download/linux-package-manager/fedora25/sdk-2.0.3)           |

**.NET Core 2.1**

>[!IMPORTANT]
> To use .NET Core 2.1 with Visual Studio, you need to [install Visual Studio 2017 15.7 or newer](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017).

|Runtimes / SDKs                  |Fedora 28          |Fedora 27             |
|---------------------------------|-------------------|----------------------|
|.NET Core Runtime 2.1.2          |[Install link](https://www.microsoft.com/net/download/linux-package-manager/fedora28/runtime-2.1.2)       |[Install link](https://www.microsoft.com/net/download/linux-package-manager/fedora27/runtime-2.1.2)           |
|.NET Core SDK 2.1.400          |[Install link](https://www.microsoft.com/net/download/linux-package-manager/fedora28/sdk-2.1.400)       |[Install link](https://www.microsoft.com/net/download/linux-package-manager/fedora27/sdk-2.1.400)           |
|.NET Core SDK 2.1.302          |[Install link](https://www.microsoft.com/net/download/linux-package-manager/fedora28/sdk-2.1.302)       |[Install link](https://www.microsoft.com/net/download/linux-package-manager/fedora27/sdk-2.1.302)           |
|.NET Core Runtime 2.1.1          |[Install link](https://www.microsoft.com/net/download/linux-package-manager/fedora28/runtime-2.1.1)       |[Install link](https://www.microsoft.com/net/download/linux-package-manager/fedora27/runtime-2.1.1)           |
|.NET Core SDK 2.1.301          |[Install link](https://www.microsoft.com/net/download/linux-package-manager/fedora28/sdk-2.1.301)       |[Install link](https://www.microsoft.com/net/download/linux-package-manager/fedora27/sdk-2.1.301)           |
|.NET Core Runtime 2.1.0          |[Install link](https://www.microsoft.com/net/download/linux-package-manager/fedora28/runtime-2.1.0)       |[Install link](https://www.microsoft.com/net/download/linux-package-manager/fedora27/runtime-2.1.0)           |
|.NET Core SDK 2.1.300          |[Install link](https://www.microsoft.com/net/download/linux-package-manager/fedora28/sdk-2.1.300)       |[Install link](https://www.microsoft.com/net/download/linux-package-manager/fedora27/sdk-2.1.300)           |

# [.NET Core 1.x](#tab/netcore1x)

1. Remove any **previous preview** versions of .NET Core from your system.

2. Install .NET Core 1.x supported Fedora versions (64 bit):

**Fedora 24**

* .NET Core Runtime 1.1.8 [install link](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.1.8-linux-fedora-24-x64-binaries)
* .NET Core Runtime 1.1.7 [install link](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.1.7-linux-fedora-24-x64-binaries)
* .NET Core Runtime 1.1.6 [install link](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.1.6-linux-fedora-24-x64-binaries)
* .NET Core Runtime 1.1.5 [install link](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.1.5-linux-fedora-24-x64-binaries)
* .NET Core Runtime 1.1.4 [install link](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.1.4-linux-fedora-24-x64-binaries)
* .NET Core Runtime 1.1.2 [install link](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.1.2-linux-fedora-24-x64-binaries)
* .NET Core Runtime 1.1.1 [install link](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.1.1-linux-fedora-24-x64-binaries)
* .NET Core SDK 1.1.9 [install link](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.1.9-linux-fedora-24-x64-binaries)
* .NET Core SDK 1.1.8 [install link](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.1.8-linux-fedora-24-x64-binaries)
* .NET Core SDK 1.1.7 [install link](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.1.7-linux-fedora-24-x64-binaries)
* .NET Core SDK 1.1.5 [install link](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.1.5linux-fedora-24-x64-binaries)
* .NET Core SDK 1.1.4 [install link](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.1.5linux-fedora-24-x64-binaries)
* .NET Core SDK 1.0.1 [install link](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.0.1-linux-debian-x64-binaries)

**Fedora 23**

* .NET Core Runtime 1.1.4 [install link](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.1.4-linux-fedora-23-x64-binaries)
* .NET Core Runtime 1.1.2 [install link](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.1.2-linux-fedora-23-x64-binaries)
* .NET Core Runtime 1.1.1 [install link](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.1.1-linux-fedora-23-x64-binaries)
* .NET Core Runtime 1.0.9 [install link](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.0.9-linux-fedora-23-x64-binaries)
* .NET Core Runtime 1.0.4 [install link](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.0.4-linux-fedora-23-x64-binaries)
* .NET Core SDK 1.1.4 [install link](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.1.4linux-fedora-23-x64-binaries)
* .NET Core SDK 1.1.2 [install link](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.1.2linux-fedora-23-x64-binaries)
* .NET Core SDK 1.1.2 [install link](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.1.2linux-fedora-23-x64-binaries)
* .NET Core SDK 1.0.4 [install link](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.0.4-linux-fedora-23-x64-binaries)
* .NET Core SDK 1.0.1 [install link](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.0.1-linux-fedora-23-x64-binaries)

---

## Install .NET Core for supported CentOS and Oracle Linux distributions/versions (64 bit)

To install .NET Core for supported CentOS and Oracle Linux distributions/versions (64 bit):

> [!NOTE]
> A user-controlled directory is required for Linux system installs from tar.gz.

# [.NET Core 2.x](#tab/netcore2x)

1. Remove any **previous preview** versions of .NET Core from your system.

2. Install .NET Core 2.x on supported CentOS and Oracle Linux distributions/versions (64 bit):

**.NET Core 2.0**

* .NET Core Runtime 2.0.9 [install link](https://www.microsoft.com/net/download/linux-package-manager/centos/runtime-2.0.9)
* .NET Core Runtime 2.0.8 [install link](https://www.microsoft.com/net/download/linux-package-manager/centos/runtime-2.0.8)
* .NET Core Runtime 2.0.7 [install link](https://www.microsoft.com/net/download/linux-package-manager/centos/runtime-2.0.7)
* .NET Core Runtime 2.0.6 [install link](https://www.microsoft.com/net/download/linux-package-manager/centos/runtime-2.0.6)
* .NET Core Runtime 2.0.5 [install link](https://www.microsoft.com/net/download/linux-package-manager/centos/runtime-2.0.5)
* .NET Core Runtime 2.0.3 [install link](https://www.microsoft.com/net/download/linux-package-manager/centos/runtime-2.0.3)
* .NET Core Runtime 2.0.0 [install link](https://www.microsoft.com/net/download/linux-package-manager/centos/runtime-2.0.0)
* .NET Core SDK 2.1.202 [install link](https://www.microsoft.com/net/download/linux-package-manager/centos/sdk-2.1.202)
* .NET Core SDK 2.1.201 [install link](https://www.microsoft.com/net/download/linux-package-manager/centos/sdk-2.1.201)
* .NET Core SDK 2.1.200 [install link](https://www.microsoft.com/net/download/linux-package-manager/centos/sdk-2.1.200)
* .NET Core SDK 2.1.105 [install link](https://www.microsoft.com/net/download/linux-package-manager/centos/sdk-2.1.105)
* .NET Core SDK 2.1.104 [install link](https://www.microsoft.com/net/download/linux-package-manager/centos/sdk-2.1.104)
* .NET Core SDK 2.1.103 [install link](https://www.microsoft.com/net/download/linux-package-manager/centos/sdk-2.1.103)
* .NET Core SDK 2.1.102 [install link](https://www.microsoft.com/net/download/linux-package-manager/centos/sdk-2.1.102)
* .NET Core SDK 2.0.3 [install link](https://www.microsoft.com/net/download/linux-package-manager/centos/sdk-2.0.3)
* .NET Core SDK 2.0.0 [install link](https://www.microsoft.com/net/download/linux-package-manager/centos/sdk-2.0.0)
 
**.NET Core 2.1**

>[!IMPORTANT]
> To use .NET Core 2.1 with Visual Studio, you need to [install Visual Studio 2017 15.7 or newer](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017).

* .NET Core Runtime 2.1.2  [install link](https://www.microsoft.com/net/download/linux-package-manager/centos/runtime-2.1.2)
* .NET Core SDK 2.1.400 [install link](https://www.microsoft.com/net/download/linux-package-manager/centos/sdk-2.1.400)
* .NET Core SDK 2.1.302 [install link](https://www.microsoft.com/net/download/linux-package-manager/centos/sdk-2.1.302)
* .NET Core Runtime 2.1.1  [install link](https://www.microsoft.com/net/download/linux-package-manager/centos/runtime-2.1.1)
* .NET Core SDK 2.1.301 [install link](https://www.microsoft.com/net/download/linux-package-manager/centos/sdk-2.1.301)
* .NET Core Runtime 2.1.0  [install link](https://www.microsoft.com/net/download/linux-package-manager/centos/runtime-2.1.0)
* .NET Core SDK 2.1.300 [install link](https://www.microsoft.com/net/download/linux-package-manager/centos/sdk-2.1.300)

# [.NET Core 1.x](#tab/netcore1x)

1. Remove any **previous preview** versions of .NET Core from your system.

2. Install .NET Core 1.x on supported CentOS and Oracle Linux distributions/versions (64 bit):

* .NET Core Runtime 1.1.9 [install link](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.1.9-linux-centos-x64-binaries)
* .NET Core Runtime 1.1.8 [install link](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.1.8-linux-centos-x64-binaries)
* .NET Core Runtime 1.1.7 [install link](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.1.7-linux-centos-x64-binaries)
* .NET Core Runtime 1.1.6 [install link](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.1.6-linux-centos-x64-binaries)
* .NET Core Runtime 1.1.5 [install link](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.1.5-linux-centos-x64-binaries)
* .NET Core Runtime 1.1.4 [install link](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.1.4-linux-centos-x64-binaries)
* .NET Core Runtime 1.1.2 [install link](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.1.2-linux-centos-x64-binaries)
* .NET Core Runtime 1.1.1 [install link](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.1.1-linux-centos-x64-binaries)
* .NET Core Runtime 1.0.12 [install link](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.0.12-linux-centos-x64-binaries)
* .NET Core Runtime 1.0.11 [install link](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.0.11-linux-centos-x64-binaries)
* .NET Core Runtime 1.0.10 [install link](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.0.10-linux-centos-x64-binaries)
* .NET Core Runtime 1.0.9 [install link](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.0.9-linux-centos-x64-binaries)
* .NET Core Runtime 1.0.8 [install link](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.0.8-linux-centos-x64-binaries)
* .NET Core Runtime 1.0.7 [install link](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.0.7-linux-centos-x64-binaries)
* .NET Core Runtime 1.0.5 [install link](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.0.5-linux-centos-x64-binaries)
* .NET Core Runtime 1.0.4 [install link](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.0.4-linux-centos-x64-binaries)
* .NET Core SDK 1.1.10 [install link](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.1.10-linux-centos-x64-binaries)
* .NET Core SDK 1.1.9 [install link](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.1.9-linux-centos-x64-binaries)
* .NET Core SDK 1.1.8 [install link](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.1.8-linux-centos-x64-binaries)
* .NET Core SDK 1.1.7 [install link](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.1.7-linux-centos-x64-binaries)
* .NET Core SDK 1.1.5 [install link](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.1.5-linux-centos-x64-binaries)
* .NET Core SDK 1.1.4 [install link](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.1.4-linux-centos-x64-binaries)
* .NET Core SDK 1.0.4 [install link](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.0.4-linux-centos-x64-binaries)
* .NET Core SDK 1.0.1 [install link](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.0.1-linux-centos-x64-binaries)

---

## Install .NET Core for supported SUSE Linux Enterprise Server and OpenSUSE distributions/versions (64 bit)

To install .NET Core 2.x for supported SUSE Linux Enterprise Server and OpenSUSE distributions/versions (64 bit):

# [.NET Core 2.x](#tab/netcore2x)

1. Remove any **previous preview** versions of .NET Core from your system.

2. Install .NET Core 2.x on supported SUSE Linux Enterprise Server and OpenSUSE distributions/versions (64 bit):

**.NET Core 2.0**

**SUSE Linux Enterprise Server**

* .NET Core Runtime 2.0.9 [install link](https://www.microsoft.com/net/download/linux-package-manager/sles/runtime-2.0.9)
* .NET Core Runtime 2.0.8 [install link](https://www.microsoft.com/net/download/linux-package-manager/sles/runtime-2.0.8)
* .NET Core Runtime 2.0.7 [install link](https://www.microsoft.com/net/download/linux-package-manager/sles/runtime-2.0.7)
* .NET Core Runtime 2.0.6 [install link](https://www.microsoft.com/net/download/linux-package-manager/sles/runtime-2.0.6)
* .NET Core Runtime 2.0.5 [install link](https://www.microsoft.com/net/download/linux-package-manager/sles/runtime-2.0.5)
* .NET Core Runtime 2.0.3 [install link](https://www.microsoft.com/net/download/linux-package-manager/sles/runtime-2.0.3)
* .NET Core Runtime 2.0.0 [install link](https://www.microsoft.com/net/download/linux-package-manager/sles/runtime-2.0.0)
* .NET Core SDK 2.1.202 [install link](https://www.microsoft.com/net/download/linux-package-manager/sles/sdk-2.1.202)
* .NET Core SDK 2.1.201 [install link](https://www.microsoft.com/net/download/linux-package-manager/sles/sdk-2.1.201)
* .NET Core SDK 2.1.200 [install link](https://www.microsoft.com/net/download/linux-package-manager/sles/sdk-2.1.200)
* .NET Core SDK 2.1.105 [install link](https://www.microsoft.com/net/download/linux-package-manager/sles/sdk-2.1.105)
* .NET Core SDK 2.1.104 [install link](https://www.microsoft.com/net/download/linux-package-manager/sles/sdk-2.1.104)
* .NET Core SDK 2.1.103 [install link](https://www.microsoft.com/net/download/linux-package-manager/sles/sdk-2.1.103)
* .NET Core SDK 2.1.102 [install link](https://www.microsoft.com/net/download/linux-package-manager/sles/sdk-2.1.102)
* .NET Core SDK 2.1.101 [install link](https://www.microsoft.com/net/download/linux-package-manager/sles/sdk-2.1.101)
* .NET Core SDK 2.1.100 [install link](https://www.microsoft.com/net/download/linux-package-manager/sles/sdk-2.1.100)
* .NET Core SDK 2.1.4 [install link](https://www.microsoft.com/net/download/linux-package-manager/sles/sdk-2.1.4)
* .NET Core SDK 2.1.2 [install link](https://www.microsoft.com/net/download/linux-package-manager/sles/sdk-2.1.2)
* .NET Core SDK 2.0.3 [install link](https://www.microsoft.com/net/download/linux-package-manager/sles/sdk-2.0.3)
* .NET Core SDK 2.0.0 [install link](https://www.microsoft.com/net/download/linux-package-manager/sles/sdk-2.0.0)

**openSUSE**

* .NET Core Runtime 2.0.9 [install link](https://www.microsoft.com/net/download/linux-package-manager/opensuse/runtime-2.0.9)
* .NET Core Runtime 2.0.8 [install link](https://www.microsoft.com/net/download/linux-package-manager/opensuse/runtime-2.0.8)
* .NET Core Runtime 2.0.7 [install link](https://www.microsoft.com/net/download/linux-package-manager/opensuse/runtime-2.0.7)
* .NET Core Runtime 2.0.6 [install link](https://www.microsoft.com/net/download/linux-package-manager/opensuse/runtime-2.0.6)
* .NET Core Runtime 2.0.5 [install link](https://www.microsoft.com/net/download/linux-package-manager/opensuse/runtime-2.0.5)
* .NET Core Runtime 2.0.3 [install link](https://www.microsoft.com/net/download/linux-package-manager/opensuse/runtime-2.0.3)
* .NET Core Runtime 2.0.0 [install link](https://www.microsoft.com/net/download/linux-package-manager/opensuse/runtime-2.0.0)
* .NET Core SDK 2.1.202 [install link](https://www.microsoft.com/net/download/linux-package-manager/opensuse/sdk-2.1.202)
* .NET Core SDK 2.1.201 [install link](https://www.microsoft.com/net/download/linux-package-manager/opensuse/sdk-2.1.201)
* .NET Core SDK 2.1.200 [install link](https://www.microsoft.com/net/download/linux-package-manager/opensuse/sdk-2.1.200)
* .NET Core SDK 2.1.105 [install link](https://www.microsoft.com/net/download/linux-package-manager/opensuse/sdk-2.1.105)
* .NET Core SDK 2.1.103 [install link](https://www.microsoft.com/net/download/linux-package-manager/opensuse/sdk-2.1.103)
* .NET Core SDK 2.1.102 [install link](https://www.microsoft.com/net/download/linux-package-manager/opensuse/sdk-2.1.102)
* .NET Core SDK 2.1.101 [install link](https://www.microsoft.com/net/download/linux-package-manager/opensuse/sdk-2.1.101)
* .NET Core SDK 2.1.100 [install link](https://www.microsoft.com/net/download/linux-package-manager/opensuse/sdk-2.1.100)
* .NET Core SDK 2.1.4 [install link](https://www.microsoft.com/net/download/linux-package-manager/opensuse/sdk-2.1.4)
* .NET Core SDK 2.1.2 [install link](https://www.microsoft.com/net/download/linux-package-manager/opensuse/sdk-2.1.2)
* .NET Core SDK 2.0.3 [install link](https://www.microsoft.com/net/download/linux-package-manager/opensuse/sdk-2.0.3)
* .NET Core SDK 2.0.0 [install link](https://www.microsoft.com/net/download/linux-package-manager/opensuse/sdk-2.0.0)
 
**.NET Core 2.1**

>[!IMPORTANT]
> To use .NET Core 2.1 with Visual Studio, you need to [install Visual Studio 2017 15.7 or newer](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017).

**SUSE Linux Enterprise Server**

* .NET Core Runtime 2.1.2 [install link](https://www.microsoft.com/net/download/linux-package-manager/sles/runtime-2.1.2)
* .NET Core SDK 2.1.400 [install link](https://www.microsoft.com/net/download/linux-package-manager/sles/sdk-2.1.400)
* .NET Core SDK 2.1.302 [install link](https://www.microsoft.com/net/download/linux-package-manager/sles/sdk-2.1.302)
* .NET Core Runtime 2.1.1 [install link](https://www.microsoft.com/net/download/linux-package-manager/sles/runtime-2.1.1)
* .NET Core SDK 2.1.301 [install link](https://www.microsoft.com/net/download/linux-package-manager/sles/sdk-2.1.301)
* .NET Core Runtime 2.1.0 [install link](https://www.microsoft.com/net/download/linux-package-manager/sles/runtime-2.1.0)
* .NET Core SDK 2.1.300 [install link](https://www.microsoft.com/net/download/linux-package-manager/sles/sdk-2.1.300)

**openSUSE**

* .NET Core Runtime 2.1.2 [install link](https://www.microsoft.com/net/download/linux-package-manager/opensuse/runtime-2.1.2)
* .NET Core SDK 2.1.400 [install link](https://www.microsoft.com/net/download/linux-package-manager/opensuse/sdk-2.1.400)
* .NET Core SDK 2.1.302 [install link](https://www.microsoft.com/net/download/linux-package-manager/opensuse/sdk-2.1.302)
* .NET Core Runtime 2.1.1 [install link](https://www.microsoft.com/net/download/linux-package-manager/opensuse/runtime-2.1.1)
* .NET Core SDK 2.1.301 [install link](https://www.microsoft.com/net/download/linux-package-manager/opensuse/sdk-2.1.301)
* .NET Core Runtime 2.1.0 [install link](https://www.microsoft.com/net/download/linux-package-manager/opensuse/runtime-2.1.0)
* .NET Core SDK 2.1.300 [install link](https://www.microsoft.com/net/download/linux-package-manager/opensuse/sdk-2.1.300)

# [.NET Core 1.x](#tab/netcore1x)

1. Remove any **previous preview** versions of .NET Core from your system.

2. Install .NET Core 1.x on supported SUSE Linux Enterprise Server and OpenSUSE distributions/versions (64 bit):

**SUSE Linux Enterprise Server 13.2**

* .NET Core Runtime 1.1.7 [install link](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.1.7-linux-opensuse-13.2-x64-binaries)
* .NET Core Runtime 1.1.6 [install link](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.1.6-linux-opensuse-13.2-x64-binaries)
* .NET Core SDK 1.1.7 [install link](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.1.7-linux-opensuse-13.2-x64-binaries)
* .NET Core SDK 1.0.4 [install link](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.0.4-linux-opensuse-13.2-x64-binaries)
* .NET Core SDK 1.0.1 [install link](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.0.1-linux-opensuse-13.2-x64-binaries)

---

## Install .NET Core for supported Alpine Linux versions (64 bit)

> [!NOTE]
> A user-controlled directory is required for Linux system installs from tar.gz.

Download and follow the .NET Core 2.1 installation instructions for supported Alpine Linux versions (64 bit) at the following links:

* .NET Core Runtime 2.1.2 [download link](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-2.1.2-linux-x64-alpine-binaries)
* .NET Core SDK 2.1.400 [download link](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-2.1.400-linux-x64-alpine-binaries)
* .NET Core SDK 2.1.302 [download link](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-2.1.302-linux-x64-alpine-binaries)
* .NET Core Runtime 2.1.1 [download link](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-2.1.1-linux-x64-alpine-binaries)
* .NET Core SDK 2.1.301 [download link](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-2.1.301-linux-x64-alpine-binaries)
* .NET Core Runtime 2.1.0 [download link](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-2.1.0-linux-x64-alpine-binaries)
* .NET Core SDK 2.1.300 [download link](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-2.1.300-linux-x64-alpine-binaries)

> [!IMPORTANT]
> If you have problems with a .NET Core installation on a supported Linux distribution/version, consult the following topics for your installed distributions/versions:
> * [.NET Core 2.1 known issues](https://github.com/dotnet/core/tree/master/release-notes/2.1)
> * [.NET Core 2.0 known issues](https://github.com/dotnet/core/tree/master/release-notes/2.0)
> * [.NET Core 1.1 known issues](https://github.com/dotnet/core/blob/master/release-notes/1.1)
> * [.NET Core 1.0 known issues](https://github.com/dotnet/core/blob/master/release-notes/1.0)
