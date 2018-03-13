#Create container and install necessary stuffs
FROM			ruby
RUN				apt-get update -y && apt-get install -y \
				build-essential libpq-dev nodejs && \
				apt-get autoclean -y && apt-get clean -y
RUN				gem install rails
#Inside container, copy whatever is needed and start up rails
ONBUILD COPY	app/ /opt/app
ONBUILD EXPOSE	3000
ONBUILD RUN		bundle install && \
				rake db:migrate && \
				rake db:setup && \
				rake db:seed
#Sets workdir
WORKDIR			/opt/app