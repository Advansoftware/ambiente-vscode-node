FROM lscr.io/linuxserver/code-server:latest
RUN apt-get update
RUN echo "y" | apt-get install curl
RUN mkdir -p /usr/local/nvm
ENV NVM_DIR /usr/local/nvm
ENV NODE_VERSION v16.18.1
RUN curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.39.1/install.sh | bash
RUN /bin/bash -c "source $NVM_DIR/nvm.sh && nvm install $NODE_VERSION && nvm use --delete-prefix $NODE_VERSION"
ENV NODE_PATH $NVM_DIR/versions/node/$NODE_VERSION/bin
ENV PATH $NODE_PATH:$PATH

#NPM update and prepare workspace
RUN npm install -g npm@latest
RUN npm install -g db-migrate
RUN npm install -g sails
RUN npm install -g yarn

#install dev dependencies
RUN apt-get install git -y
RUN apt-get install python3 -y
RUN apt-get install build-essential -y
RUN apt-get update