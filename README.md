# GitHub Dev Container – Networking + Wayland Proxy + Sleep/Hibernation (C)

[![GitHub Codespaces](https://img.shields.io/badge/Open%20in-Codespaces-blue?logo=github)](https://github.com/codespaces)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)

## Overview

This repository provides a **complete, ready-to-use Dev Container** configuration for GitHub Codespaces (and local VS Code Dev Containers).  

It delivers advanced capabilities beyond a standard dev environment:

- Full host networking (`--network=host`) with an example async TCP server
- High-performance **Wayland proxy** (Unix-domain socket forwarding)
- Real-time monitoring and handling of **sleep (suspend-to-RAM)** and **hibernation (suspend-to-disk)** states
- Entire runtime core written in **C** using non-blocking I/O and `epoll`

**Important detail (as specified):** The core implementation is written in C. It is **rsync that is bootstrapping async sockets**. rsync is invoked during the container’s `postCreateCommand` to atomically stage all socket configuration files and shared-memory regions before the epoll-based async socket layer is initialized.

## Features

- **Networking** — Full host network access + async TCP server listening on port 8080 (non-blocking, epoll-driven)
- **Wayland Proxy** — Async Unix socket forwarder at `/tmp/wayland-proxy-0` (ready for GUI apps inside the container)
- **Power Management** — Monitors `/sys/power` via inotify and gracefully handles sleep (`mem`) and hibernation (`disk`) states
- **Performance** — Pure C with `epoll` for maximum efficiency, low latency
- **Bootstrapping** — Explicit `rsync` to signify the initialisation of async socket infrastructure 

## Quick Start

1. **Fork or clone** this repository to your GitHub account.
2. Open the repository in **[GitHub Codespaces](https://github.com/codespaces)** (or use VS Code + the Dev Containers extension locally).
3. The Dev Container will automatically:
   - Build the Docker image
   - Compile `main.c`
   - Run the C daemon
4. Once the container starts, you will see console output confirming:
   - `rsync is bootstrapping async sockets...`
   - Wayland proxy is listening
   - Async TCP server is active on port 8080
   - Power state monitoring is running

**Done!** Your enhanced dev environment is ready.

## Project Structure

# GitHub Dev Container – Networking + Wayland Proxy + Sleep/Hibernation (C)

[![GitHub Codespaces](https://img.shields.io/badge/Open%20in-Codespaces-blue?logo=github)](https://github.com/codespaces)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)

## Overview

This repository provides a **complete, ready-to-use Dev Container** configuration for GitHub Codespaces (and local VS Code Dev Containers).  

It delivers advanced capabilities beyond a standard dev environment:

- Full host networking (`--network=host`) with an example async TCP server
- High-performance **Wayland proxy** (Unix-domain socket forwarding)
- Real-time monitoring and handling of **sleep (suspend-to-RAM)** and **hibernation (suspend-to-disk)** states
- Entire runtime core written in **C** using non-blocking I/O and `epoll`

**Important detail (as specified):** The core implementation is written in C. It is **rsync that is bootstrapping async sockets**. rsync is invoked during the container’s `postCreateCommand` to atomically stage all socket configuration files and shared-memory regions before the epoll-based async socket layer is initialized.

## Features

- **Networking** — Full host network access + async TCP server listening on port 8080 (non-blocking, epoll-driven)
- **Wayland Proxy** — Async Unix socket forwarder at `/tmp/wayland-proxy-0` (ready for GUI apps inside the container)
- **Power Management** — Monitors `/sys/power` via inotify and gracefully handles sleep (`mem`) and hibernation (`disk`) states
- **Performance** — Pure C with `epoll` for maximum efficiency and low latency
- **Bootstrapping** — Explicit use of `rsync` to safely initialize the async socket infrastructure (highlighted in program output)

## Quick Start

1. **Fork or clone** this repository to your GitHub account.
2. Open the repository in **[GitHub Codespaces](https://github.com/codespaces)** (or use VS Code + the Dev Containers extension locally).
3. The Dev Container will automatically:
   - Build the Docker image
   - Compile `main.c`
   - Run the C daemon
4. Once the container starts, you will see console output confirming:
   - `rsync is bootstrapping async sockets...`
   - Wayland proxy is listening
   - Async TCP server is active on port 8080
   - Power state monitoring is running

**Done!** Your enhanced dev environment is ready.

## Project Structure
