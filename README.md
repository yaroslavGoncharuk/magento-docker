# magento-docker

`magento-docker` is Docker environment for easy to set up, configure, debug Magento2 with Live Search instance.

### Requirements

* [Git](https://git-scm.com/book/en/v2/Getting-Started-Installing-Git)
* [Docker](https://docs.docker.com/)
* [Docker Compose](https://docs.docker.com/compose/install/)
* Setup SSH-keys on your github account. (see [docs](https://help.github.com/en/github/authenticating-to-github/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent)  for [help](https://help.github.com/en/github/authenticating-to-github/adding-a-new-ssh-key-to-your-github-account))

* (optional - for Mutagen installation only) Install Mutagen [docs](https://mutagen.io/documentation/introduction/installation)
* Ensure you do not have `dnsmasq` installed/enabled locally (will be auto-installed if you've use Valet+ to install Magento)


### How to install

#### Steps

1. Create a directory where all repositories will be cloned (used in your IDE)
 
    Proposed structure:
```
    ~/www/magento-docker                    # This repo
    ~/www/repos/magento2ce                  # Magento 2 repo
```

2. Copy `.env.dist` in `.env` and update the variables you need.

3. Add `magento.test` to hosts:

```
    sudo -- sh -c "echo '127.0.0.1 magento.test' >> /etc/hosts"
```

### Project start

* RUN `mutagen project start` to start project (repositories clone, linking, configuration)

#### Enable/disable Xdebug 

* Enable: `mutagen project run xdebug-enable`
* Disable: `mutagen project run xdebug-disable`

:warning: Enabled Xdebug may slow your environment. 
 
:exclamation: port `9003` is used for debug. 

#### Emails sending

Sent emails will be saved in folder `~/www/magento2ce/var/tmp/mails/` as .htm files

### Project termination (removes all containers and volumes)

* RUN `mutagen project terminate`

