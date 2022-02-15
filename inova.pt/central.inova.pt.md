#Instance details

- Ubuntu OS
- Type - t2micro
- eth0 subnet IP - 172.31.128.11/24


#Services installed


- In this instance was installed a NFS server complemented with a NIS server, with the following configuration;

        https://github.com/JFRego/NIS-NFS-config/blob/main/nis-nfs-config.md
        
- Both this services were mounted on a raid5 array encrypted created by the following method in the repository bellow;

        https://github.com/JFRego/raid-luks-lvm-config/blob/main/raid%20luks%20lvm.md
        
- It was also installed a email server with the following configuration;

        https://github.com/JFRego/basic-mail-server-config/blob/main/Exim4%20%2B%20courier%20config.md
        

