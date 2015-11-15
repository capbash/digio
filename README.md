dio
==============

A bash implementation of the [Digital Ocean API](https://developers.digitalocean.com/documentation/v2/)

# How to Install #

To install from scratch, run

```bash
curl -s https://raw.githubusercontent.com/capbash/dio/master/dio-installer | bash
```

This will install capbash into /usr/local/bin/dio.  To install it somewhere else, for example:

```bash
curl -s https://raw.githubusercontent.com/capbash/dio/master/dio-installer | bash -s -- --path ~/.bin
```

If you don't trust this project, please don't pipe into bash, and instead download the file,
inspect it and run it directly.

If you already have dio and want to upgrade to the altest, please run

```
dio update-self
```

# Getting Started #

First let's initialize the configs

```
dio init
```

This will create a .dio file in the local directory, and you will need to
specify two important pieces of information.

* TOKEN
* SSH_KEYS

Here's the default config file

```
# dio v0.10
# Provide your Digital Ocean TOKEN
# https://www.digitalocean.com/community/tutorials/how-to-use-the-digitalocean-api-v2
#
# TOKEN=XXXX
#
# You can provide your desired SSH_KEY ID for password login
# https://developers.digitalocean.com/documentation/v2/#ssh-keys
#
# You can get more information about your keys by running
#  > dio list keys
#
# It should be provided as a list, do don't forget your square brackets
# SSH_KEYS=[1234, 4567]
```

Uncomment the TOKEN and put in your tokens value (the above is fake, so don't bother trying it)

Once that's in place, let's create a new droplet

```
dio create drop1
```

If everything was setup correctly, you should see a message like

```
Creating a new droplet drop1 (tor1, 512mb, ubuntu-14-04-x64)
Reply: {"droplet":{"id":1234,"name":"drop1","memory":512,"vcpus":1,"disk":20,"locked":true,"status":"new","kernel":{"id":5175,"name":"Ubuntu 14.04 x64 vmlinuz-3.13.0-57-generic","version":"3.13.0-57-generic"},"created_at":"2015-10-23T03:36:57Z","features":["virtio"],"backup_ids":[],"next_backup_window":null,"snapshot_ids":[],"image":{"id":13089493,"name":"14.04 x64","distribution":"Ubuntu","slug":"ubuntu-14-04-x64","public":true,"regions":["nyc1","ams1","sfo1","nyc2","ams2","sgp1","lon1","nyc3","ams3","fra1","tor1"],"created_at":"2015-08-10T21:30:19Z","min_disk_size":20,"type":"snapshot"},"size":{"slug":"512mb","memory":512,"vcpus":1,"disk":20,"transfer":1.0,"price_monthly":5.0,"price_hourly":0.00744,"regions":["nyc1","sgp1","sfo1","nyc2","lon1","nyc3","ams3","ams2","fra1","tor1"],"available":true},"size_slug":"512mb","networks":{"v4":[],"v6":[]},"region":{"name":"Toronto 1","slug":"tor1","sizes":["512mb","1gb","2gb","4gb","8gb","16gb","32gb","48gb","64gb"],"features":["private_networking","backups","ipv6","metadata"],"available":true}},
        "links":{"actions":[{"id":1234,"rel":"create","href":"https://api.digitalocean.com/v2/actions/1234"}]}}
```

Using the droplet id above (e.g. 1234), we could delete the droplet if it's no longer needed

```
dio delete 1234
```


# Help #

Here's what is currently available

```bash
=============================
 dio v0.15.3 A Bash Implementation
 Of the Digital Ocean API

 More information about the API at
 https://developers.digitalocean.com/documentation/v2/
=============================


Usage

  dio [action]

Project Setup

  init                        - Initialize the local directory to access a digital ocean account

Account

  account                     - To retrieve a list of all of the domains in your account

Actions

  actions                     - List all actions on your account

Domains

  domains                     - List all domains
  domain <name>               - Retrieve info about domain <name>
  create domain <name> <ip>   - Create new domain <name> attached to <ip>
  delete domain <name>        - Delete the domain <name>

Domain Records

  N/A

Droplets

  droplets                   - List all droplets (use this to grab your droplet IDs
  droplet <id>               - List details about a droplet by <id>
  create <name>              - Create a new droplet (by <name>)
  clone <IMAGE> <name>       - Create a new droplet based on the provided <IMAGE> (by <name>)

Droplet Actions

  power on <ID>              - Start your droplet
  power off <ID>             - Turn off your droplet
  snapshot <ID> <name>       - Create a snapshot of <ID> called <name>
  delete                     - Delete a new digitalocean droplet (by ID)
  ssh <ID>                   - SSH into your droploet

API Queries

  list keys                  - List all SSH Keys assoicated with your account
  list droplets              - List all droplets (use this to grab your droplet IDs
  list images                - List all private images

  info <ID>                  - List details about your droplet

Other Actions

  update-self                - Upgrade to latest version
  version                    - Display just version information, like 'dio v0.15.3'
  help                       - Show this message


For reporting issues, please contact aforward@gmail.com, or
report directly against the project at https://github.com/capbash/dio
```


