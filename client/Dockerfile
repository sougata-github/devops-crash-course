# set the base image
FROM node:22-alpine

# create a user with permissions to run the app
# -S -> create a system user
# -G -> add the user to a group 
# this is done to avoid running the apps as root
# if app is run as root, any vulnerability in the app can be exploited to gain access to host system
# good practice to run the app as a non-root user
# still root user 
RUN addgroup app && adduser -S -G app app

# set the working directory
WORKDIR /app

# install pnpm globally
RUN npm install -g pnpm

# copy package.json and packgae-lock.json (here pnpm-lock) to the working directory
# this is done before copying rest of the files to take advantage of Docker's cache and cached dependencies 
COPY package.json pnpm-lock.yaml ./

# install depencencies
RUN pnpm install --frozen-lockfile

# copy rest of the files to working directory
COPY . .

# change the ownership of the /app directory to the app user
# chown -R <user>:<group> <directory> 
# chown command changes the user and/or group ownership of for given file
RUN chown -R app:app .

# switch to non-root user
USER app

# expose port 5173 to tell Docker that the container listens on the specified network at runtime
EXPOSE 5173

# run the app
CMD ["pnpm", "run", "dev"]



