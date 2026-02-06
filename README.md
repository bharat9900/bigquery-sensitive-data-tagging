# Automated BigQuery Sensitive Column Tagging

From Discovery to Lockdown: Automating tagging of sensitive columns in BigQuery.

## Overview
This repository contains a reusable solution to automate the classification and protection of sensitive data in BigQuery. It leverages:
1. **Sensitive Data Protection (SDP)**: To discover sensitive data (PII, financial info, etc.).
2. **IAM Data Governance Tags**: To classify columns based on sensitivity.
3. **Automation Script**: A Python script (provided in the notebook) to bridge the gap between discovery and enforcement.

## Contents
- `automated_column_tagging.ipynb`: A comprehensive Jupyter Notebook that guides you through the entire process, from setting up SDP scans to running the automation script.

## Quick Start
1. Open `automated_column_tagging.ipynb` in Vertex AI Workbench or your local Jupyter environment.
2. Follow the "Prerequisites" and "Discovery" sections to set up your environment.
3. Run the "Automated Tagging Code" cells to apply tags to your BigQuery columns.

## Authors
- Bharat Tiwari
- Varun Joshi
- Vignesh Rajamani
