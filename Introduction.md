#Introduction

![Topology](https://user-images.githubusercontent.com/98925009/173232812-8e9a237b-e11d-4ae7-a0cb-aca2d3a48895.png)




- In this project it was ask to create a network topology with two sites in different vpc's, east site and west site, both connected with a site-to-site vpn;
The two sites were configured with the same network IP and also the same subnets IP's as well;

- Network IP's - 172.31.0.0/16

- Subnets IP's - 172.31.0.0/20
               - 172.31.96.0/24
               - 172.31.128.0/24
               
- In the west site was set the inova.pt domain and in the east site the enta.pt domain;
All instances under inova.pt domain were configured with a debian based OS and the instances in enta.pt domain with redhat based OS;

- It also have an external client wich has two remote access vpn connection to each site, more specifically connections to the control instance of each site;

- inova.pt site has 6 instances as well as enta.pt site;

- control.inova.pt (.enta.pt)
- www.inova.pt (.enta.pt)
- central.inova.pt (.enta.pt)
- wazuh.inova.pt (.enta.pt)
- sales.inova.pt (.enta.pt)
- marketing.inova.pt (.enta.pt)

- In the following directories it is specified all the configurations made in each instance;

