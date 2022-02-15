#Instance details


- Ubuntu OS
- Type - t2micro
- eth0 subnet IP - 50.16.75.140


#Services installed


- In order to establish remote access vpn connections to both sites the service was installed with the following configuration;

        https://github.com/JFRego/basic-openvpn-config/blob/main/RA%20config%20client%20side.md
        
- It was also installed an Desktop environment using the follow configuratio;

        apt install -y xfce4 xfce4-goodies
        apt install -y xrdp chromium-browser filezilla thunderbird
        adduser xrdp ssl-cert 
        echo xfce4-session > ~/.xsession - inside ubuntu user
