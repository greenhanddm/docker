#1. load vsftpd image
    $ docker load < greenhanddm-vsftpd.tar
#2. docker run containner 
    #FTP User is rtlshftp,FTP Directory is /home/rtlshftp
	  #Mapping /data/docker/httpfile/httpshare to /home/rtlshftp
    $ docker run -d --name vsftpd -p 20:20 -p 21:21 -p 21100-21110:21100-21110 \
	    -v /data/docker/httpfile/httpshare:/home/rtlshftp \
	    --privileged=true greenhanddm/vsftpd
