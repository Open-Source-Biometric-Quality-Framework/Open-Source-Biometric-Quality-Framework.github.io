---
layout: default
title: Limitations
parent: Cookbooks
nav_order: 5
---

### Memory Pressure

When processing a large dataset, you may encounter OOM issue, the worker will be restarted automatically and retry the job, but this will slow down your workflow. You could limit the memory or CPU available to Docker runtime or increase physical memory. Modify `--cpus` or `--memory` flags or in the Docker desktop app.

### Iris Sample Resizing

The size/resolution of the iris image will be rescaled for processing if out of range. When resized, the quality score might deviate from original input. For certain edge cases, the processing engine may fail to generate output. [BIQT-Iris](https://github.com/mitre/biqt-iris)
