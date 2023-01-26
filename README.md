# Examination files

In these folders, you will find the necessary files for setting up a nodemailer API on your server. Nodemailer is a popular Node.js module that allows you to send emails from your server. The Nodemailer API in these folders has been configured to send emails to a Gmail account using the SMTP protocol. Additionally, the folders contain config files for nginx on Debian/Ubuntu OS. These files are used to configure nginx as a reverse proxy. The config file is also scripted to create a log file. This log file stores logs for every request made to the server.

# Ports

API: 4000
Nginx: 80

# Nodemailer API installation

## Pre-requisites

Before you proceed to install the Nodemailer API, you need to have the following tools installed:

- [Node](https://nodejs.org/en/)

## How to install

In order to install Nodemailer API you need to run:

```
npm install
```

## How to run project locally

To execute a local Nodemailer API, run:

```
npm run start
```

## Restrict CORS origin

Currently, the CORS origin for Nodemailer API is open to all origins. You can change the default origin to a specific origin to restrict access. This is recommended.

To restrict access open index.js inside the nodemailer-api folder and change to your client domain name:

const corsOptions = {
origin: "example.com",
};

# Nginx installation on a linux OS

## How to install Nginx from official Debian/Ubuntu packages

In order to install Nginx you need to run:

```
sudo apt update
sudo apt install nginx
```

## Add client domain name to Nginx configuration

Open nodemailer-server.conf and change the domain name to your existing client domain name:

server_name example.com;

## How to create a Nginx reverse proxy

Move file inside the nginx-configs folder to:

/etc/nginx/conf.d

## How to start Nginx

In order to start Nginx you need to run:

```
sudo systemctl start nginx
```

# How to expose Nodemailer to the internet

## Open port on router

In order for Nginx to be able to receive incoming requests, it is necessary to open a port on the server where it is running. Port 80 is the default port for the Nginx configuration file and can be changed.

In order for requests to reach the server, the router that is directing traffic to the server must also have port 80 open. The exact method for doing this will depend on the type of router you are using.

## Open port on your firewall

If you have followed the previous steps and port 80 is still not open, it may be due to a firewall on the server or network blocking access to that port. To resolve this issue, you will need to open port 80 on the firewall. The exact method for doing this will depend on the type of firewall you are using.

# Client post requests

## A valid post request

In order for the Nodemailer API to send emails it needs a valid post request.

This is a valid post request body:

{
email: string,
subject: string,
message: string,
}
