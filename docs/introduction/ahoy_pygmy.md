---
sidebar_position: 2
title: "Local Environment"
---


## Local environment setup - pygmy

1. Checkout this project repo and confirm the path is in Docker's file sharing config - https://docs.docker.com/docker-for-mac/#file-sharing

2. Make sure you don't have anything running on port 80 on the host machine (like a web server) then run `pygmy up`

3. Build and start the build images:

    ```bash
    ahoy up
    ```

4. Visit the new site @ `http://opc.docker.amazee.io`

* If any steps fail, you're safe to rerun from any point.
Starting again from the beginning will just reconfirm the changes.

5. To import the site config:

    ```bash
    ahoy cim
    ahoy drush cr
    ```