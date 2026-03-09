##STAGE 1##
##--BUILD--##

# taking the base image
FROM node:18-alpine AS BUILD
# creating the directory for the container 
WORKDIR /app
# Copy the package.json in container directory from local to avoid repeating the downloads of dependencies
COPY package.json .
# Run the commands to install all
RUN npm install 
# Copy the code from my local 
COPY . .
# 
RUN npm run build 

##STAGE 2##
##SERVE##

FROM nginx:alpine
COPY --from=BUILD /app/build /usr/share/nginx/html
EXPOSE 80
