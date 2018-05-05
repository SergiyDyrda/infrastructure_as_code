# infrastructure_as_code

Vagrant file here to help you provision testing vm\`s in your environment.

To get work done you\`ll need vagrant 2.0+, Ansible 2.0+ and some vm\`s hypervisor.
If it\`s not virtual box, please indicate this in vagrant file.


This configuration includes: nginx as a front-end load-balancer, two back-end Apache2 servers, MariaDB server.

Note: vagrant configuration also includes manager vm that do all dirty job. You can remove  it if it\`s not need.
