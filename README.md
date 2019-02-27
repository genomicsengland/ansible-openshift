# ansible-openshift

Dockerfile that contains ansible, along with OpenShift CLI tools. 

Published here: https://hub.docker.com/r/bobbydvo/ansible

## To execute from Docker env:

Add an alias, so that 'ansible-playbook' actually calls a docker container:
```
alias ansible-playbook='docker run -it  -v $PWD:/app -w /app bobbydvo/ansible:latest ansible-playbook'
```

Now run Ansible playbook as above, via the alias:
```
$ ansible-playbook NGIS.yaml -i inventory.ini --tags <role_name>
```

## Executing OpenShift in the container

The oc CLI tool changed in recent releases and needs to be executed a certain way on Alpine:
```
/lib/ld-musl-x86_64.so.1 --library-path /lib /bin/oc --version
```

## Build Instructions

@TODO - currently built manually by Bobby and pushed manually to his Docker Hub

BUT:

```
docker build -t ansible .  
```

```
docker tag ansible:latest bobbydvo/ansible:latest
```

```
docker login
docker push
```