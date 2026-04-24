---
title: "Switch Configurator (NAC)"
description: "Python-based network automation tool for pushing ISE/RADIUS/AAA configurations across large Cisco switch environments"
tags: ["python", "cisco", "networking", "automation", "ise"]
---

## Overview

Switch Configurator is a Python automation tool designed to push configurations across large-scale Cisco switch environments using Netmiko and `ciscoisesdk`. Originally build to enroll ISE, RADIUS, AAA and NAC configs.

## Features

- Config push via Netmiko across hundreds of switches based on config Files
- ISE ERS API integration for NAD creation or verification
- Config comparison and normalization logic
- Per-port verification and CSV reporting (device-level)
- `configparser`-based config files for flexible deployment
- Display and Confirmation Process on each step
