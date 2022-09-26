# Goobi workflow test environments

## Local Setup

### Requirements

- local docker installation with docker compose plugin installed

### Usage

```sh
# download the database dump
./init.sh
# initialize the database
docker compose up -d goobi-workflow-db
# start goobi workflow
docker compose up -d goobi-workflow
```

After a moment, you should be able to access the UI via http://localhost:8080/goobi in your browser and be able to log in with the username `goobi` and the password `goobi`.


## Remote setup via cloud-init

In order to setup a simple remote test instance you can use the provided cloud-init user data file `user-data.yml`. You should however change the user stanza to use your own ssh-key or add a password hash.

To use this with the Hetzner hcloud CLI you could run something like:

```sh
hcloud server create --image=ubuntu-22.04 --name=docker-workflow-test --ssh-key=MY_REGISTERED_SSH_KEY--user-data-from-file=user-data.yml --type=cx21
```