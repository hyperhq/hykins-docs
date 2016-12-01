Documents about integration of Hyper.sh and Jenkins
===================================================

<!-- TOC depthFrom:1 depthTo:6 withLinks:1 updateOnSave:1 orderedList:0 -->

- [Introduction](#introduction)
- [Comparison](#comparison)
- [Usage](#usage)
	- [Prerequisites](#prerequisites)
	- [Run Jenkins Server in Hyper.sh Cloud](#run-jenkins-server-in-hypersh-cloud)
	- [Use customized image](#use-customized-image)
- [User Cases](#user-cases)

<!-- /TOC -->

# Introduction

[`Hyper.sh Slaves Plugin`](https://github.com/jenkinsci/hyper-slaves-plugin) allows to execute a jenkins job inside Hyper.sh container.

When Jenkins Master build a Jenkins job, it will start a `Hyper.sh container` as a `Jenkins Slave node`, The Slave agent connects to Jenkins Master via `JNLP`.

The Hyper.sh container will be destroyed after Jenkins job is finished.


# Comparison

Compare `Hyper.sh Slaves Plugin` with `Amazon EC2 Plugin` and `DigitalOcean Plugin`.

`Hyper.sh Slaves Plugin` can optimize performance and cost:  
- Startup Slave Node faster: `3~10` seconds
- Cheaper to run Hyper.sh container: per `second` billing

To view the detail, please click [here](compare/README.md).

# Usage


## Prerequisites

1. Jenkins Server `2.7.4 LTS`/`2.19.3 LTS`:
  - install tool: [`hyper client`](https://docs.hyper.sh/GettingStarted/install.html)
  - install plugin: [`Hyper.sh Slaves Plugin`](https://wiki.jenkins-ci.org/display/JENKINS/Hyper_+Slaves+Plugin)
  - assign `IP Address`: Jenkins Server requires a public IP, so Jenkins Agent can connect to it.
2. Hyper.sh Credential: [Generate API Credential]( https://docs.hyper.sh/GettingStarted/generate_api_credential.html)
3. Docker image: (build environment)
  - [`jenkinsci/slave`](https://hub.docker.com/r/jenkinsci/slave/)
  - [`oracle/openjdk:8`](https://hub.docker.com/r/oracle/openjdk/)
  - [`openjdk:8-jdk`](https://hub.docker.com/_/openjdk/)



## Run Jenkins Server in Hyper.sh Cloud

[`hyperhq/hykins`](https://github.com/hyperhq/hykins) is a pre-built docker image,

It's based on [`jenkins`](https://hub.docker.com/_/jenkins/), the following contents has been installed:  
- [`hyper client`](https://docs.hyper.sh/GettingStarted/install.html)
- [`Hyper.sh Slaves Plugin`](https://wiki.jenkins-ci.org/display/JENKINS/Hyper_+Slaves+Plugin)

To Run Jenkins Server in Hyper.sh Cloud, please click [here](https://github.com/hyperhq/hykins#quickstart).

## Use customized image

Here are some examples:
- `hyperhq/jenkins-slave-centos`
  - based on centos:7.2.1511, [Dockerfile](https://github.com/hyperhq/jenkins-image-slave/blob/master/jenkins-slave-centos)
- `hyperhq/jenkins-slave-golang`
  - for build golang project [Dockerfile](https://github.com/hyperhq/jenkins-image-slave/tree/master/jenkins-slave-golang)
- `jenkins-slave-python`
  - for build python project [Dockerfile](https://github.com/hyperhq/jenkins-image-slave/tree/master/jenkins-slave-python)
- `jenkins-slave-php`
  - for build php project [Dockerfile](https://github.com/hyperhq/jenkins-image-slave/tree/master/jenkins-slave-php/base)

To find all example images, please see [this](https://hub.docker.com/search/?q=hyperhq%2Fjenkins-slave)

# User Cases

- [Build Github Pull Request](use-case/build-github-pull-request)
- [Call Remote Access API to trigger build](use-case/remote-access-api)
