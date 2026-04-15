---
title: "SNA Configurator"
date: 2025-01-01
description: "Python-based network automation tool for pushing ISE/RADIUS/AAA configurations across large Cisco switch environments"
tags: ["python", "cisco", "networking", "automation", "ise"]
---

## Overview

SNA Configurator is a Python automation tool designed to push ISE, RADIUS, AAA, and IPDT configurations across large-scale Cisco switch environments (~900 switches) using Netmiko and `ciscoisesdk`.

## Features

- Bulk config push via Netmiko across hundreds of switches
- ISE ERS API integration for endpoint and session queries
- Config comparison and normalization logic
- Per-port verification and dual CSV reporting (device-level + port-level)
- `configparser`-based config files for flexible deployment

## Source

[GitHub →](https://github.com/unit363)
