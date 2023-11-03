# ElasticSearch High Availability Automation

![Elasticsearch Logo](https://play.vidyard.com/Gfs339uMBi1CVavZEjXVZ8.jpg)

This repository contains scripts and configuration files to automate the setup and management of a High Availability cluster for Elasticsearch. In this Repository we are going to automate the following.
1. Java Installation
2. Elasticsearch Installation and configuration in dedicated VMs
3. Elasticsearch High Availabilty setup
4. Kibana Installation and Configuration in dedicated VM
5. Installation and Configuration of webservers in dedicated VMs
6. Install and configuration of Filebeat in the webservers VMs
7. Install and configuration of Metricbeat in the webservers VMs

## Table of Contents

- [Introduction](#introduction)
- [Features](#features)
- [Getting Started](#getting-started)
  - [Prerequisites](#prerequisites)
  - [Installation](#installation)
- [Usage](#usage)
- [Configuration](#configuration)
- [Contributing](#contributing)
- [License](#license)
- [Acknowledgments](#acknowledgments)

## Introduction

ElasticSearch is a powerful search engine used for various applications, including log and data analytics. To ensure high availability and fault tolerance, it's essential to set up an ElasticSearch cluster with multiple nodes. ElasticSearch-HA-Automation simplifies this process by automating the setup and management of an HA ElasticSearch cluster.

## Features

- Automated deployment of an ElasticSearch High Availability cluster.
- Supports configuration of multiple ElasticSearch nodes.
- Streamlines the setup process to save time and reduce errors.
- Ensures data redundancy and reliability.
- Provides a foundation for scalable ElasticSearch deployments.
- Automated deployment of Kibana to setup the dashboard
- Automated deployment of Filbeat to get the Logs from Webservers VMs
- Automated deployment of Metricbeat to get the Metrics from Webservers VMs

## Getting Started

Follow these steps to get started with ElasticSearch-HA-Automation.

### Prerequisites

Before you begin, ensure you have the following prerequisites:

- Linux-based operating system (e.g., Ubuntu, CentOS)
- Ansible installed on your local machine
- SSH access to target servers for ElasticSearch deployment

### Installation

1. Clone the repository:

```diff
git clone https://github.com/Adarsh-Suvarna/ElasticSearch-HA-Automation.git
```

2. Change to the project directory:

```diff
cd ElasticSearch-HA-Automation
```

3. Customize the configuration:

- Modify the ```hosts.yml``` file to specify the target servers for ElasticSearch nodes.
- Update the ```elasticsearch.yml``` file to configure ElasticSearch settings.
- Update the ```kibana.yml``` file to configure Kibana settings.
- Update the ```filebeat.yml``` file to configure Filebeat settings.
- Update the ```metricbeat.yml``` file to configure Metricbeat settings.

4. Run the automation script:
```diff
ansible-playbook -i inventory/hosts.yml playbooks/deploy-elk-ha.yml
```
ElasticSearch-HA-Automation will automate the deployment of an HA ElasticSearch cluster based on your configuration.

```diff
ansible-playbook -i inventory/hosts.yml playbooks/deploy-beats.yml
```
To install the webservers in the dedicated VMs. Also it will install and configures the Filebeat and Metricbeat in the same VMs.

## Usage
After following the installation steps, you will have a fully functional ElasticSearch High Availability cluster. You can interact with the cluster through the ElasticSearch REST API or by configuring your applications to use it as a backend search engine.

Example:

```diff
# Access the ElasticSearch cluster on a specific node
curl -X GET http://localhost:9200
```
For more information on how to use ElasticSearch, refer to the ElasticSearch documentation.

## Configuration
You can customize the ElasticSearch cluster configuration by modifying the ```elasticsearch.yml``` file. Ensure that you have reviewed the ElasticSearch documentation for available configuration options.

## Contributing
We welcome contributions to ElasticSearch-HA-Automation. To contribute:

1. Fork the repository.
2. Create a new branch for your feature or bug fix.
3. Make your changes and commit them with clear messages.
4. Push your branch to your fork.
5. Create a pull request to the main repository.
6. Please follow the Contributing Guidelines for more details.

## License
This project is licensed under the MIT License - see the LICENSE file for details.

## Acknowledgments
We'd like to express our gratitude to the open-source community and the ElasticSearch team for providing such a valuable tool. Special thanks to our contributors for their support and contributions to this project.