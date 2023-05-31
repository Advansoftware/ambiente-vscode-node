FROM node:18.16.0-alpine
RUN npm install -g npm@latest
RUN npm config set legacy-peer-deps true
COPY node-entrypoint.sh /usr/local/bin
RUN ln -s usr/local/bin/node-entrypoint.sh /
RUN chmod +x node-entrypoint.sh