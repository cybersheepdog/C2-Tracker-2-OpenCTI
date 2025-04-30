# C2-Tracker to OpenCTI
[![Build Status](https://img.shields.io/badge/platform-Windows%20%7C%20Linux-blue.svg)](https://shields.io/)
![Maintenance](https://img.shields.io/maintenance/yes/2025.svg?style=flat-square)
[![GitHub last commit](https://img.shields.io/github/last-commit/cybersheepdog/C2-Tracker-2-OpenCTI.svg?style=flat-square)](https://github.com/cybersheepdog/C2-Tracker-2-OpenCTI/commit/master)
![GitHub](https://img.shields.io/github/license/cybersheepdog/C2-Tracker-2-OpenCTI)

Ingest data [C2 Tracker Data](https://github.com/montysecurity/C2-Tracker/tree/main/data) into an [OpenCTI](https://github.com/OpenCTI-Platform/opencti) instance.

## Features

- Import C2 Tracker IOCs as Indicators in OpenCTI in STIX format
- Intelligently manage Indicators
    - Does not delete indicators if they are no longer seen in C2 Tracker.  Instead it is expected that       indicator decay rules are in place.
    - Use "c2-tracker" label to avoid deleting unrelated IOCs
    - Creates additional labels based on the file names produced by C2 Tracker
    - Link indicators to MITRE tools and malware (requires [MITRE Connector](https://github.com/OpenCTI-Platform/connectors/tree/master/external-import/mitre))

## Install (Standalone Python)

Requires Python 3

1. Create a user with "Connector" & "Default" roles, take note of the Token that is made and put it in an environment variable called `OPENCTI_C2TRACKER_TOKEN`
2. Set environment variable `OPENCTI_URL`
3. Download the repo: `git clone https://github.com/cybersheepdog/C2-Tracker-2-OpenCTI.git'
4. Navigate to connector: `cd C2-Tracker-2-OpenCTI/`
5. Install packages: `pip3 install --upgrade pip && pip3 install requests pycti`
6. Run `
7. Set Cron Job or Service to run when OpenCTI starts up

## Purge Script

There is a script `purge.py` that is not executed by the main script. It solely exists to allow the operator to easily delete all of the indicators that were made by this connector. It relies on the label `c2-tracker` to identify those.
