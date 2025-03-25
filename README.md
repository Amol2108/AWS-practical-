# AWS-practical-
for pinging from public to private ec2 and making all the 
[ec2-user@ip-172-31-6-115 ~]$ sudo -i
[root@ip-172-31-6-115 ~]# nano private.txt
[root@ip-172-31-6-115 ~]# nano private.pem
[root@ip-172-31-6-115 ~]# chmod 700 private.pem
[root@ip-172-31-6-115 ~]# ping 13.201.82.118
PING 13.201.82.118 (13.201.82.118) 56(84) bytes of data.
64 bytes from 13.201.82.118: icmp_seq=1 ttl=126 time=0.592 ms
64 bytes from 13.201.82.118: icmp_seq=2 ttl=126 time=1.17 ms
64 bytes from 13.201.82.118: icmp_seq=3 ttl=126 time=0.618 ms
64 bytes from 13.201.82.118: icmp_seq=4 ttl=126 time=0.286 ms
64 bytes from 13.201.82.118: icmp_seq=5 ttl=126 time=1.01 ms
64 bytes from 13.201.82.118: icmp_seq=6 ttl=126 time=0.471 ms
64 bytes from 13.201.82.118: icmp_seq=7 ttl=126 time=0.318 ms
64 bytes from 13.201.82.118: icmp_seq=8 ttl=126 time=1.86 ms
64 bytes from 13.201.82.118: icmp_seq=9 ttl=126 time=0.697 ms
64 bytes from 13.201.82.118: icmp_seq=10 ttl=126 time=0.749 ms
64 bytes from 13.201.82.118: icmp_seq=11 ttl=126 time=1.71 ms
64 bytes from 13.201.82.118: icmp_seq=12 ttl=126 time=1.30 ms
64 bytes from 13.201.82.118: icmp_seq=13 ttl=126 time=0.588 ms

-------------------------------------25-3-2025------------------------
Volume practical
1  sudo
    2  sudo -i
    3  lsblk
    4  fdosk /dev/xvdbf
    5  fdisk /dev/xvdbf
    6  lsblk
    7  ls
    8  mkdir /mnt/data
    9  ls
   10  ls mnt
   11  ls /mnt
   16  lsblk
   17  
   18  lsblk
   19  
   20  lsblk
   21  mount /dev/xvdbf1 /mnt/data
   22  mount /dev/xvdbf1 /mnt/data/
   23  mount dev/xvdbf1 /mnt/data/
   24  mount dev/xvdbf1 /mnt/data
   25*
   26  mount /dev/xvdbf1 /mnt/data
   27  mount /dev/xvdbf1 /mnt/data/
   28  lsblk
   29  history
   30  mkfs -t ext3 /dev/xvdbf1 -------to format particular disk/partition
   31  mount /dev/xvdbf1 /mnt/data/
   32  lsblk-------- to check all the partition created



