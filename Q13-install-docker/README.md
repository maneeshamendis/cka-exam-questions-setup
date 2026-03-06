You are given a host to prepare for Kubernetes: 
1. Use dpkg to install cri-dockerd Enable and start the cri-docker service 
2. Set net.bridge.bridge-nf-call-iptables to 1 via sysctl. Make sure the changes are persistance accross reboots 
