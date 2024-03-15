# promtail

[![Source Code](https://img.shields.io/badge/github-source%20code-blue?logo=github&logoColor=white)](https://github.com/rolehippie/promtail)
[![General Workflow](https://github.com/rolehippie/promtail/actions/workflows/general.yml/badge.svg)](https://github.com/rolehippie/promtail/actions/workflows/general.yml)
[![Readme Workflow](https://github.com/rolehippie/promtail/actions/workflows/docs.yml/badge.svg)](https://github.com/rolehippie/promtail/actions/workflows/docs.yml)
[![Galaxy Workflow](https://github.com/rolehippie/promtail/actions/workflows/galaxy.yml/badge.svg)](https://github.com/rolehippie/promtail/actions/workflows/galaxy.yml)
[![License: Apache-2.0](https://img.shields.io/github/license/rolehippie/promtail)](https://github.com/rolehippie/promtail/blob/master/LICENSE)
[![Ansible Role](https://img.shields.io/badge/role-rolehippie.promtail-blue)](https://galaxy.ansible.com/rolehippie/promtail)

Ansible role to install and configure promtail.

## Sponsor

Building and improving this Ansible role have been sponsored by my current and previous employers like **[Cloudpunks GmbH](https://cloudpunks.de)** and **[Proact Deutschland GmbH](https://www.proact.eu)**.

## Table of content

- [Requirements](#requirements)
- [Default Variables](#default-variables)
  - [promtail_client_configs](#promtail_client_configs)
  - [promtail_cpu_shares](#promtail_cpu_shares)
  - [promtail_default_folders](#promtail_default_folders)
  - [promtail_default_labels](#promtail_default_labels)
  - [promtail_default_publish](#promtail_default_publish)
  - [promtail_default_volumes](#promtail_default_volumes)
  - [promtail_extra_folders](#promtail_extra_folders)
  - [promtail_extra_labels](#promtail_extra_labels)
  - [promtail_extra_publish](#promtail_extra_publish)
  - [promtail_extra_volumes](#promtail_extra_volumes)
  - [promtail_image](#promtail_image)
  - [promtail_memory_limit](#promtail_memory_limit)
  - [promtail_memory_soft_limit](#promtail_memory_soft_limit)
  - [promtail_memory_swap](#promtail_memory_swap)
  - [promtail_network](#promtail_network)
  - [promtail_number_of_cpus](#promtail_number_of_cpus)
  - [promtail_pull_image](#promtail_pull_image)
  - [promtail_scrape_configs](#promtail_scrape_configs)
  - [promtail_version](#promtail_version)
- [Discovered Tags](#discovered-tags)
- [Dependencies](#dependencies)
- [License](#license)
- [Author](#author)

---

## Requirements

- Minimum Ansible version: `2.10`

## Default Variables

### promtail_client_configs

List of client configs for Promtail

#### Default value

```YAML
promtail_client_configs: []
```

#### Example usage

```YAML
promtail_client_configs:
  - url: http://loki.example.com/promtail/api/v1/push
```

### promtail_cpu_shares

CPU shares with Docker deployment

#### Default value

```YAML
promtail_cpu_shares:
```

#### Example usage

```YAML
promtail_cpu_shares: '512'
```

### promtail_default_folders

List of default folders to create

#### Default value

```YAML
promtail_default_folders:
  - /etc/promtail
```

### promtail_default_labels

List of default labels to assign to docker

#### Default value

```YAML
promtail_default_labels: []
```

### promtail_default_publish

List of default port publishing for docker

#### Default value

```YAML
promtail_default_publish: []
```

#### Example usage

```YAML
promtail_default_publish:
  - 127.0.0.1:3100:3100
```

### promtail_default_volumes

List of default volumes to mount for docker

#### Default value

```YAML
promtail_default_volumes:
  - /etc/promtail:/etc/promtail
```

### promtail_extra_folders

List of extra folders to create

#### Default value

```YAML
promtail_extra_folders: []
```

#### Example usage

```YAML
promtail_extra_folders:
  - /path/to/host/folder1
  - /path/to/host/folder2
  - /path/to/host/folder3
```

### promtail_extra_labels

List of extra labels to assign to docker

#### Default value

```YAML
promtail_extra_labels: []
```

### promtail_extra_publish

List of extra port publishing for docker

#### Default value

```YAML
promtail_extra_publish: []
```

#### Example usage

```YAML
promtail_extra_publish:
  - 127.0.0.1:3100:3100
```

### promtail_extra_volumes

List of extra volumes to mount for docker

#### Default value

```YAML
promtail_extra_volumes: []
```

#### Example usage

```YAML
promtail_extra_volumes:
  - /path/to/host/folder1:/path/within/container1
  - /path/to/host/folder2:/path/within/container2
  - /path/to/host/folder3:/path/within/container3
```

### promtail_image

Docker image to use for deployment

#### Default value

```YAML
promtail_image: grafana/promtail:{{ promtail_version }}
```

### promtail_memory_limit

Memory limit with Docker deployment

#### Default value

```YAML
promtail_memory_limit:
```

#### Example usage

```YAML
promtail_memory_limit: 1024m
```

### promtail_memory_soft_limit

Soft memory limit with Docker deployment

#### Default value

```YAML
promtail_memory_soft_limit:
```

#### Example usage

```YAML
promtail_memory_soft_limit: 512m
```

### promtail_memory_swap

Swap usage with Docker deployment

#### Default value

```YAML
promtail_memory_swap:
```

#### Example usage

```YAML
promtail_memory_swap: 2048m
```

### promtail_network

Optional docker network to attach

#### Default value

```YAML
promtail_network:
```

### promtail_number_of_cpus

Number of CPUs with Docker deployment

#### Default value

```YAML
promtail_number_of_cpus:
```

#### Example usage

```YAML
promtail_number_of_cpus: '1.0'
```

### promtail_pull_image

Pull image as part of the tasks

#### Default value

```YAML
promtail_pull_image: true
```

### promtail_scrape_configs

List of scrape configs for Promtail

#### Default value

```YAML
promtail_scrape_configs: []
```

#### Example usage

```YAML
promtail_scrape_configs:
  - job_name: system
    static_configs:
      - targets:
          - localhost
        labels:
          job: varlogs
          __path__: /var/log/*log
```

### promtail_version

Version of the release to install

#### Default value

```YAML
promtail_version: 2.9.5
```

## Discovered Tags

**_promtail_**


## Dependencies

- [rolehippie.docker](https://github.com/rolehippie/docker)
- [community.docker](https://github.com/ansible-collections/community.docker)

## License

Apache-2.0

## Author

[Thomas Boerger](https://github.com/tboerger)
