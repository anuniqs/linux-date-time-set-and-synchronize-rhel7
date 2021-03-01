## Time and date set and synchronize on Redhat —

### Change the current date and time —

#### 1. To change the date, use the following syntax:

[root@localhost ~]# timedatectl set-time [YYYY-MM-DD]

#### 2. To change the current time, use the following syntax. Enter the hour by using a 24-hour clock.

[root@localhost ~]# timedatectl set-time [HH:MM:SS]

#### 3. To configure your system to maintain the clock in the local time, use the following command:

[root@localhost ~]# timedatectl set-local-rtc yes

#### 4. To configure your system to use UTC, use the following command:

[root@localhost ~]# timedatectl set-local-rtc no


### Change Time Zone — 

#### 1 -  List all the available timezones

[root@localhost ~]# timedatectl list-timezones

#### 2 - Locate the correct timezone you need that is in the Indian timezone and set the specific timezone.

[root@localhost ~]# tzselect

[root@localhost ~]# timedatectl set-timezone Asia/Kolkata


### 3 - Check status

[root@localhost ~]# timedatectl status


### Configuring NTP —

#### Use the set-ntp argument to enable or disable automatic synchronization of your system clock with a remote server over the Network Time Protocol (NTP).

[root@localhost ~]# timedatectl set-ntp yes

[root@localhost ~]# timedatectl set-ntp no


### Set hardware time to local timezone —

#### First Find out if your hardware clock is set to local timezone :

[root@localhost ~]# timedatectl | grep local

#### Set your hardware clock to local timezone :

[root@localhost ~]# timedatectl set-local-rtc 1

#### Set your hardware clock to coordinated universal time (UTC) :

[root@localhost ~]# timedatectl set-local-rtc 0


### Synchronize Time on Installed Linux Operating Systems — 

Run the `ntpdate -u <ntpserver>` command to update the machine clock.

For example, `ntpdate -u ntp-time.for.mydomain`

Open the `/etc/ntp.conf` file and add the NTP servers used in your environment.

You can add multiple NTP servers similar to these examples.

```
server ntp-time.for.mydomain

server otherntp.server.org

server ntp.research.gov

```

Run the `service ntpd start` command to start the NTP service and implement you configuration changes.


## Redefined —

### Installation —

[root@localhost ~]# rpm -qi ntp

[root@localhost ~]# yum install ntp

[root@localhost ~]# systemctl status ntpd.service

[root@localhost ~]# systemctl status ntpdate.service

[root@localhost ~]# nano /etc/ntp.conf

[root@localhost ~]# nano /etc/sysconfig/ntpd

[root@localhost ~]# nano /etc/sysconfig/ntpdate


[root@localhost ~]# timedatectl status

[root@localhost ~]# ntpdate pool.ntp.org

[root@localhost ~]# ntpq -p


### Set time zone  —

[root@localhost ~]# timedatectl status

```
      Local time: Mon 2021-01-04 12:04:02 IST
  Universal time: Mon 2021-01-04 06:34:02 UTC
        RTC time: Mon 2021-01-04 06:34:02
       Time zone: Asia/Kolkata (IST, +0530)
     NTP enabled: yes
NTP synchronized: yes
 RTC in local TZ: no
      DST active: n/a

```

[root@localhost ~]# timedatectl list-timezones

[root@localhost ~]# timedatectl list-timezones | grep Asia

```
Asia/Kolkata
```

[root@localhost ~]# timedatectl set-timezone Asia/Kolkata

[root@localhost ~]# timedatectl status

[root@localhost ~]# timedatectl set-timezone UTC

[root@localhost ~]# timedatectl status


### Sync with hardware clock (RTC in local TZ) — 

[root@localhost ~]# timedatectl set-local-rtc 1

[root@localhost ~]# timedatectl status


### Enable ntp server (NTP enabled) —

[root@localhost ~]# timedatectl set-ntp true

[root@localhost ~]# timedatectl set-ntp false

[root@localhost ~]# timedatectl status


### Automatic synchronization (NTP synchronized) —

[root@localhost ~]# timedatectl set-ntp yes

[root@localhost ~]# timedatectl set-ntp no

[root@localhost ~]# timedatectl status

.
  
**@ By — Anup Kumar Mondal**
