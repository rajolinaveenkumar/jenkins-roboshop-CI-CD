FROM node:20 AS builder
WORKDIR /opt/server
COPY scripts/* .
RUN npm install


FROM node:20.18.0-alpine3.20
EXPOSE 8080
RUN addgroup -S roboshop && adduser -S roboshop -G roboshop
# RUN addgroup -S <group-name> && adduser -S <user-name> -G <group-name>
RUN mkdir /opt/server
RUN chown roboshop:roboshop /opt/server
# chown <user>:<group> <path>
WORKDIR /opt/server
COPY --from=builder /opt/server /opt/server
USER roboshop
CMD ["node", "server.js"]




### IMP NOTES
# What it does:
# addgroup -S roboshop:
# ➤ Creates a system group named roboshop.

# adduser -S roboshop -G roboshop:
# ➤ Creates a system user named roboshop
# ➤ Assigns it to the group roboshop.

# System users (-S) are for services, not for login. They usually have no password and no home directory.