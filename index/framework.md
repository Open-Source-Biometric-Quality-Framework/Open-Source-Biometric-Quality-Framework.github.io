---
layout: default
title: Framework
nav_order: 5
permalink: /framework/
---

# Framework

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

## Project Diagram

 The OpenBQ framework consists of the [command line interface](https://github.com/Open-Source-Biometric-Quality-Framework/bqConnect-CLI), and a [desktop app](https://github.com/Open-Source-Biometric-Quality-Framework/bqinsights).

``` mermaid
---
title: OpenBQ
config:
  theme: neutral
  layout: elk
---
graph TD
  core((BQ Core Service)) --> cli(BQConnect CLI)
  core --> gui(BQInsights Desktop)
```


### BQ Core

The core component of OpenBQ implement various vendor algorithms, including face, fingerprint, iris and voice processing engines. 

It will analyse the input biometric files and produce the quality metrics. 

``` mermaid
---
title: BQ Core Service
config:
  theme: neutral
  layout: elk
---
graph LR
    input(Biometric files) --> core{BQ Core}
    core{BQ Core} --> face(Face)
    core{BQ Core} --> finger(Fingerprint)
    core{BQ Core} --> iris(Iris)
    core{BQ Core} --> speech(Speech)
```

### Interfaces

BQ Core service is exposed via command line interfaces.

``` mermaid
---
title: BQConnect CLI
config:
  theme: neutral
  layout: elk
---
graph LR
    input(Input Folder) --> cli{Command Line}
    cli{Command Line} --> report(EDA Report)
    cli{Command Line} --> output(CSV)
    cli{Command Line} --> log(Log)
```

+ The BQConnect CLI provides terminal commands to interact with bqcore service.

+ It takes a folder in your file system as input and produces the raw metrics in CSV along with a EDA report.

+ It is distributed as Docker container as well as a Python entry point application.

### BQInsights Desktop

BQInsights provide a GUI to the CLI tool as well as data analysis capabilities via local LLM.

``` mermaid
---
title: BQInsights Desktop
config:
  theme: neutral
  layout: elk
---
graph LR
    input(Input Folder) --> desktop{Desktop Application}
    desktop <--> cli[BQConnect CLI]
    desktop <--> llm[Loacal AI Host]
```

## System Requirements

### Operating System

+ x86, ARM platform
+ Linux, Windows, macOS

> Since data processing is compute-intensive, you may want to allocate more cpu/memory with the host machine for better performance and stability.

### Runtime

OpenBQ deliverables are packaged as Docker containers, you will need Docker engine to host the container.

### Performance Benchmark

Test Platform 1: 6/12 cores, amd64, Ubtuntu 25.10, 16 GB of RAM.

| Mode | Throughput (per second) \| (per hour) |
| --- | --- |
| Face (obqe) | 9.86 \| 35,496 |
| Face (OFIQ) | 1.02 \| 3,672 |
| Face (BIQT) | 3.75 \| 13,500 |
| Fingerprint (NFIQ2) | 7.16 \| 25,776 |
| Iris (BIQT) | 18.63 \| 67,068 |
| Speech (NISQA) | 0.77 \| 2,772 |

Test Platform 2: 14 cores, arm64, macOS 15.6.1, 32 GB of RAM.

| Mode | Throughput (per second) \| (per hour) |
| --- | --- |
| Face (obqe) | 53.94 \| 194,184 |
| Face (OFIQ) | 2.08 \| 7,488 |
| Face (BIQT) | 8.54 \| 30,744 |
| Fingerprint (NFIQ2) | 14.54 \| 52,344 |
| Iris (BIQT) | 40.14 \| 144,504 |
| Speech (NISQA) | 1.50 \| 5,400 |


> As new quality metrics added to the engine, the benchmark number above might not reflect the current status of the project.

