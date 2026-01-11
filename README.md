# DMARC Engine Builder

This repository is an automated **CI/CD Controller** for our email security infrastructure. 

## Use Case
We use this to build and maintain a private, audited version of the `parsedmarc` engine. Instead of relying on 3rd-party Docker Hub images that may become deprecated or insecure, this repository:
1. Fetches the latest stable source code from the official `domainaware/parsedmarc` project.
2. Builds a Docker image using GitHub Actions.
3. Publishes the image to our private **GitHub Container Registry (GHCR)**.

## Infrastructure Integration
- **Registry:** `ghcr.io/${{ github.repository_owner }}/parsedmarc:latest`
- **Deployment:** Managed via **Coolify** on our production monitoring server.
- **Reporting:** Processes DMARC (RUA/RUF) and TLS-RPT reports into Elasticsearch for Grafana visualization.

## How to Trigger
- The build runs automatically every Sunday at midnight.
- To force a build (e.g., after a security update), go to the **Actions** tab and click **Run workflow**.
