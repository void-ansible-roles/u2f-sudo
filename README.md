u2f_sudo
====


What is does this role do?
--------------------------

This role installs and configures the appropriate tools to use a U2F security token for authentication to the `sudo` command.


Meta
----

Files Managed:
  * /etc/u2f_mappings
  * /etc/pam.d/sudo
  * /etc/sudoers.d/timeout

Defaults Provided:
  * u2f_sudo_cue: true
  * u2f_sudo_interactive: true
  * u2f_sudo_allow_password: true

Variables Required:
  * u2f_sudo_mappings

```
Mappings should be defined as follows

sudo_u2f_mappings:
  username1:
    username: username1
    u2fkeys:
      friendlyName:
        keyhandle: longStringOne
        userkey: longStringTwo

Where username1 is the user account name on the machine itself, friendlyName
is the person's name, and longStringOne and longStringTwo are obtained by
running `sudo pamu2fcfg -n` and given in the format:
:longStringOne,longStringTwo

Additionally, to ensure that the appid is the same across hosts, set:
u2f_sudo_appid: myAppId
And use the `-i myAppId` argument when running pamu2fcfg
```

Optional Variables:
  * u2f_sudo_timestamp_timeout: how long is sudo auth cached when using timestamps

Files Required:
  * None

Optional Files:
  * None

Conflicting Roles:
  * None

Depends On:
  * None
