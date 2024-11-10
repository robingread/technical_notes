tags: #linux 

To time-sync different computers on Linux you can use [`chrony`](https://chrony.tuxfamily.org/). Even if we are using `docker` containers, we setup `chrony` on bare-metal:

```bash
sudo apt install chrony
```

You can backup the initial config file:

```bash
sudo mv /etc/chrony/chrony.conf{,.default}
```

Populate a new `chrony.conf` with the following:
```bash
server 192.168.10.1 iburst prefer minpoll 0 maxpoll 5 maxdelay .1
server dyson.global.corp iburst
server 0.pool.ntp.org iburst
server 1.pool.ntp.org iburst
server 2.pool.ntp.org iburst
server 3.pool.ntp.org iburst
maxchange 60 1 -1
rtcsync
driftfile /var/lib/chrony/drift
logdir /var/log/chrony
log measurements statistics tracking
```

The first line is used to tell `chrony` to get the time from a specific IP address.

Once set, restart `chronyd`:

```bash
sudo systemctl restart chrony.service
```

This should start syncing automatically, but you can use the following to check and get some statistics on the setup:

```bash
chronyc sources
chronyc sourcestats
```

You check that that you can see an [NTP](https://en.wikipedia.org/wiki/Network_Time_Protocol) server by running:

```bash
sudo apt install ntpdate
ntpdate -d 192.168.10.1
```
Here we assume that the sever is at 192.168.10.1.