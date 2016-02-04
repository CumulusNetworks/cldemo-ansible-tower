Quagga on Docker
================
This demo shows off two ways of putting Quagga into a container to do Layer 3
networking on the hosts.

docker-privileged
-----------------
This demo puts Quagga in a privileged container with direct access to the host
networking stack.

Pros:
  * Layer 3 on the host without installing or compiling Quagga
  * Portable Quagga solution

Cons:
  * Requires a fully privileged docker container, slightly increases attack
    surface compared to just running Quagga as root


docker-vrouter
--------------
This demo creates a lightweight virtual router running Quagga, making it easy to
connect other tenants on the host (such as containers or VMs) to the rest of the
network.

Pros:
  * Behaves like a lightweight virtual Cumulus switch
  * Probably more efficient than using VX as a Vrouter
  * Connects containers and VMs to the rest of the Layer 3 fabric without having
    to use NAT or a separate overlay solution
  * No configuration on other tenants necessary

Cons:
  * Very convoluted process for setting up the vrouter itself
  * Less efficient than using docker-privileged
