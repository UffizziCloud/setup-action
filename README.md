# Setup Action

The Uffizzi Setup Action is a GitHub Action that facilitates the installation of the latest Uffizzi CLI Linux binary from the [Uffizzi CLI](https://github.com/UffizziCloud/uffizzi_cli) repository. This action enables users to easily set up the Uffizzi CLI binary in their workflows and subsequently utilize it for various tasks. By using this action, users can seamlessly integrate Uffizzi's capabilities into their development workflows, allowing them to manage Kubernetes clusters effortlessly.

## Overview

The Setup Action automates downloading and configuring the Uffizzi CLI binary. With this action, users can ensure that they are always using the latest version of the CLI, facilitating efficient management of Kubernetes clusters and Preview Environments. This action serves as a prerequisite for utilizing the [Uffizzi Cluster Action](https://github.com/UffizziCloud/cluster-action), which enables the creation and deletion of Uffizzi uClusters.

## Inputs

1. **release-tag:**
   - **Description:** Tag for the CLI release. Use "latest" to get the most recent release.
   - **Required:** Yes
   - **Default:** "latest"

2. **binary-name:**
   - **Description:** Name of the CLI binary.
   - **Required:** Yes
   - **Default:** "uffizzi-linux"

## Usage

You can incorporate the Setup Action into your GitHub Actions workflows using the following configuration in your workflow YAML file:

```yaml
name: Your Workflow Name

on: [push]

jobs:
  setup-uffizzi:
    runs-on: ubuntu-latest

    steps:
    - name: Checkout code
      uses: actions/checkout@v2

    - name: Setup Uffizzi CLI
      uses: UffizziCloud/setup-action@v1
      with:
        release-tag: ${{ github.event.inputs.release-tag }}  # Replace with the desired release tag
        binary-name: ${{ github.event.inputs.binary-name }}  # Replace with the desired binary name
```

## How It Works
The UffizziCloud Setup Action performs the following steps to set up the Uffizzi CLI binary:

1. Downloads the Uffizzi CLI binary from the specified release tag.
2. Makes the binary executable using the chmod command.

This action prepares the Uffizzi CLI binary for use in subsequent steps of your workflow.