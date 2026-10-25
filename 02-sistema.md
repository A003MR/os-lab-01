# 02. Сведения о системе

### 1. Ядро и архитектура
Команды:
```bash
uname -a

Linux fedora 6.19.10-300.fc44.x86_64 #1 SMP PREEMPT_DYNAMIC Wed Mar 25 18:23:49 UTC 2026 x86_64 GNU/Linux 

cat /etc/os-release

NAME="Fedora Linux"
VERSION="44 (Workstation Edition)"
RELEASE_TYPE=stable
ID=fedora
VERSION_ID=44
VERSION_CODENAME=""
PRETTY_NAME="Fedora Linux 44 (Workstation Edition)"
ANSI_COLOR="0;38;2;60;110;180"
LOGO=fedora-logo-icon
CPE_NAME="cpe:/o:fedoraproject:fedora:44"
DEFAULT_HOSTNAME="fedora"
HOME_URL="https://fedoraproject.org/"
DOCUMENTATION_URL="https://docs.fedoraproject.org/en-US/fedora/f44/"
SUPPORT_URL="https://ask.fedoraproject.org/"
BUG_REPORT_URL="https://bugzilla.redhat.com/"
REDHAT_BUGZILLA_PRODUCT="Fedora"
REDHAT_BUGZILLA_PRODUCT_VERSION=44
REDHAT_SUPPORT_PRODUCT="Fedora"
REDHAT_SUPPORT_PRODUCT_VERSION=44
SUPPORT_END=2027-05-19
VARIANT="Workstation Edition"
VARIANT_ID=workstation

uptime

 05:49:59 up 17 min,  1 user,  load average: 0,00, 0,04, 0,09

whoami

admin

id

uid=1000(admin) gid=1000(admin) groups=1000(admin),10(wheel) context=unconfined_u:unconfined_r:unconfined_t:s0-s0:c0.c1023

lsblk

NAME   MAJ:MIN RM  SIZE RO TYPE MOUNTPOINTS
sda      8:0    0   40G  0 disk 
├─sda1   8:1    0  600M  0 part /boot/efi
├─sda2   8:2    0    1G  0 part /boot
├─sda3   8:3    0 36,4G  0 part /
└─sda4   8:4    0    2G  0 part [SWAP]
sr0     11:0    1 1024M  0 rom

df -h

Filesystem      Size  Used Avail Use% Mounted on
/dev/sda3        36G  5,1G   31G  15% /
/dev/sda2       974M  182M  725M  21% /boot
/dev/sda1       599M  8,0M  591M   2% /boot/efi

free -h

               total        used        free      shared  buff/cache   available
Mem:           3,8Gi       1,2Gi       2,1Gi        48Mi       643Mi       2,5Gi
Swap:          2,0Gi          0B       2,0Gi

lscpu | head -20

Architecture:            x86_64
  CPU op-mode(s):        32-bit, 64-bit
  Address sizes:         45 bits physical, 48 bits virtual
  Byte Order:            Little Endian
CPU(s):                  2
  On-line CPU(s) list:   0,1
Vendor ID:               AuthenticAMD
  Model name:            AMD Ryzen 5 3550H with Radeon Vega Mobile Gfx
    CPU family:          23

ps aux | head -15

USER         PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
root           1  0.2  0.5 43628 22776 ?        Ss   05:32   0:03 /usr/lib/systemd/systemd --switched-root --system --deserialize=55 rhgb
root           2  0.0  0.0     0     0 ?        S    05:32   0:00 [kthreadd]
root           3  0.0  0.0     0     0 ?        S    05:32   0:00 [pool_workqueue_release]
root           4  0.0  0.0     0     0 ?        I<   05:32   0:00 [kworker/R-rcu_gp]
root           5  0.0  0.0     0     0 ?        I<   05:32   0:00 [kworker/R-sync_wq]
root           6  0.0  0.0     0     0 ?        I<   05:32   0:00 [kworker/R-kvfree_rcu_reclaim]
root           7  0.0  0.0     0     0 ?        I<   05:32   0:00 [kworker/R-slub_flushwq]
root           8  0.0  0.0     0     0 ?        I<   05:32   0:00 [kworker/R-netns]

systemctl list-units --type=service --state=running

  UNIT                       LOAD   ACTIVE SUB     DESCRIPTION
  abrt-journal-core.service  loaded active running ABRT coredumpctl message creator
  abrt-oops.service          loaded active running ABRT kernel log watcher
  abrt-xorg.service          loaded active running ABRT Xorg log watcher
  abrtd.service              loaded active running ABRT Daemon
  accounts-daemon.service    loaded active running Accounts Service
  alsa-state.service         loaded active running Manage Sound Card State
  atd.service                loaded active running Deferred execution scheduler
  auditd.service             loaded active running Security Audit Logging Service
  avahi-daemon.service       loaded active running Avahi mDNS/DNS-SD Stack
