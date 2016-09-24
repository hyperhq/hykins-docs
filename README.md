Documents about integration of Hyper_ and Jenkins
=================================================

<!-- TOC depthFrom:1 depthTo:6 withLinks:1 updateOnSave:1 orderedList:0 -->

- [Introduction](#introduction)
- [Comparison](#comparison)
- [Usage](#usage)
	- [Prerequisites](#prerequisites)
	- [Run Jenkins Server in Hyper_ Cloud](#run-jenkins-server-in-hyper-cloud)
	- [Use customized image](#use-customized-image)
- [User Cases](#user-cases)

<!-- /TOC -->

# Introduction

[`Hyper_ Slaves Plugin`](https://github.com/jenkinsci/hyper-slaves-plugin) allows to execute a jenkins job inside Hyper_ container.

When Jenkins Master build a Jenkins job, it will start a `Hyper_ container` as a `Jenkins Slave node`, The Slave agent connects to Jenkins Master via `JNLP`.

The Hyper_ container will be destroyed after Jenkins job is finished.


# Comparison

Compare `Hyper_ Slaves Plugin` with `Amazon EC2 Plugin` and `DigitalOcean Plugin`.

`Hyper_ Slaves Plugin` can optimize performance and cost:  
- Startup Slave Node faster: `3~10` seconds
- Cheaper to run Hyper_ container: per `second` billing

To view the detail, please click [here](compare/README.md).

# Usage


## Prerequisites

1. Jenkins Server `2.7.x LTS`:
  - install tool: [`hyper client`](https://docs.hyper.sh/GettingStarted/install.html)
  - install plugin: [`Hyper_ Slaves Plugin`](https://wiki.jenkins-ci.org/display/JENKINS/Hyper_+Slaves+Plugin)
  - assign `IP Address`: Jenkins Server requires a public IP, so Jenkins Agent can connect to it.
2. Hyper_ Credential: [Generate API Credential]( https://docs.hyper.sh/GettingStarted/generate_api_credential.html)
3. Docker image: (build environment)
  - [`jenkinsci/slave`](https://hub.docker.com/r/jenkinsci/slave/)
  - [`oracle/openjdk:8`](https://hub.docker.com/r/oracle/openjdk/)
  - [`openjdk:8-jdk`](https://hub.docker.com/_/openjdk/)



## Run Jenkins Server in Hyper_ Cloud

[`hyperhq/hyperkins`](https://github.com/hyperhq/jenkins-image-hyperkins) is a pre-built docker image,

It's based on [`jenkins:2.7.4`](https://hub.docker.com/_/jenkins/), the following contents has been installed:  
- [`hyper client`](https://docs.hyper.sh/GettingStarted/install.html)
- [`Hyper_ Slaves Plugin`](https://wiki.jenkins-ci.org/display/JENKINS/Hyper_+Slaves+Plugin)

To Run Jenkins Server in Hyper_ Cloud, please click [here](https://github.com/hyperhq/jenkins-image-hyperkins#quickstart).

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
