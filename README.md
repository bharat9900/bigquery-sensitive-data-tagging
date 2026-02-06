# 🔒 Automated BigQuery Sensitive Column Tagging

**From Discovery to Lockdown**: Automating the tagging of sensitive columns in BigQuery using Sensitive Data Protection (SDP) and IAM Data Governance Tags.

---

## 📖 Overview
This solution bridges the gap between **Google Cloud Sensitive Data Protection (SDP)** and **BigQuery IAM Data Governance**. 

It works in two stages:
1.  **Discovery**: SDP scans your data and saves the "Sensitivity Score" to a BigQuery profile table.
2.  **Enforcement**: This notebook reads those scores and automatically applies the corresponding **prescriptive IAM Tags** to your BigQuery columns.

---

## 🚀 How to Run

### Step 1: Prerequisites
Before running the automation, ensure you have the following:
*   A Google Cloud Project with billing enabled.
*   **Permissions**:
    *   `roles/bigquery.admin` or `roles/bigquery.dataOwner` (to apply tags).
    *   `roles/dlp.user` (to run scans).
    *   `roles/resourcemanager.tagAdmin` (to create IAM tags).

### Step 2: Configure Discovery Scan (SDP)
You must first have SDP findings saved to BigQuery.
1.  Go to **[Sensitive Data Protection > Discovery](https://console.cloud.google.com/security/sensitive-data-protection/discovery)**.
2.  Create a **New Scan Configuration** for **BigQuery**.
3.  **Critical**: In the "Actions" step, select **"Save data profile to BigQuery"**.
    *   Let Google create the table for you.
    *   **Note down** the `Project ID`, `Dataset ID`, and `Table ID` of this profile table.

### Step 3: Create IAM Data Governance Tags
Define the tags you want to apply.
1.  Go to **[IAM & Admin > Tags](https://console.cloud.google.com/iam-admin/tags)**.
2.  Create a Tag Key (e.g., `data_sensitivity`).
3.  Add Values (e.g., `High`, `Medium`, `Low`).
4.  **Note down** the "namespaced" Key and Values (e.g., `123456789012/data_sensitivity` and `High`).

### Step 4: Run the Notebook
1.  **Open the Notebook**:
    *   Upload `automated_column_tagging.ipynb` to **[Vertex AI Workbench](https://console.cloud.google.com/vertex-ai/workbench)**.
    *   *Or* run it locally with JupyterLab (`gcloud auth application-default login` required).

2.  **Execute the Cells**:
    *   Run the **Configuration** cell: Enter the Source Table details (from Step 2).
    *   Run the **Tag Config** cell: Enter your Tag Keys/Values (from Step 3).
    *   Run the **Execution** cell: This will scan the findings and apply the tags to your columns.

---

## 📂 Repository Structure
*   `automated_column_tagging.ipynb`: The main automation tool.
*   `README.md`: This documentation.

## 👥 Authors
*   Bharat Tiwari
*   Varun Joshi
*   Vignesh Rajamani
