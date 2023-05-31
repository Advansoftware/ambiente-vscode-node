FROM ubuntu:18.04
RUN apt-get update
#install nvm e node
RUN echo "y" | apt-get install curl
RUN mkdir -p /usr/local/nvm
ENV NVM_DIR /usr/local/nvm
ENV NODE_VERSION v16.18.1
RUN curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.39.1/install.sh | bash
RUN /bin/bash -c "source $NVM_DIR/nvm.sh && nvm install $NODE_VERSION && nvm use --delete-prefix $NODE_VERSION"
ENV NODE_PATH $NVM_DIR/versions/node/$NODE_VERSION/bin
ENV PATH $NODE_PATH:$PATH

#NPM update and prepare sails
RUN npm install -g npm@latest
RUN npm install -g db-migrate
RUN npm install -g sails
#install dev dependencies
RUN apt-get install python3 -y
RUN apt-get install build-essential -y
RUN apt-get install wget libnss3-tools -y

#install mkcert 
RUN wget https://github.com/FiloSottile/mkcert/releases/download/v1.4.3/mkcert-v1.4.3-linux-amd64
RUN mv mkcert-v1.4.3-linux-amd64 /usr/bin/mkcert
RUN chmod +x /usr/bin/mkcert

#update again
RUN apt-get update
COPY node-entrypoint.sh /usr/local/bin
RUN ln -s usr/local/bin/node-entrypoint.sh /
RUN chmod +x node-entrypoint.sh
