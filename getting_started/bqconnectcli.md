---
layout: default
title: bqconnect CLI
parent: Getting Started
nav_order: 1
---

# bqconnect CLI

[![GitHub Tag](https://img.shields.io/github/v/tag/biometix/bqat-cli)](https://github.com/Biometix/bqat-cli/releases)
[![PyPI - Version](https://img.shields.io/pypi/v/bqat)](https://pypi.python.org/pypi/bqat)
[![PyPI - Downloads](https://img.shields.io/pypi/dm/bqat)](https://pypi.python.org/pypi/bqat)

---
<details open markdown="block">
  <summary>
    Table of contents
  </summary>
  {: .text-delta }
- TOC
{:toc}
</details>

---

{: .highlight }
> 🚀 Introducing the new [bqconnect CLI](https://pypi.org/project/openbq/)!

{: .highlight }
> 🌟 bqconnect CLI now supports ARM-based CPUs! Whether you're on an Apple M‑series or a Qualcomm Snapdragon X‑series processor, you can leverage its performance for biometric data analysis.


## Setup

Prerequisites:
- [Docker](https://www.docker.com/)
- Python (3.10+)
- AMD64 or ARM64 CPU

### Install bqconnect CLI
{: .no_toc }

```sh
pip install openbq
```

<a name="usage">
## Usage

To validate the installation, you could start a benchmark task.

```sh
openbq --benchmark
```

Example use cases for biometric quality assessment:

``` sh
# Process all face images in 'data/'
openbq --input data --mode face

# Process iris images in 'data/iris/'
openbq --input data/iris --mode iris

# Process all face images using OFIQ engine
openbq --input data --mode face --engine OFIQ

# Enable EDA report for the assessment
openbq --input data/fingerprint --mode fingerprint --report
```

Check current installed version:

```sh
openbq --verison
```

Get bqconnect CLI Update if available:

``` sh
openbq --update
```

<a name="uninstall">
## Uninstall

```sh
openbq --uninstall
```

<a name="output">
## Output

open**bq** will produce the quality metrics in a CSV file, a EDA report when enabled.

## Further details about the command and advanced option flags
{: .no_toc }
+ [Command Line Interface Cookbook](https://docs.openbq.io/cookbook/bqconnectcli.html)
