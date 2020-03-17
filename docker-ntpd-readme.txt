#1. load httpd image
     docker load < greenhanddm-ntp.tar
#2. docker run containner
     docker run -d --name ntp-server -p 8080:80 -p 123:123/udp -v /etc/localtime:/etc/localtime:ro --privileged=true greenhanddm/ntp
#3. check ntp service
     docker exec -it ntp-server service ntp status
#4. check the connection between the NTP server and the upper layer
     docker exec -it ntp-server ntptrace -n 127.0.0.1
#5. Check that the NTP server has completed its own synchronization
     docker exec -it ntp-server ntpq -p