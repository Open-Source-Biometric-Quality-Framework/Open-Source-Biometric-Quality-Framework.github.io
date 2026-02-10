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

 The openbq framework consists of the [bqcore](https://github.com/Open-Source-Biometric-Quality-Framework/bqCore) backend service, a [command line interface](https://github.com/Open-Source-Biometric-Quality-Framework/bqConnect-CLI), and a [desktop app](https://github.com/Open-Source-Biometric-Quality-Framework/bqConnect-Desktop).

``` mermaid
---
title: openbq
config:
  theme: neutral
  layout: elk
---
graph TD
  core((bqcore service)) --> cli(bqconnect CLI)
  core --> gui(bqconnect Desktop)
```


### bqcore

The core component of openbq implement various vendor algorithms, including face, fingerprint, iris and voice processing engines. 

It will analyse the input biometric files and produce the quality metrics. 

``` mermaid
---
title: bqcore
config:
  theme: neutral
  layout: elk
---
graph LR
    input(Biometric files) --> core{bqcore}
    core{bqcore} --> face(Face)
    core{bqcore} --> finger(Fingerprint)
    core{bqcore} --> iris(Iris)
    core{bqcore} --> speech(Speech)
```

### Interfaces

bqcore service is exposed via different interfaces (CLI and GUI), which handle data loading, data management and task queueing.

***

``` mermaid
---
title: bqconnect CLI
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

+ The bqconnect CLI provides terminal commands to interact with bqcore.

+ It takes a folder in your file system as input and produces the raw metrics in CSV along with a EDA report.

+ It is distributed as Docker container as well as a Python entry point application.

***

``` mermaid
---
title: bqconnect Desktop
config:
  theme: neutral
  layout: elk
---
graph LR
    upload(Upload) --> gui{Web}
    gui{Web GUI} --> api(bqconnect Service)
    api(Backend) --> db[(Database)]
    db[(Database)] --> report(EDA Report)
    db[(Database)] --> output(Raw CSV)
    db[(Database)] --> outlier(Outliers Detected)
```

+ bqconnect Desktop is a GUI application for openbq.

+ Can, currently, only be deployed as a desktop application.

+ Vertical scaling only.

+ It is distributed as Docker container.


## System Requirements

### Operating System

+ x86, ARM platform
+ Linux, Windows, macOS

> Since data processing is compute-intensive, you may want to allocate more cpu/memory with the host machine for better performance and stability.

### Runtime

openbq deliverables are packaged as Docker containers, you will need Docker engine to host the container.

### Performance Benchmark

Test Platform 1: 6/12 cores, amd64, Ubtuntu 25.10, 16 GB of RAM.

| Mode | Throughput (per second) \| (per hour) |
| --- | --- |
| Face (openbq) | 9.86 \| 35,496 |
| Face (OFIQ) | 1.02 \| 3,672 |
| Face (BIQT) | 3.75 \| 13,500 |
| Fingerprint (NFIQ2) | 7.16 \| 25,776 |
| Iris (BIQT) | 18.63 \| 67,068 |
| Speech (NISQA) | 0.77 \| 2,772 |

Test Platform 2: 14 cores, arm64, macOS 15.6.1, 32 GB of RAM.

| Mode | Throughput (per second) \| (per hour) |
| --- | --- |
| Face (openbq) | 53.94 \| 194,184 |
| Face (OFIQ) | 2.08 \| 7,488 |
| Face (BIQT) | 8.54 \| 30,744 |
| Fingerprint (NFIQ2) | 14.54 \| 52,344 |
| Iris (BIQT) | 40.14 \| 144,504 |
| Speech (NISQA) | 1.50 \| 5,400 |


> As new quality metrics added to the engine, the benchmark number above might not reflect the current status of the project.


> Test done in iris mode.
