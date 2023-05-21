# Mini Project <!-- omit in toc -->

Author: **Le Minh Duc**

## Table of Contents <!-- omit in toc -->

- [0. Requirements](#0-requirements)
- [1. Developing a Simple 3-Tier Web Application](#1-developing-a-simple-3-tier-web-application)
- [2. Continuous Integration](#2-continuous-integration)
- [3. Continuous Delivery](#3-continuous-delivery)
- [4. Monitoring](#4-monitoring)
- [5. Logging](#5-logging)
- [6. References](#6-references)

## 0. Requirements

- To see the requirements in Vietnamese, please visit [here](./assets/requirements.pdf).

## 1. Developing a Simple 3-Tier Web Application

- Dockerfile for each service:
  - db: None
  - [api](./app/api/Dockerfile)
  - [web](./app/web/Dockerfile)
- Output of the `docker build` command for each service:
  - db: None
  - [api](./app/api_build.log)

  ```shell
  docker build --no-cache -t duclm278/api api 2>&1 | tee api_build.log
  ```

  - [web](./app/web_build.log)

  ```shell
  docker build --no-cache -t duclm278/web web --build-arg "VITE_APP_BASE_URL=http://178.128.124.152:5000" 2>&1 | tee web_build.log
  ```

  - Since static files are needed for the web service, the API endpoint must be bundled into it. Therefore, I pass `VITE_APP_BASE_URL` as the build argument to the `docker build` command.

  - Techniques I used have already been documented in the practice 1, containerization.
- Output of the `docker history` command for each service:
  - db: None
  - [api](./app/api_history.log)

  ```shell
  docker history duclm278/api 2>&1 | tee api_history.log
  ```

  - [web](./app/web_history.log)

  ```shell
  docker history duclm278/web 2>&1 | tee web_history.log
  ```

- Techniques I used to optimize the images have already been documented in the practice 1, containerization.

## 2. Continuous Integration

- GitHub Action CI workflow: [here](./.github/workflows/ci.yml)

- Output log of the CI workflow: [here](./.github/workflows/ci.log)

- Demo:

  ![img](./assets/ci_demo.png)

## 3. Continuous Delivery

- GitHub Action release workflow: [here](./.github/workflows/ci.yml)

## 4. Monitoring

## 5. Logging

## 6. References

[1] [Basic Blog App Built in Flask](https://github.com/pallets/flask/tree/2.3.2/examples/tutorial)

[2] [Unit Testing Pymongo Flask Applications With Mongomock](https://github.com/reritom/Flask-PyMongo-Unittest-Guide)

[3] [Docker-Compose Build Environment Variable](https://stackoverflow.com/questions/52429984/docker-compose-build-environment-variable)

[4] [Docker-Compose --Scale X nginx.conf Configuration](https://stackoverflow.com/questions/50203408/docker-compose-scale-x-nginx-conf-configuration)

[5] [Dynamic Nginx Configuration for Docker With Python](https://www.ameyalokare.com/docker/2017/09/27/nginx-dynamic-upstreams-docker.html)

[6] [GitHub Actions Starter Workflows](https://github.com/actions/starter-workflows)

[7] [Sample Workflows by Mentor `haminhcong`](https://github.com/haminhcong/demo-ci-cd-netbox)

[8] [How to Configure Prometheus Server as a Remote-Write Receiver](https://faun.pub/how-to-configure-prometheus-server-as-a-remote-write-receiver-4c8e265011c2)

[9] [Cannot Unmarshal http_listen_address and http_listen_port](https://github.com/grafana/agent/issues/1935)

[10] [Enabling the Remote Write Receiver Endpoint](https://prometheus.io/docs/prometheus/latest/storage/#overview)

[11] [Connect to the Localhost of the Machine From Inside of a Docker Container](https://stackoverflow.com/questions/24319662/from-inside-of-a-docker-container-how-do-i-connect-to-the-localhost-of-the-mach)

[12] [Exploring Default Docker Networking Part 1](https://blogs.cisco.com/learning/exploring-default-docker-networking-part-1)

[13] [Sample DockProm by Mentor `vanduc95`](https://github.com/vanduc95/dockprom)

[14] [Sample EFK Stack by Mentor `quynhvuongg`](https://github.com/quynhvuongg/EFK-stack)
