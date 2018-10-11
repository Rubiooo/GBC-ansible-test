#GBC-ansible-test


# Setup Gitlab server

## Gitlab configuration

* Domain name
The domain name for GBC gitlab server is `gitrepo.gbc.ca`.

* SSL certificate
put valid ssl certificate file(`gitrepo.gbc.ca.crt`) and key(`gitrepo.gbc.ca.key`) under `roles/gitlab-master/files/config/ssl` folder

## Gitlab installation

* With ansible script

`# ansible-playbook -i inventory gitlab.yaml -K`  # provide sudo password

## Gitlab start/stop

`# systemctl gitlab start`
`# systemctl gitlab stop`

## Gitlab backup

Stop gitlab. Backup the data folder(`/app/gitlab/data`) on gitlab server


# Setup Jenkins server

## Jenkins configuration

* Domain name
Jenkins is running on same machine as GBC gitlab server, share the same domain name as `gitrepo.gbc.ca`

* SSL certificate
put valid ssl certificate file(`gbc.ca.crt`) and key(`gbc.ca.key`) under `roles/jenkins/files/config/ssl` folder

* Port
Jenkins is listening on port 8443, `https://gitrepo.gbc.ca:8443/`

* Jenkins Plugins
The plugins install in GBC jenkins are listed in the `roles/jenkins/files/plugins.txt`

* SSH keys
The ssh key for GBC gitlab checkout is at `roles/jenkins/files/config/ssh/id_rsa`, The ssh key for gitrepo checkout is at `roles/jenkins/files/config/ssh/id_rsa_gjsun`.

## Jenkins installation

* With ansible script

`# ansible-playbook -i inventory jenkins.yaml -K`  # provide sudo password

## Jenkins start/stop

`# systemctl jenkins start`
`# systemctl jenkins stop`

## Jenkins backup

Stop jenkins. Backup the jenkins home folder(`/var/jenkins_home`) on jenkins server
