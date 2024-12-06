# Stealthy LD_PRELOAD Rootkit

## Overview
This project demonstrates the creation of a Linux rootkit using the `LD_PRELOAD` environment variable. The rootkit hides a specific file (`/etc/ld.so.preload`) by intercepting and modifying the behavior of common system calls.

## Features
- Hides the file `/etc/ld.so.preload` from being accessed or listed.
- Overrides the following library functions:
  - `fopen`: Prevents opening the file directly.
  - `read`: Ensures the file cannot be read through file descriptors.
  - `readdir`: Hides the file from directory listings.

## How It Works
The rootkit uses the `LD_PRELOAD` environment variable to load a shared object (`.so` file) into a process's memory space. It overrides specific functions from the C standard library (`libc`) using `dlsym` to call the original implementation when necessary.
