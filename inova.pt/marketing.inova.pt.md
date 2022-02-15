#Instance details

- Ubuntu OS
- Type - t2micro
- eth0 subnet IP - 172.31.128.14


#Services installed


- In this instance was installed a NFS and NIS client service with the configuration from the repository in the client side section;

        https://github.com/JFRego/NIS-NFS-config/blob/main/nis-nfs-config.md

- It was also installed an Desktop environment using the follow configuratio;

        apt install -y xfce4 xfce4-goodies
        apt install -y xrdp chromium-browser filezilla thunderbird
        adduser xrdp ssl-cert
        
- And was also installed a wazuh agent from wazuh documentation;

        https://documentation.wazuh.com/current/installation-guide/wazuh-agent/wazuh-agent-package-linux.html
