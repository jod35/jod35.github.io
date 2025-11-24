---
title: "My Linux Setup For Programming"
description: "People choose Linux over operating systems like macOS or Windows for several reasons, which can differ based on individual perspectives. For me, it comes down to three key factors"
pubDate: "Jul 6 2025"
tags: ["linux", "open-source", "i3wm", "tiling-window-managers"]
---

<iframe width="560" height="315" src="https://www.youtube.com/embed/uTDCuEbq1aU?si=NNO7Q59qmxxUtawX" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>

This video is one I made to show my Linux Setup for work and software development. 
<!-- more -->

## Why I use Linux?
People choose Linux over operating systems like macOS or Windows for several reasons, which can differ based on individual perspectives. For me, it comes down to three key factors:

- Open-source and cost-free
- Highly customizable
- Reliable and stable

### **Open-Source and Cost-Free**  
   Linux is free and open-source software (FOSS), meaning its source code is publicly available, and users can download, use, modify, and distribute it without any licensing fees. Unlike Windows, which requires purchasing a license, or macOS, which is tied to Apple's proprietary hardware, Linux distributions (distros) like Ubuntu, Fedora, or Debian are available at no cost. This makes Linux accessible to individuals, businesses, and organizations with limited budgets.  
   The open-source nature also fosters a community-driven development model. Developers worldwide contribute to Linux, ensuring transparency, security, and continuous improvement. Users can inspect the code to verify it meets their needs or lacks malicious elements, which is not possible with proprietary systems like Windows or macOS. For those who value software freedom and want to avoid vendor lock-in, Linux’s open-source philosophy is a major draw.

### **Highly Customizable**  
   Linux offers unparalleled flexibility, allowing users to tailor the operating system to their specific needs and preferences. Unlike macOS or Windows, which have rigid interfaces and limited customization options, Linux provides a variety of desktop environments (e.g., GNOME, KDE Plasma, XFCE) and window managers (e.g., i3, Openbox) that cater to different workflows and aesthetic preferences. Users can modify everything from the look and feel of the interface to system-level functionality.  
   For advanced users, Linux’s command-line interface (CLI) and scripting capabilities enable deep system tweaks, automation, and optimization. Developers, for instance, can configure Linux to create highly efficient programming environments, while hobbyists can build lightweight systems for older hardware. This level of control is particularly appealing to power users, tech enthusiasts, and those who want a system that aligns perfectly with their workflow, something macOS and Windows cannot match due to their standardized, one-size-fits-all approach.

### **Reliable and Stable**  
   Linux is renowned for its stability and robustness, making it a preferred choice for servers, supercomputers, and critical infrastructure. Many Linux distros, such as CentOS or Debian Stable, are designed to run for years without requiring reboots, except for critical kernel updates. This reliability stems from Linux’s modular design and rigorous testing by the community or enterprise maintainers (e.g., Red Hat, Canonical).  
   Compared to Windows, which can suffer from slowdowns, bloatware, or unexpected updates that disrupt workflows, Linux systems are leaner and less prone to crashes. macOS is stable but tightly coupled to Apple’s ecosystem, limiting hardware choices and exposing users to planned obsolescence. Linux, by contrast, runs efficiently on a wide range of hardware, from low-end devices to high-performance machines, and its long-term support (LTS) releases ensure consistent performance over time. For users prioritizing dependability—whether for personal use, development, or enterprise applications—Linux’s stability is a significant advantage.

These factors combine to make Linux an attractive alternative for those who value cost savings, creative control, and a dependable computing experience. While macOS and Windows may suit users who prefer polished, out-of-the-box experiences, Linux appeals to those who want a system they can fully own and optimize.

## A tour of my Desktop
Here I will give you a tour of my Destktop showing you what I use daily.

## My Computer
I use an HP ProBook 440 G4 equipped with 16GB of RAM, a 256GB SSD, and an additional 1TB HDD for extra storage. It features a 7th-generation Intel i7 quad-core processor running at 3.1GHz, and I rely on integrated graphics without a dedicated GPU.

![Neofetch showing my computer specs](/neofetch.png)

## Window Manager & Theming

I use [**i3**](https://i3wm.org/) as my [window manager](https://en.wikipedia.org/wiki/Window_manager) for its simplicity and keyboard-driven workflow. My entire desktop is themed with the [**Dracula**](https://draculatheme.com/) color scheme, which I apply to i3, GTK, and terminal applications for a consistent look. For window transparency and effects, I run [**picom**](https://github.com/yshui/picom) as my compositor.

## Application Launcher

For quickly launching applications, I rely on [**rofi**](https://github.com/davatorium/rofi). It's lightweight, highly customizable, and fits perfectly with my Dracula-themed setup.

## Terminal & Tools

My terminal of choice is [**Terminator**](https://gnome-terminator.org/) because of its split panes and easy configuration. I use [**pyenv**](https://github.com/pyenv/pyenv) to manage multiple Python versions, which is essential for working on different projects.

## Development Utilities

- [**LazyDocker**](https://github.com/jesseduffield/lazydocker): A simple terminal UI for managing Docker containers and images.
- [**Git**](https://git-scm.com/downloads): For version control, integrated with my terminal and editors.
- [**VS Code**](https://code.visualstudio.com/) or [**Neovim**](https://neovim.io/): Depending on the project, I switch between these editors, both themed with Dracula.

This setup keeps my workflow efficient, visually cohesive, and highly customizable for programming on Linux.