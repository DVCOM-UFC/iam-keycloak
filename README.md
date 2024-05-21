# Keycloak - Synapse Integration

Keycloak is an open-source identity and access management solution. Keycloak provides user federation, strong authentication, user management, fine-grained authorization, and more

# Certificate generation with Lets Encrypt

## 1. Install certbot

First you will need to install certbot. This depends on the Linux distro you are using.

For example, for apt-based distros such as Debian or Ubuntu, you can just run the following:

```bash
apt install certbot
```
  
## 2. Create HTTPS certificates

Set up certificates:

```bash
certbot certonly --standalone
```
