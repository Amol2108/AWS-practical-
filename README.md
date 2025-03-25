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


-------------------------------------25-3-2025------------------------
Volume practical
1  sudo
    2  sudo -i
    3  lsblk
    4  
    5  fdisk /dev/xvdbf ---- used to create, delete, and manage disk partitions, allowing you to manipulate the partition table on a hard disk
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
   31  mount /dev/xvdbf1 /mnt/data/ ------------- mounting the directory "data" on the partition
   32  lsblk-------- to check all the partition created

Explanation-
1- In this practical we firstly create a volume in aws.
2- connect that volume to instance.
3- in the terminal we then create partitions for the volume.
4- suppose if we create two additional partition volumes of 2 gb and 4gb then if we want to mount some directories in the created partiton then first we need to format the created partition here which is 4 gb, then we mount the directory on the partiton. 



