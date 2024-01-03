# custom_ansible_roles

## For installing Prometheus Node Exporter on a Linux system.
## The provided steps are:

## Download Node Exporter:

``` wget https://github.com/prometheus/node_exporter/releases/download/v1.3.1/node_exporter-1.3.1.linux-amd64.tar.gz
```
This command uses wget to download the Node Exporter version 1.3.1 for Linux on AMD64 architecture from the specified URL.

## Extract the Tarball:

```
tar xvf node_exporter-1.3.1.linux-amd64.tar.gz
```
This command extracts the contents of the downloaded tarball.

## Navigate to the Node Exporter Directory:

``` cd node_exporter-1.3.1.linux-amd64 ```
This command changes the current working directory to the extracted Node Exporter directory.

## Copy Node Exporter Binary to /usr/local/bin:

``` sudo cp node_exporter /usr/local/bin ```
This command copies the Node Exporter binary to the /usr/local/bin directory, making it accessible system-wide.

## Create a Dedicated User for Node Exporter:

```sudo useradd --no-create-home --shell /bin/false node_exporter ```
This command creates a user named node_exporter with a disabled login shell for security purposes.

## Set Ownership for the Node Exporter Binary:

``` sudo chown node_exporter:node_exporter /usr/local/bin/node_exporter ```
This command changes the ownership of the Node Exporter binary to the newly created user and group (node_exporter:node_exporter).

## Create a Systemd Service File:

```sudo vi /etc/systemd/system/node_exporter.service ```
This command opens a text editor (in this case, vi) to create/edit a Systemd service file for Node Exporter. You should add the appropriate configuration for the service in this file.

## Reload Systemd Daemon:

``` sudo systemctl daemon-reload ```
This command reloads the Systemd daemon to pick up any changes made to service files.

## Start Node Exporter Service:

``` sudo systemctl start node_exporter ```
This command starts the Node Exporter service.

## Enable Node Exporter to Start on Boot:

``` sudo systemctl enable node_exporter ```
This command configures Node Exporter to start automatically at boot time.

Now, Node Exporter should be installed, configured, and running on your system. You can access its metrics at http://localhost:9100/metrics or configure Prometheus to scrape the metrics from this endpoint.
