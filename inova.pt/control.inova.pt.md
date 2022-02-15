#Instance details

- Ubuntu OS
- Type - t2small
- eth0 subnet IP - 172.31.9.208/20
- eth1 subnet IP - 172.31.96.0/24
- eth2 subnet IP - 172.31.128.0/24


#Services installed


- In control.inova.pt was set a subordinate CA server, signed by control.enta.pt CA server who was used to signed all certificates in both sites;
the configuration of this sub CA server is present in the reposytory bellow;

        https://github.com/JFRego/CA-subCA-configuration/blob/main/ca%20subca%20config.md
        
- In order to establish the remote access and site-to-site vpn connections both services were configured with the following configuration;

        ra - https://github.com/JFRego/basic-openvpn-config/blob/main/RA%20config%20server%20side.md
        
        ss - https://github.com/JFRego/basic-openvpn-config/blob/main/SS%20config%20server%20side.md
        
- It was also install and configured a DNS master server with the following configuration;        

        https://github.com/JFRego/Master-DNS-config/blob/main/Master%20DNS%20debian.md
        
- And was also installed a wazuh agent from wazuh documentation;

        https://documentation.wazuh.com/current/installation-guide/wazuh-agent/wazuh-agent-package-linux.html
        

#NAT/FW configuration


- In order to both sites comunicate truth the ss vpn conection and to all the instances comunicate to each others and to the internet was necessary to configure
the firewall as it is shown bellow;

        -A PREROUTING -d 172.29.0.0/16 -i tun-ss -j NETMAP --to 172.31.0.0/16
        -A PREROUTING -i eth0 -p tcp -m tcp -m multiport --dports 80,443 -j DNAT --to-destination 172.31.96.11
        -A PREROUTING -i eth0 -p tcp -m tcp -m multiport --dports 20,21,990 -j DNAT --to-destination 172.31.96.11
        -A PREROUTING -i eth0 -p tcp --dport 3389 -j DNAT --to-destination 172.31.128.13
        -A PREROUTING -i eth0 -p tcp -m tcp --dport 10000:10100 -j DNAT --to-destination 172.31.96.11
        -A PREROUTING -i eth0 -p tcp --dport 444 -j DNAT --to-destination 172.31.128.12:443
        -A POSTROUTING -s 172.31.0.0/16 -o tun-ss -j NETMAP --to 172.29.0.0/16
        -A POSTROUTING -o eth0 -j MASQUERADE
        


