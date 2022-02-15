#Instance details

- Amazon Linux 2 os
- Type - t2small
- security group -      

        –	sgr-0976375e5e987eb68	IPv4	All traffic	All	All	172.16.0.0/12	–
	–	sgr-04b7138a65dd3428c	–	All traffic	All	All	sg-0b14f4accebd2d242 / default	–
	–	sgr-0c84dc0f58aac77b7	IPv4	All traffic	All	All	192.168.0.0/16	–
	–	sgr-018cf9332d49729c0	IPv4	All traffic	All	All	78.29.147.32/32	–
	–	sgr-04f7a62a0169aaf2a	IPv4	All traffic	All	All	35.86.49.237/32	–
	–	sgr-0174c79ce302d662b	IPv4	All traffic	All	All	85.244.38.230/32	–
	–	sgr-01a54a4bebb7f892d	IPv4	All traffic	All	All	10.0.0.0/8	–
	–	sgr-0b2c1f943e7559a1e	IPv4	All traffic	All	All	54.157.93.37/32	–
	–	sgr-0ef7a3626bac3dedd	IPv4	All traffic	All	All	50.16.75.140/32	–

- eth0 subnet IP - 172.31.2.196/20
- eth1 subnet IP - 172.31.96.0/24
- eth2 subnet IP - 172.31.128.0/24

#Services installed

- In control.enta.pt was set a CA server with the following configuration from my github repository;

        https://github.com/JFRego/CA-subCA-configuration/blob/main/ca%20subca%20config.md

- In order to establish the remote access and site-to-site vpn connections both services were configured with the following configuration;

        ra - https://github.com/JFRego/basic-openvpn-config/blob/main/RA%20config%20server%20side.md

        ss - https://github.com/JFRego/basic-openvpn-config/blob/main/SS%20config%20client%20side.md

- It was also install and configured a DNS master server with the following configuration;

        https://github.com/JFRego/Master-DNS-config/blob/main/Master%20DNS%20redhat.md

- And was also installed a wazuh agent from wazuh documentation;

        https://documentation.wazuh.com/current/installation-guide/wazuh-agent/wazuh-agent-package-linux.html


#NAT/FW configuration

- In order to both sites comunicate truth the ss vpn conection and to all the instances comunicate to each others and to the internet was necessary to 
configure the firewall as it is shown bellow;

        -A PREROUTING -i eth0 -p tcp -m tcp -m multiport --dports 80,443 -j DNAT --to-destination 172.31.96.11
        -A PREROUTING -i eth0 -p tcp -m tcp -m multiport --dports 20,21,990 -j DNAT --to-destination 172.31.96.11
        -A PREROUTING -i eth0 -p tcp -m tcp --dport 10000:10100 -j DNAT --to-destination 172.31.96.11
        -A PREROUTING -i eth0 -p tcp -m tcp --dport 3389 -j DNAT --to-destination 172.31.128.13
        -A PREROUTING -i eth0 -p tcp -m tcp --dport 3390 -j DNAT --to-destination 172.31.128.14:3389
        -A PREROUTING -i eth0 -p tcp -m tcp --dport 444 -j DNAT --to-destination 172.31.128.12:443
        -A PREROUTING -d 172.30.0.0/16 -i tun-ss -j NETMAP --to 172.31.0.0/16
        -A POSTROUTING -o eth0 -j MASQUERADE
        -A POSTROUTING -s 172.31.0.0/16 -o tun-ss -j NETMAP --to 172.30.0.0/16






        
