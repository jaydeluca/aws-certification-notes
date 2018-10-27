# Encrypt EBS Volume to EC2 Instance

1. Navigate to your EC2 under Services
2. On the left-side panel, under Elastic Block Store click "Volumes"
3. Click "Create Volume"
4. For Availability Zone - make sure it matches your EC2 instance
5. Check off "Encrypt This Volume"
    - Note: Volumes that are created from encrypted snapshots are automatically encrypted, and volumes that are created from unencrypted snapshots are automatically unencrypted. If no snapshot is selected, you can choose to encrypt the volume.
6. For **Master Key** select (default) aws/ebs
7. Click Create
8. You will now see your volumne with a _Stage_ or "available"
9. Check off the volume and click "Actions" > "Attach Volume"
10. Select your EC2 instance from and click "Attach"
11. Now ssh into your EC2 instance
    ```sh 
    ssh ec2-user@00.000.000.00 -i MyNewKeyPair.pem
    sudo su # elevate to root
    lsblk # shows all volumes
    ```
12. You should see `xvdf    202:80   0  100G  0 disk ` = encrypted volume (Needs to be mounted)
13. Before mounting volume, put file system on volume
    ```sh 
    # check if volume already has file system
    file -s /dev/xvdf 
    >> /dev/xvdf: data  # no data on volume - can create file system now
    ```

14. Create file system
    ```sh 
    mkfs -t ext4 /dev/xvdf
    # check that file system has been created
    file -s /dev/xvdf 
    >> /dev/xvdf: Linux rev 1.0 ext4 filesystem data, UUID=eea5f458-339b-4781-9b23-48af4bc153dd (extents) (64bit) (large files) (huge files)
    ```
    ```sh 
    lsblk
    >> NAME    MAJ:MIN RM  SIZE RO TYPE MOUNTPOINT
       xvda    202:0    0    8G  0 disk 
       └─xvda1 202:1    0    8G  0 part /
       xvdf    202:80   0  100G  0 disk 
    cd /
    mkdir filesystem
    # mount xvdf to this directory (filesystem)
    mount /dev/xvdf /filesystem
    lsblk
    >> NAME    MAJ:MIN RM  SIZE RO TYPE MOUNTPOINT
       xvda    202:0    0    8G  0 disk 
       └─xvda1 202:1    0    8G  0 part /
       xvdf    202:80   0  100G  0 disk /filesystem
    cd filesystem
    echo "Hello Cloud Gurus" > hello.txt
    ls
    >> hello.txt
    ```

15. Now lets go ahead and unmount this
    ```sh 
    cd /
    lsblk
    >> NAME    MAJ:MIN RM  SIZE RO TYPE MOUNTPOINT
       xvda    202:0    0    8G  0 disk 
       └─xvda1 202:1    0    8G  0 part /
       xvdf    202:80   0  100G  0 disk /filesystem
    umount -d /dev/xvdf
    lsblk
    >> NAME    MAJ:MIN RM  SIZE RO TYPE MOUNTPOINT
       xvda    202:0    0    8G  0 disk 
       └─xvda1 202:1    0    8G  0 part /
       xvdf    202:80   0  100G  0 disk 
    ```
16. Theres no no mount point
17. Lets create Snapshot of EBS Volume and deploy it again
18. Navigate to AWS Console > Click "Actions" > "Detatch Volume"
19. After it's been detatched click "Actions" > "Create Snapshot"
20. Name it "myencryptedsnap"
21. If you navigate to Snapshots you should see that the _Status_ is completed
22. Go back to Volumes and delete the volume
23. Go back to your terminal and run `lsblk`. We should see that the volume xvdf is no longer there
    ```sh
    lsblk
    >> NAME    MAJ:MIN RM SIZE RO TYPE MOUNTPOINT
       xvda    202:0    0   8G  0 disk 
       └─xvda1 202:1    0   8G  0 part /
    ```
24. Back in AWS Console > Snapshots > Actions > Create Volume
35. Navigate to Volumes > Actions > Attach Volume
36. Select your instance > Create
37. Open up terminal and enter `lsblk`
    ```sh 
    lsblk
    >> NAME    MAJ:MIN RM  SIZE RO TYPE MOUNTPOINT
       xvda    202:0    0    8G  0 disk 
       └─xvda1 202:1    0    8G  0 part /
       xvdf    202:80   0  100G  0 disk 
    file -s /dev/xvdf
    >> /dev/xvdf: Linux rev 1.0 ext4 filesystem data, UUID=eea5f458-339b-4781-9b23-48af4bc153dd (extents) (64bit) (large files) (huge files)
    cd ..
    mount /dev/xvdf /filesystem
    cd filesystem/
    ls
    >> hello.txt  lost+found
    nano hello.txt 
    >> "Hello Cloud Gurus"
    cd ..
    umount -d /dev/xvdf
    lsblk
    >> NAME    MAJ:MIN RM  SIZE RO TYPE MOUNTPOINT
       xvda    202:0    0    8G  0 disk 
       └─xvda1 202:1    0    8G  0 part /
       xvdf    202:80   0  100G  0 disk 
    ```
38. We've successfully encrypted an additional volume - We've taken a snapshot of the volume - We've deleted that volume - Restored the volume 
