#sid install of Debian automatically sets up the $GOPATH and whatnot
#when I install golang
FROM	debian:sid
#Installing the goods
RUN		apt-get update && \
		apt-get install ca-certificates \
		golang-go git mysql-server nginx -y && \
		service mysql start && mysql -uroot -e "create database gogs"
#Making a home for the goods and then building
#THE GOODS
RUN		mkdir -p /root/go/src/github.com/gogits && \
		cd /root/go/src/github.com/gogits && \
		git clone --depth=1 -b develop https://github.com/gogits/gogs && \
		cd gogs && \
		go build .
#Making sure that I'm running this all as root
USER	root
EXPOSE	3000
#Revving that engine
RUN		service mysql start
#Pulling into place
WORKDIR	/root/go/src/github.com/gogits/gogs
#THAT GUD GUD GOOOOOOOOOOOOOOODS!
CMD		["./gogs", "web"]