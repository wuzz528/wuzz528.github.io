---
update: 2017-12-25 15:41:51 +0800
layout: post
title: "Docker Usage"
date: 2017-12-25 14:35:37 +0800
categories: docker uwsgi
---

### Run a MySQL Container 
```
docker run --name={name} -p {host port}:3306 -e MYSQL_ROOT_PASSWORD={mysql root password} -e MYSQL_ROOT_HOST=localhost -d mysql/mysql-server:{mysql version} --config-entry-key=value
```

- Check container logs  
  `docker logs {name}`
- Restore from dump files  
  `cat {dump file} | docker exec -i {name} mysql -u{user} -p{pass} {database}`
- Enter MySQL console  
  `docker exec -it {name} mysql -u{user} -p{pass}`

### Build a docker image
`docker build --force-rm=true -t {tag} {docker file directory}`

### Run a docker container with volume mount
`docker run --name={name} --privileged=true --detach=true -d {name} -h {docker hostname} --volume "/host/src":"/docker/target":rw -d {tag}`

### Run uwsgi in upstat mode in docker
`nohup uwsgi --master --emperor /etc/uwsgi/vassals --die-on-term --uid www-data --gid www-data --logto {log location} &`
