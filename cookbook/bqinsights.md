---
layout: default
title: Desktop App
parent: Cookbooks
nav_order: 2
---

<img alt="GitHub Release" src="https://img.shields.io/github/v/release/Open-Source-Biometric-Quality-Framework/bqInsights">
<img alt="GitHub Release Date" src="https://img.shields.io/github/release-date/Open-Source-Biometric-Quality-Framework/bqInsights">
<img alt="GitHub issues" src="https://img.shields.io/github/issues-raw/Open-Source-Biometric-Quality-Framework/bqInsights">
<img alt="GitHub commit activity" src="https://img.shields.io/github/commit-activity/m/Open-Source-Biometric-Quality-Framework/bqInsights">
<img alt="GitHub Downloads (all assets, all releases)" src="https://img.shields.io/github/downloads/Open-Source-Biometric-Quality-Framework/bqInsights/total">
<img alt="GitHub" src="https://img.shields.io/github/license/Open-Source-Biometric-Quality-Framework/bqInsights">

<details open markdown="block">
  <summary>
    Table of contents
  </summary>
  {: .text-delta }
- TOC
{:toc}
</details>

---

> This project is in beta for early access and is not recommended for production environments.

## Prerequisites

You can run the application on Windows, macOS, and Linux. Both ARM and x86 platforms are supported.

- [ ] [Git](https://git-scm.com/install/) (to sync source code)
- [ ] [Python](https://www.python.org/downloads/) (to provide application runtime, Windows only)
- [ ] [Node.js](https://nodejs.org/en/download) (to provide application runtime)
- [ ] [Bun](https://bun.com/get) (to provide application runtime)
- [ ] [Visual Studio](https://visualstudio.microsoft.com/downloads/) (use Desktop development with C++ workload, Windows only)
- [ ] [Docker](https://docs.docker.com/get-started/get-docker/) (to host data processing backend)
- [ ] [Ollama](https://ollama.com/download) (to provide local AI capability)

### Start AI service

You could use Ollama desktop app or run the AI server via docker container:

```sh
docker run -d --gpus=all -v ollama:/root/.ollama -p 11434:11434 --name ollama ollama/ollama
```

> You don’t have to use Ollama for hosting LLM. You can bring your own AI model—the application supports OpenAI- or Claude-compatible models, hosted locally or remotely.

## Set Up

- Find a location on your computer, open a terminal and run:

```sh
git clone https://github.com/Open-Source-Biometric-Quality-Framework/bqInsights.git
```

This will pull the source code to the current directory.

- Go into the project directory (`/bqInsights`) and run the commands below to build and install the project:

```sh
bun install
```

```sh
bun run build:openbq
```

- Once all dependencies properly configured, run the following command to start up the application:

```sh
bun run dev:openbq
```

## Update

- Pull latest changes from the source code repository:

```sh
git pull
```

## Uninstall

- Simply remove the project directory.