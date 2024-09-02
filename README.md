
# Kafka Cluster Deployment with Ansible

This repository contains an Ansible-based solution for deploying and managing a Kafka cluster with Zookeeper. It provides an automated and reproducible way to set up a highly available, fault-tolerant Kafka cluster, complete with Prometheus monitoring.

## Table of Contents

1. [Features](#features)
2. [Prerequisites](#prerequisites)
3. [Getting Started](#getting-started)
   - [Vagrant Environment](#vagrant-environment)
   - [Production Deployment](#production-deployment)
4. [Configuration](#configuration)
   - [Zookeeper](#zookeeper)
   - [Kafka](#kafka)
   - [Monitoring](#monitoring)
5. [Security Considerations](#security-considerations)
6. [Lessons Learned](#lessons-learned)
7. [Contributing](#contributing)
8. [License](#license)

## Features

- Automated deployment of a Kafka cluster with 3 Zookeeper nodes and 3 Kafka brokers
- Dynamic configuration of Kafka heap size during deployment
- Integrated Prometheus monitoring for Kafka and Zookeeper
- Support for various deployment environments (Vagrant, AWS, on-premises)
- Reusable and customizable Ansible roles and playbooks

## Prerequisites

- Ansible 2.9 or later
- Docker and Docker Compose
- Vagrant (for local testing)
- Access to the target deployment environment (Vagrant, AWS, on-premises)

## Getting Started

### Vagrant Environment

1. Clone the repository:

   ```bash
   git clone https://github.com/thenameisvikash/kafkacluseterplaybook.git
   cd kafkacluseterplaybook
   ```

2. Spin up the Vagrant environment:

   ```bash
   vagrant up
   ```

3. Deploy the Kafka cluster:

   ```bash
   ansible-playbook -i vagrant.yml deploy-kafka-cluster.yml
   ```

### Production Deployment

1. Clone the repository:

   ```bash
   git clone https://github.com/thenameisvikash/kafkacluseterplaybook.git
   cd kafkacluseterplaybook
   ```

2. Update the inventory file for your deployment environment (e.g., `inventory/aws.yml`, `inventory/onprem_keybased.yml`).

3. Deploy the Kafka cluster:

   ```bash
   ansible-playbook -i <inventory_file> deploy-kafka-cluster.yml
   ```

Replace `<inventory_file>` with the appropriate inventory file for your environment.

## Configuration

### Zookeeper

The Zookeeper configuration is defined in the `group_vars/all.yml` file. Key settings include:

- `zookeeper_data_dir`: Path for Zookeeper data
- `zookeeper_datalog_dir`: Path for Zookeeper data log
- `zookeeper_servers`: Definition of the Zookeeper ensemble

### Kafka

The Kafka configuration is also defined in the `group_vars/all.yml` file. Key settings include:

- `kafka_port`: Port used by Kafka brokers
- `kafka_log_segment_bytes`: Maximum size of a single log file
- `kafka_log_retention_bytes`: Maximum total size of log files
- `kafka_log_retention_ms`: Maximum retention time for log files

### Monitoring

The Ansible playbook sets up Prometheus monitoring for Kafka and Zookeeper. The Prometheus configuration is defined in the `roles/common/templates/prometheus-config.yml` file.

## Security Considerations

The provided setup includes basic security measures, such as:

- Enabling SSL/TLS encryption for Kafka
- Implementing SASL authentication
- Configuring ACLs to control access to topics

However, it's important to review and enhance the security measures based on your specific requirements and best practices.

## Lessons Learned

- Start with modest log retention settings and scale up as needed
- Monitor your Kafka cluster closely and set up alerts for critical events
- Security is an ongoing process, not a one-time setup
- Regularly backup Zookeeper data and test your restore process
- Document everything for easier maintenance and troubleshooting

## Contributing

Contributions are welcome! If you find any issues or have suggestions for improvements, please feel free to create a new issue or submit a pull request.

## License

This project is licensed under the [MIT License](LICENSE).
```
