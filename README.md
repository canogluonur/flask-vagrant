# Vagrant Nginx-Flask Setup

This project sets up an Ubuntu virtual machine using Vagrant, installs Nginx, Flask, and Docker Compose, and then starts a Flask application using Docker Compose.

## Requirements

- [Vagrant](https://www.vagrantup.com/downloads)
- [VirtualBox](https://www.virtualbox.org/wiki/Downloads)
- Internet connection

## Installation

1. Clone this repository to your local machine:

    ```bash
    git clone https://github.com/canogluonur/flask-vagrant.git
    cd flask-vagrant
    ```

2. Start the Vagrant virtual machine:

    ```bash
    vagrant up
    ```
    ```bash
    vagrant ssh
    ```
    ```bash
    curl http://localhost
    ```
    This command will create a virtual machine using the Vagrantfile and install the necessary software.

## Vagrantfile Explanation

### Box (Base Image)

```ruby
config.vm.box = "ubuntu/bionic64"
