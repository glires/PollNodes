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
  $ sudo mv -i pollnodes /usr/local/bin/
  $ sudo chown root:root /usr/local/bin/pollnodes
  $ getenforce	# SELinux Enforcing
  $ sudo chcon -t bin_t /usr/local/bin/pollnodes	# SELinux
  $ sudo /usr/local/bin/pollnodes -v
  $ sudo /usr/local/bin/pollnodes -h
  $ sudo mkdir /var/pollnodes
  $ sudo chmod go+rx /var/pollnodes/
  $ sudo ssh -l alice 10.11.12.13	# login the center host without passwd
  $ sudo vi /etc/systemd/system/pollnodes.service
  $ sudo systemctl daemon-reload
  $ sudo systemctl enable pollnodes	# daemon
  $ systemctl is-enabled pollnodes
  $ sudo systemctl start pollnodes
  $ systemctl status pollnodes
  $ sudo cat /etc/systemd/system/pollnodes.service
  [Unit]
  Description = collect and send node information periodically
  After = network.target
  [Service]
  ExecStart = /usr/local/bin/pollnodes -c 10.11.12.13 \
                  -n -l /net/pollnodes -s 512
  Restart = always
  RestartSec = 16
  Type = simple
  StandardOutput = syslog
  StandardError = syslog
  [Install]
  WantedBy = multi-user.target
```
----
