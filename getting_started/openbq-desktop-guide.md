---
layout: default
title: OpenBQ Desktop
parent: Getting Started
nav_order: 2
---

# OpenBQ Desktop

[![GitHub Release](https://img.shields.io/github/v/release/Open-Source-Biometric-Quality-Framework/openbq-desktop-releases)](https://github.com/Open-Source-Biometric-Quality-Framework/openbq-desktop-releases/releases)

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
> 🖥️ **OpenBQ Desktop** is a local desktop application for biometric quality assessment — no data is ever sent to the internet.

## What is OpenBQ Desktop?

OpenBQ Desktop allows you to analyse a collection of biometric files — such as face images, fingerprints, iris scans, or voice recordings — and understand their quality. It produces visual charts and metrics that help you identify low-quality samples, spot systematic capture problems, and assess the overall health of your dataset.

---

## Prerequisites

Before installing or using OpenBQ Desktop, you will need the following software installed and running on your computer.

### Docker

Docker is required for OpenBQ Desktop to run its analysis pipeline.

**Windows and Mac:**
1. Go to [https://www.docker.com/products/docker-desktop](https://www.docker.com/products/docker-desktop)
2. Download **Docker Desktop** for your operating system
3. Run the installer and follow the prompts
4. Once installed, open **Docker Desktop** from your applications or Start menu
5. Wait for the status indicator to turn green — this means Docker is running

{: .note }
> You must have Docker Desktop **open and running** before launching OpenBQ Desktop. If you see a message saying "Docker is not running" in the app, open Docker Desktop and wait for it to start, then relaunch OpenBQ Desktop.

**Linux:**
Follow the [official Docker Engine installation guide](https://docs.docker.com/engine/install/) for your distribution.

---

### Ollama (for AI features)

Ollama is required to use the built-in AI assistant. It runs an AI model entirely on your own computer — no data is sent externally.

1. Go to [https://ollama.com/download](https://ollama.com/download)
2. Download and install Ollama for your operating system
3. Once installed, open a terminal and run:

```sh
ollama pull llama3.1
```

This downloads a local AI model (this may take a few minutes depending on your internet connection). You only need to do this once.

{: .note }
> Ollama is optional. If you prefer, you can use OpenAI or Claude as your AI provider instead — see [AI Settings](#ai-settings) below. If you don't need AI features at all, you can skip this step.

---

## Installation

Download the latest release of OpenBQ Desktop from the [releases page](https://github.com/Open-Source-Biometric-Quality-Framework/openbq-desktop-releases/releases).

| Platform | File to download |
|----------|-----------------|
| Windows  | `.exe` portable installer |
| macOS    | `.dmg` disk image |
| Linux    | `.deb` package |

**Windows:** Run the downloaded `.exe` file.

**macOS:** Open the `.dmg` file, drag **OpenBQ** to your Applications folder, then double-click to open. If macOS says the app can't be opened, right-click the app icon and choose **Open**, then confirm in the dialog.

**Linux:** Install the `.deb` package with:

```sh
sudo dpkg -i openbq-desktop_*.deb
```

---

## Getting Started

### Loading Your Data

There are several ways to open a folder of biometric files:

- **Menu bar:** Click **File → Open**
- **Button:** Click **Open Directory** in the left-hand panel and browse to your folder
- **Drag and drop:** Drag a folder from your file explorer onto the app window
- **Recent items:** Previously opened folders appear in the left panel — click any to reopen

Once a folder is selected, the app will display how many files were found.

### Running an Analysis

After opening a folder, select your modality and quality algorithm, then click the **Start Analysis** button in the left panel. The app will begin processing your files.

A progress indicator will appear while the analysis runs. Depending on the number of files, this may take anywhere from a few seconds to several minutes.

Click **Cancel** at any time to stop.

{: .note }
> The first time OpenBQ Desktop opens, it may take a few minutes to initialise. This is normal — it is downloading and setting up the analysis (bqCore) container. This only happens once.

### Configuring the clusters

In order for OpenBQ Desktop to cluster your results you must choose your required Cluster Sensitivity. Once selected click **Apply**, your results will be clustered based on the selected setting.

### Understanding the Results

Once complete, charts and quality metrics will appear in the main area of the screen. Use these to identify:

- **Outliers** — individual files significantly lower quality than the rest
- **Clusters** — groups of similar files, useful for spotting capture issues
- **Overall dataset health** — whether your collection is suitable for its intended use

Click on individual data points in the charts to see more detail about specific samples.

---

## AI Settings

Click the **⚙ Settings** icon in the top-right toolbar to open Settings and configure the AI assistant.

| Provider | Description |
|----------|-------------|
| **Local AI** | Runs entirely on your computer using Ollama. No data leaves your machine. Recommended for sensitive data. |
| **OpenAI** | Uses ChatGPT. Requires an OpenAI API key. |
| **Claude** | Uses Anthropic's Claude. Requires a Claude API key. |
| **Apple Intelligence** | macOS only. Uses Apple's built-in on-device AI. |

{: .highlight }
> 🔒 **Local AI** is recommended when working with sensitive biometric data, as no information is sent externally.

### Focus Instructions

**Optional:** You can give the AI specific guidance on what to look for during analysis. In Settings, click **+ Add** under **Focus instructions** to create a named instruction set, then type your instructions — for example:

> "Flag any images where lighting is uneven or the subject is not centred."

Select the instruction set you want active before running an analysis.

### AI Summary

OpenBQ Desktop can provide a summary report of the biometric quality results, click the **AI Summary** button and wait for a omprehensive summary report to be generated.

### Cluster Labels

OpenBQ Desktop can provide labl all of your clusters, click the **AI Label Clusters** button and wait for a omprehensive summary report to be generated.

---

## Settings Reference

| Setting | Description |
|---------|-------------|
| AI provider | Choose between Local AI, OpenAI, Claude, or Apple Intelligence |
| Focus instructions | Named instruction sets to guide AI analysis |
| Dark mode | Toggle between light and dark appearance |
| Clear analysis cache | Force a fresh re-analysis next time |

---

## FAQ

**Is my biometric data shared with anyone?**
No. All processing runs locally on your computer. Biometric data is never uploaded or shared externally.

**What biometric types are supported?**
Face images, fingerprints, iris scans, and voice recordings. Available metrics depend on which OpenBQ modules are enabled in your version.

**Docker is not running — what do I do?**
Open Docker Desktop from your Start menu or Applications folder and wait until the status indicator turns green, then relaunch OpenBQ Desktop.

**Results look the same even after I updated my files.**
Go to **Settings** and click **Clear Analysis Cache**, then run the analysis again.

**The AI isn't responding or gives errors.**
Check that your selected AI provider is configured correctly in Settings. For Local AI, ensure Ollama is installed and that you have pulled a model (e.g. `ollama pull llama3.1`). For OpenAI or Claude, verify your API key is entered correctly.

---

## Support

For further help, click the **? Help** button in the app and use the support email link.

More information is available at [https://openbq.io](https://openbq.io).
