---
sidebar_position: 1
slug: /
title: Introduction
---

# OPC Website

1

This template includes everything necessary to run on [Lagoon](https://www.github.com/uselagoon/lagoon) (in both the local development environments or on hosted Lagoon clusters.) This project manages website dependencies with [Composer](https://getcomposer.org/). It is based on the [original Drupal Composer Template](https://github.com/drupal-composer/drupal-project),

## Included Services

This project contains the following services:
* Drupal 10 (prerelease versions)
* PHP 8.1
* NGINX
* MariaDB 10.6

To find out more about the services, please visit the documentation at https://docs.lagoon.sh/lagoon

## Requirements

* [docker](https://docs.docker.com/install/)
* [pygmy](https://www.github.com/pygmystack/pygmy)


## Updating Drupal Core

Follow the steps below to update your core files. Scaffolding is managed by Drupal core. See the `assets/` directory for more information.

1. Run `composer update drupal/core-recommended drupal/core-dev-pinned --with-dependencies`

## FAQ

### What are the "TESTING" files in this repo?

These files are used by Github actions to run a basic suite of tests specific to this template.  They utilise the excellent [Leia](https://github.com/lando/leia) tool to generate a set of mocha-compatible tests. These tests can also be generated and run locally.
