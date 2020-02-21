#1. load httpd image
    $ docker load < greenhanddm-httpd.tar
#2. docker run containner # Web Home Directory as /var/www/html
    $ docker run -d --name httpd -p 8089:80 -v /data/docker/httpfile/httpshare:/var/www/html --privileged=true greenhanddm/httpd
#3. enter containner and delete /etc/httpd/conf.d/welcome.conf
    $ cp /etc/httpd/conf.d/welcome.conf /etc/httpd/conf.d/welcome.conf.back
	  $ rm /etc/httpd/conf.d/welcome.conf
#4. restart containner
    $ docker restart httpd
