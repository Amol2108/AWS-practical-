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
Volume practical---------temporary mounting
--After we create volume we need to attach it to the instance and give device name, so that device name will be searched by using /dev/"device name".
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

----------------------------------------------------27-03-2025----------------------------------------------------
Practical for permanent mounting-- EBS (Elastic Block Storage)-
 1  lsblk
    2  pv /dev/xvdbf
    3  pv /dev/xvdbf1
    4  pvcreate /dev/xvdbf
    5  pvdisplay
    6  vgcreate my-vg /dev/xvdbf1
    7  lsblk
    8  pvdisplay
    9  vgcreate my-vg /dev/xvdbf
   10  vgdisplay
   11  fdisk /dev/xvdbf
   12  lsblk
   13  exit
   14  lsblk
   15  pvdisplay
   16  vgdisplay
   17  pvcreate /dev/xvdbf1
   18  pvdisplay
   19  vgcreate my-vg /dev/xvdbf1
   20  lvcreate -L 4.5G -n my-lv my-vg
   21  lvdisplay
   22  blkid ---USE TO COPY ID OF THE PARTITION CREATED TO PERMANENTLY MOUNT THE DISK
   23  mkdir data
   24  ls
   25  rmdir data
   26  ls
   27  mkdir /mnt/data
   28  mount /dev/my-vg/my-lv /mnt/data
   29  mount /dev/my-vg/my-lv mnt/data
   30  mount dev/my-vg/my-lv mnt/data
   31  mount dev/my-vg/my-lv mnt/data/
   32  mount /dev/my-vg/my-lv /mnt/data/
   33  lsblk
   34  vgdisplay
   35  mount /dev/my-vg/my-lv /data
   36  ls
   37  mkdir /mnt/data
   38  rmdir data
   39  rmdir /mnt/data
   40  l
   41  ls
   42  mkdir /mnt/data
   43  ls
   44  ls /mnt
   45  mount /dev/my-vg/my-lv /mnt/data
   46  rmdir /mnt/data
   47  ls /mnt
   48  mkdir data
   49  mount /dev/my-vg/my-lv /root/data
   50  mkfs.ext3 /dev/my-vg/my-lv
   51  mount /dev/my-vg/my-lv /root/data
   52  ls
   53  lsblk
   54  nano /etc/fstab
   55  blkid
   56  nano /etc/fstab --HERE WE MOUNT THE DISK BY " 
   /MNT/DATA /DEV/XVDBF1 EXT3(EXTENSION USED TO MAKE PARTITON OF DISK) ID(OF THE DISK WHICH WE GOT FROM BLKID)
   57  mount -a --TO SAVE THE PERMANENT MOUNTING OF THE DISK
   58  lsblk
   59  nano /etc/fstab
   60  history
Explanation---
step-1: create a instance and volume of 10GB then attach volume to instance.
step-2: login to terminal and create a physical volume with pv
step-3: create a volume group
step-4: create a logical volume
step-5: format the partition which is created(DO NOT FORMAT WHOLE VOLUME OR ELSE WE WONT BE ABLE TO CREATE ANY PARTITION).
step-6: create a directory and mount it on the created partiton.
step-7: go to /etc/fstab and give the path of the created partition and directroy along with extension type used and the id of partition.
ex- /dev/xvdbf1 /mnt/data ext3 <id of partition>
step-8: now using mount -a we make sure it is permanently mounted.
step-9: using lsblk we can now check the permanent mounting done on the partiton.
---------------------------------------------28-03-2025--------------------------------------------------------------------------------
Practical for EFS- (Elastic File System)-
QUE- Why use EFS- 
ANS- we use EFS so that when we create two instances in two different regions and we want to connect them in as in if we create a file in one instance then automatically we should see the file in other instance, means they are connected to each other.
just for linux terminal commands-
  1  yum install nfs-common
    2  update
    3  apt update
    4  apt install nfs-common
    5  mkdir efs
    6  ls
    7  sudo mount -t nfs4 -o nfsvers=4.1,rsize=1048576,wsize=1048576,hard,timeo=600,retrans=2,noresvport 172.31.43.43:/ efs
    8  cd efs/
    9  ls
   10  cd
   11  exit
   12  history
Explanation-
step-1: create security group with inbound rules as 
1- SSH : 
2- HTTP : 
3- NFS :
and for outbound rules keep it all traffic then create two instances in same region with name efs1 and efs2, efs1 will be in ap-south-1a and efs2 will be in ap-south-1b.
step-2: connect the two instances in two different terminals and install nfs-common in both the terminal.
step-3: create a directory called efs in both terminals.
step-4: Now create efs file system and in network section always select the created secuirty group and save it.
click on attach > we will get a window with mount ip and other option always click on mount ip and copy the code in it and paste it in both the terminals.
step-5: now create a file in any of the directory in any terminal, so the file should be visible in the other terminal as well, if this happens the practical is succesful.
[PS- we create efs directory because the code we are copying has efs in it, we can also change the name as per our requirement]

-----------------------------------------------------------------03/04/2025---------------------------------------------------------------------
PRACTICAL FOR VPC PEERING:-
Step 1:-
create a VPC- 
 
 Step 2:-
Create 2 subnets one public and private, set CIDR values with caution as we need to communicate outside the region so the CDIR/IP’s should never overlap each other.
 
Step 3:-
Create a Internet Gateway and attach to the user created VPC.
 
Step 4:-
Create a NGW(Nat-gateway), while creating attach the NGW to public subnet. Allocate elastic Ip to NGW always while creating.
 
Step 5:- Creating Route Tables
1-	Create route table, one public and other private.
2-	Add internet gateway to public route.
3-	Add Nat-gateway to private route.
4-	Edit subnet association of public route to public subnet.
5-	Edit subnet association of private route to private subnet. 

Step 6:- Creating two Ec2 instances.
1-	Create one public ec2 instance in one AZ(availability zones), the security group should be all traffic.
2-	Create another private ec2 instance in other AZ, security group should be same which is used in public instance.
  
Step 7:- Create VPC Peering
1-	Create VPC peering between two regions one will be requester and other will be receiver.
2-	Add the details through the form and create VPC peering.
3-	A VPC peering can be done in-
1-	Same region same account
2-	Different region same account
3-	Different region different account.
 
 NOW FOR CONNECTING PUBLIC INSTANCE TO PRIVATE INSTANCE OF DIFFERENT REGIONS-
1-	IN THE PUBLIC ROUTE TABLE, WE NEED TO ADD BOTH THE IP’S OF THE INSTANCES CREATED IN DIFFERENT REGION
Ex- PUBLIC INSTANCE IN MUMBAI REGION WANTS TO CONNECT WITH THE PRIVATE INSTANCE CREATED IN NORTH VIRIGINIA.
2-	SO INORDER TO ESTABLISH THEIR CONNECTION FIRSTLY WE ADD IP’S OF BOTH THE INSTANCES IN PUBLIC AND PRIVATE ROUTES OF MUMBAI REGIONS, FOLLOW THE IMAGE BELOW FOR THE SEQUENCE TO ADD ROUTE FOR THE IP’S.
------------------------------------------------------------------------------------------------------------------

 














