FROM node:14

WORKDIR /app

COPY package.json .

RUN ["npm", "install"]

COPY . .

EXPOSE 80

VOLUME [ "/app/feedback" ]
# This tells docker which folder IN THE CONTAINER to be stored on the HOST 

CMD [ "node", "server.js" ]