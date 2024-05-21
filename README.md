# Keycloak - Synapse Integration

In this document, will explain SSO(Single Sign-on) implementation with the Matrix Synapse server. For this, we will use Keycloak. Keycloak is an open-source identity and access management (IAM) solution that provides single sign-on (SSO), user authentication, and authorization services for applications and services.

# Certificate generation with Lets Encrypt

## 1. Install certbot

If our Matrix server wants to connect with the SSO provider we should run both the Matrix server and Keycloak in https and configure with SSL certificate. 

First you will need to install certbot. This depends on the Linux distro you are using. For example, for apt-based distros such as Debian or Ubuntu, you can just run the following:

```bash
apt install certbot
```
  
## 2. Create HTTPS certificates

Set up certificates:

```bash
certbot certonly --standalone
```

Save the cert.pem and privkey.pem files into /certs directory

## 3. Change certs directory owner

In order to use the certificate, we need to transfer certs ownership to UID 1000

```bash
chown -R 1000:1000 certs/
```

# Run Keycloak

To run Keycloak just run:

```bash
docker compose up -d
```

Keycloak runs in 5000 port. 

# Keycloak Configuration

## Create a Realm

Here I have created a realm called matrix. Once you created the realm then choose the realm after logging in. After choosing the realm do all other activities such as creating new clients and users

## Create a new Client

The above three screenshots are examples of creating a client and configuring with matrix synapse callback.

We have to give a valid redirect URL [synapse public baseurl]/_synapse/client/oidc/callback.

## Create users

Create users by clicking the Users menu. Using the same user, we can log in to our application.

# Synapse configuration

Open homeserver.yaml file and add the below configuration lines for SSO implementation.
