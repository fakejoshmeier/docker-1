#Create container and install necessary stuffs
FROM			ruby
RUN				apt-get update && \
				apt-get install nodejs -y && \
				apt-get autoclean -y && \
				apt-get clean -y && \
				gem install rails && \
				mkdir /opt/app
#Inside container, copy contents of app folder over to image and set everything
#up
ONBUILD WORKDIR	/opt/app
ONBUILD EXPOSE	3000
ONBUILD COPY	app/ /opt/app
ONBUILD RUN		bundle install && \
				rake db:migrate && \
				rake db:setup && \
				rake db:seed