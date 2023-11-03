# ElasticSearch High Availability Automation

![Elasticsearch Logo](https://play.vidyard.com/Gfs339uMBi1CVavZEjXVZ8.jpg)

This repository contains scripts and configuration files to automate the setup and management of a High Availability cluster for Elasticsearch. Here we are going to install Elasticsearch in the 3VMs, Kibana in 1 VM and Beats agent in 2 webserver VMs. In this Repository we are going to automate the following.
1. Java Installation in the 3 Elasticsearch VMs
2. Adding Elasticsearch repository to all the 6 VMs
3. Elasticsearch Installation and configuration in 3 VMs
4. Elasticsearch High Availabilty setup
5. Kibana Installation and Configuration in 1 VM
6. Installation and Configuration of webservers in 2 VMs
7. Install and configuration of Filebeat in the webserver VMs
8. Install and configuration of Metricbeat in the webserver VMs

## Table of Contents

- [Introduction](#introduction)
- [Features](#features)
- [Getting Started](#getting-started)
  - [Prerequisites](#prerequisites)
  - [Installation](#installation)
- [Usage](#usage)
- [Configuration](#configuration)

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

1. Add the SSL certificates in the ```files``` directory. i.e ```elastic-certificates.p12``` and ```elasticsearch-ca.pem``` files.
2. Add the Username and password for the Elasticsearch login in the ```vars/credentials.yml``` file.
3. Add the required variables in the ```vars/main.yml``` file.

### Prerequisites

Before you begin, ensure you have the following prerequisites:

- Linux-based operating system (e.g., Ubuntu)
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

- Modify the ```hosts.yml``` file to specify the target servers for ElasticSearch,Kibana and Beats agent nodes.
- Update the ```elasticsearch/templates/elasticsearch.yml``` file to configure ElasticSearch settings.
- Update the ```kibana/templates/kibana.yml``` file to configure Kibana settings.
- Update the ```filebeat/templates/filebeat.yml``` file to configure Filebeat settings.
- Update the ```metricbeat/templates/metricbeat.yml``` file to configure Metricbeat settings.

4. Run the automation script :
ElasticSearch-HA-Automation will automate the deployment of an HA ElasticSearch cluster based on your configuration.
```diff
ansible-playbook -i inventory/hosts.yml playbooks/deploy-elk-ha.yml
```
To install the webservers in the dedicated VMs and to install the Filebeat and Metricbeat in the same VMs run the below automation script.
```diff
ansible-playbook -i inventory/hosts.yml playbooks/deploy-beats.yml
```

## Usage
After following the installation steps, you will have a fully functional ElasticSearch High Availability cluster. You can interact with the cluster through the ElasticSearch REST API or by configuring your applications to use it as a backend search engine.

Example:

```diff
# Access the ElasticSearch cluster on a specific node
curl -X GET http://localhost:9200
```
For more information on how to use ElasticSearch, refer to the ElasticSearch documentation.

## Configuration
You can customize the ElasticSearch cluster configuration by modifying the ```elasticsearch.yml``` file. Ensure that you have reviewed the ElasticSearch documentation for available configuration options. To customize the Kibana configuration modify the ```kibana.yml``` file.