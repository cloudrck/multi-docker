# Use an existing docker image as a base for Node App
FROM node:alpine as builder

WORKDIR /opt/app

#Copy files in current directory.
#Copy Just the file needed to install npm
COPY  ./package.json ./
# Run command in container at boot.
RUN npm install
COPY ./ ./
RUN npm run build

# Use an existing docker image as a base for Node App
FROM nginx
EXPOSE 3000
#Nginx is started automatically
COPY ./nginx/default.conf /etc/nginx/conf.d/default.conf
COPY --from=builder /opt/app/build /usr/share/nginx/html
