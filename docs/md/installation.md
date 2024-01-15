# swd-services

## Installation

In order to install **swd-services** with apt (Advanced Packaging Tool), you need to add ez-Wheel repository to your Apt sources configuration file as sudo in: */etc/apt/sources.list*. Type the following command:

```shell
echo "deb http://packages.ez-wheel.com:8081/ubuntu $(lsb_release -cs) main" | sudo tee -a /etc/apt/sources.list
```

Then, download and add the GPG key. Type the following command:

```shell
wget -qO - http://packages.ez-wheel.com:8081/archive.key | sudo apt-key add -
```

Now, you should be able to install the package using apt:

```shell
sudo apt update && sudo apt install swd-services
```

The libraries are now installed in your linux environment in */opt/ezw/usr/* directory.
