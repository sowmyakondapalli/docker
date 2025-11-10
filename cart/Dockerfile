FROM node:18
ENV MONGO=true
EXPOSE 8080
WORKDIR /opt/server
COPY package.json /opt/server/
RUN npm install
COPY server.js /opt/server/
CMD ["node", "server.js"]