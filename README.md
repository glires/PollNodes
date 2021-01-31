# PollNodes

A Perl script, which periodically summarizes Linux server stats and shows them at a WWW site

----

## Synopsis
```
sudo pollnodes [-c center_host] [-h] [-l data_path] [-n] [-o] \
                 [-p localhost_port] [-q httpd_scp_port] \
                 [-r] [-s seconds] [-t httpd_target] [-v]
```
----

## Author

Coded by Kohji OKAMURA, Ph.D.

----

## Usage
```
$ sudo pollnodes -h
$ sudo getenforce	# SELinux should be disabled or permissive
$ sudo mkdir /var/pollnodes
$ sudo chmod go+rx /var/pollnodes/
$ sudo chown root:root /usr/local/bin/pollnodes
$ sudo ssh -l root griffith	# login the center host without passwd
$ sudo systemctl enable pollnodes	# daemon
$ sudo systemctl start pollnodes
$ sudo systemctl status pollnodes
$ sudo cat /etc/systemd/system/pollnodes.service
[Unit]
Description = collect and send node information periodically
After = network.target
[Service]
ExecStart = /usr/local/bin/pollnodes -c 10.11.12.13 \
                   -l /net/pollnodes -s 512
Restart = always
RestartSec = 16
Type = simple
StandardOutput = syslog
StandardError = syslog
[Install]
WantedBy = multi-user.target
```
----
