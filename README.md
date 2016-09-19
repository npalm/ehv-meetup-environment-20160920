# Build environment

## Setup you build eco-system
1. Install docker and docker-compose, on Mac use dinghy
  1. When using docker-machine you should create the base directory for the mount points in the vm, see `docker-compose.yml` for the mount points.
  2. An example:
```
docker-machine ssh default
sudo su
mkdir /var/lib/boot2docker/gitlab
mkdir /var/lib/boot2docker/sonar
exit
exit
```
2. Run `docker-compuse up -d` ensure you docker-engine has enought memory. You can also simply start only the services needed. For example `docker-compuse up -d gitlab gitlabrunner`.
3. Register the runner to gitlab.
```
docker exec -i -t gitlab-runner-dind1 gitlab-runner register -n \
   --docker-links 'cicd_gitlab_1:gitlab.docker'
```
4. Login to gitlab, which is available on the port mapped in the docker-compose file or on the dns name docker.gitlab when using dinghy.
5. Login to gitlab using username: "root" and password: "5iveL!fe".
6. Add your own user, setup ssh keys and so on.
7. Add your sources and run builds.
