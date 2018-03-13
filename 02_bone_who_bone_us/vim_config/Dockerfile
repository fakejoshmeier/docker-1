#This Dockerfile is a basic install of Debian that pulls my .vimrc and applies it
#to this container's .vimrc, allowing me to keep all my nifty features, like dynamic
#numbering
FROM	debian
RUN		apt-get update && apt-get upgrade -qq && \
		apt-get install vim git iceweasel -qq && \
		git clone https://github.com/VundleVim/Vundle.vim.git ~/.vim/bundle/Vundle.vim && \
		git clone https://github.com/fakejoshmeier/defaults yo && \
		cd yo && mv .vimrc ~/.vimrc && cd && \
		vim +PluginInstall +qall && \
		echo "colorscheme desert" >> ~/.vimrc