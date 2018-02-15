How to use repository
=========
----

Requirements
------------
* Perpetration

# for Mac

``` bash
$ vim  ~/.ansible.cfg 
[defaults]
roles_path = /Users/`uname -n`/tkd-ansible/roles
```


# for CentOS
$ vim /etc/ansible/ansible.cfg
roles_path = /home/`uname -n`/tkd-ansible/roles
```

# Set deploy host

```bash
# fix localhost -> my tkd001 ip
$ /Users/`uname -n`/tkd-ansible/roles/setup-hosts/tkd001/tasks/main.yml 
```

# Deploy
```bash
# list
$ ansible-playbook -i inventories/personal-environment/hosts personal_environment.yml -uroot -k --list-tasks --list-hosts
# exec
$ ansible-playbook -i inventories/personal-environment/hosts personal_environment.yml -uroot -k

失敗した場合は
--start-at-task=START_AT_TASK
で該当行からサイド実施すること
```

# Output example

```bash
$ ansible-playbook -i inventories/personal-environment/hosts personal_environment.yml --ask-vault -uroot -k
SSH password: 
Vault password: 
[DEPRECATION WARNING]: 'include' for playbook includes. You should use 'import_playbook' instead. This feature will be removed in version 2.8. 
Deprecation warnings can be disabled by setting deprecation_warnings=False in ansible.cfg.

PLAY [Setup_tkd001] *************************************************************************************************************************************

TASK [Gathering Facts] **********************************************************************************************************************************
ok: [133.242.231.69]

TASK [yum install jq] ***********************************************************************************************************************************
ok: [133.242.231.69]

TASK [setup-hosts/tkd001 : Download the Go tarball] *****************************************************************************************************
ok: [133.242.231.69]

TASK [setup-hosts/tkd001 : Register the current Go version (if any)] ************************************************************************************
ok: [133.242.231.69]

TASK [setup-hosts/tkd001 : Remove old installation of Go] ***********************************************************************************************
skipping: [133.242.231.69]

TASK [setup-hosts/tkd001 : Extract the Go tarball if Go is not yet installed or not the desired version] ************************************************
skipping: [133.242.231.69]

TASK [setup-hosts/tkd001 : Add the Go bin directory to the PATH environment variable for all users] *****************************************************
ok: [133.242.231.69]

TASK [setup-hosts/tkd001 : Set GOPATH for all users] ****************************************************************************************************
ok: [133.242.231.69]

TASK [setup-hosts/tkd001 : Set docker repo] *************************************************************************************************************
ok: [133.242.231.69]

TASK [setup-hosts/tkd001 : Install docker] **************************************************************************************************************
ok: [133.242.231.69]

TASK [setup-hosts/tkd001 : service] *********************************************************************************************************************
ok: [133.242.231.69]

TASK [setup-hosts/tkd001 : service] *********************************************************************************************************************
ok: [133.242.231.69]

TASK [setup-hosts/tkd001 : Get docker-compose] **********************************************************************************************************
ok: [133.242.231.69]

TASK [setup-hosts/tkd001 : chmod docker-compose] ********************************************************************************************************
skipping: [133.242.231.69]

TASK [setup-hosts/tkd001 : Get docker-compose ver] ******************************************************************************************************
ok: [133.242.231.69]

TASK [setup-hosts/tkd001 : Install command completion] **************************************************************************************************
ok: [133.242.231.69]

PLAY RECAP **********************************************************************************************************************************************
133.242.231.69             : ok=13   changed=0    unreachable=0    failed=0   
```

# memo 

``` bash
git config --global user.name "GitSumito"
git config --global user.email tsukada@sumito.jp
git add -u .
git add .
git commit -m "delete something"
git status
git push -u origin master
```
