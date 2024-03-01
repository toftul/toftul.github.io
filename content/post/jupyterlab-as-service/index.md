---
title: "Jupyterlab as Service"
description:
date: 2024-03-01T11:12:30+11:00
image:
math: true
license: MIT
hidden: false
comments: true
draft: false
tags: ["linux"]
categories: []
---

# jupyter lab as service

## Systemd config

```systemd
# Place this in ~/.config/systemd/user
[Unit]
Description=Service to run JupyterLab in user space

[Service]
Type=simple
ExecStart=/home/ivan/.pyenv/shims/jupyter-lab --no-browser --port 8888
WorkingDirectory=/home/ivan/

[Install]
WantedBy=default.target

```

## Allow remote access

https://stackoverflow.com/a/54063685

Basically, you need to generate config file by

```shell
jupyter lab --generate-config
```

and then add/uncomment these lines in `~/.jupyter/jupyter_lab_config.py`:

```python
# Configuration file for lab.

c = get_config()  # noqa

## Set the Access-Control-Allow-Origin header
#
#          Use '*' to allow any origin to access your server.
#
#          Takes precedence over allow_origin_pat.
#  Default: ''
c.ServerApp.allow_origin = "*"


## The IP address the Jupyter server will listen on.
#  Default: 'localhost'
c.ServerApp.ip = "0.0.0.0"

```

and also set password by

```shell
jupyter lab password
```
