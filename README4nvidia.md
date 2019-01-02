# nvidia-docker 支持

## 目的

在制作tensorflow镜像时，tensorflow的脚本会根据参数选择docker/nvidia-docker

为了增加nvidia-docker的支持。将jenkins的base镜像改为，tensorflow的base镜像。并在此基础上安装docker、nvidia-docker

## Dockerfile说明

1. Dockerfile-nvidia-docker-base

   基于tensorflow官方的Dockerfile，保留nvidia驱动，增加mellanox驱动，增加docker、nvidia-docker

2. Dockerfile-nvidia

   基于jenkins官方的Dockerfile，以上一步制作的镜像为base，jenkins的版本升级到2.156

3. Dockerfile-nvidia-slave-base

   基于jenkins官方的[docker-slave](https://github.com/jenkinsci/docker-slave)，以第一步的制作的镜像为base  

4. Dockerfile-nvidia-slave-jnlp

   基于jenkins官方的[docker-jnlp-slave](https://github.com/jenkinsci/docker-jnlp-slave)，以第一步的制作的镜像为base

## jenkins版本以及checksum

从下面的连接，可以获取到jenkins各个版本的war文件的checksum值。用于修改Dockerfile-nvidia里的`JENKINS_SHA`

[https://updates.jenkins-ci.org/download/war/](https://updates.jenkins-ci.org/download/war/)
