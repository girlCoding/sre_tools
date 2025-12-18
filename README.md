# Welcome to girlCoding sre_tools Repo. 
# feedback is always welcomed.
# girlCoding@icloud.com
---

# sre_tools

A collection of lightweight, practical tools for Site Reliability Engineering.
This repository focuses on fast diagnostics, observability checks, incident response helpers, and automation scripts used to troubleshoot Linux systems, Kubernetes environments, cloud resources, and application performance issues.

## Overview

sre_tools is designed to give engineers quick, actionable insights into system health. These tools help reduce mean time to detect (MTTD) and mean time to resolve (MTTR) by automating common investigative steps.

## Features

* System resource diagnostics (CPU, memory, load, disk I/O, network)
* Kubernetes cluster checks
* Log collection helpers
* Process state analysis (D-state, zombies, runaway processes)
* Common service triage commands
* Customizable bash utilities for repeated troubleshooting workflows
* Hooks for exporting results into Slack, Grafana alerts, or incident tickets

## Tools Included

### system_diagnostic_folder/system_diagnostics.sh

Runs a full system health sweep including:

* top-like output for CPU, load, memory
* disk I/O metrics using iostat
* filesystem checks with df
* network socket summary
* process tree analysis
* dmesg and journalctl error highlights

### process_inspector_folder/process_inspector.sh

Identifies:

* D-state processes (uninterruptible sleep)
* Zombie processes
* High CPU or RSS processes
* Threads stuck in kernel I/O wait

### kube_health.sh

Performs Kubernetes-focused checks:

* pod status summary
* node resource snapshot
* crashlooping or pending pods
* event inspection
* optional namespace filters

### log_bundle.sh

Packages useful logs and telemetry into a single archive for incident response:

* system logs
* application logs (configurable paths)
* kube pod logs (if enabled)

## Requirements

* Linux-based system (Ubuntu, CentOS, RHEL, Amazon Linux, etc.)
* bash 4.x or newer
* Optional: kubectl, jq, iostat (sysstat), netstat or ss

## Installation

Clone the repository:

```
git clone https://github.com/USERNAME/sre_tools.git
cd sre_tools
```

Make scripts executable:

```
chmod +x *.sh
```

Run any tool:

```
./system_diagnostics.sh
```

## Usage Examples

Run diagnostics and save output:

```
./system_diagnostics.sh > diagnostics_$(date +%F).log
```

Check Kubernetes resources in a specific namespace:

```
./kube_health.sh -n gremlin
```

Inspect processes stuck in D-state:

```
./process_inspector.sh --dstate
```

Create an incident log bundle:

```
./log_bundle.sh --output incident_bundle.tar.gz
```

## Roadmap

* Add OpenTelemetry inline checks
* Add JSON export mode for dashboards
* Add cloud provider troubleshooting modules (AWS, GCP, Azure)
* Add a TUI-style curses interface
* Add automated remediation suggestions based on findings

## Contributing

Contributions, suggestions, and pull requests are welcome.
Please open an issue before submitting major changes.

## License

MIT License

---

If you want, I can turn this into a formatted README.md file with icons, badges, colorized code blocks, or a more technical tone.
