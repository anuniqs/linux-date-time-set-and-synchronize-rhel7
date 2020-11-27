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


Configuring NTP —

Use the set-ntp argument to enable or disable automatic synchronization of your system clock with a remote server over the Network Time Protocol (NTP).

[root@localhost ~]# timedatectl set-ntp yes

[root@localhost ~]# timedatectl set-ntp no


Set hardware time to local timezone —

First Find out if your hardware clock is set to local timezone :

[root@localhost ~]# timedatectl | grep local

Set your hardware clock to local timezone :

[root@localhost ~]# timedatectl set-local-rtc 1

Set your hardware clock to coordinated universal time (UTC) :

[root@localhost ~]# timedatectl set-local-rtc 0


Synchronize Time on Installed Linux Operating Systems - 

Run the ntpdate -u <ntpserver> command to update the machine clock.

For example, ntpdate -u ntp-time.for.mydomain.

Open the /etc/ntp.conf file and add the NTP servers used in your environment.

You can add multiple NTP servers similar to these examples.

server ntp-time.for.mydomain

server otherntp.server.org

server ntp.research.gov

Run the service ntpd start command to start the NTP service and implement you configuration changes.
