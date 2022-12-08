---
title: Fixing Visualize Ampliseq 10
author: Ben Lorentz
date: '2022-12-08'
slug: fixing-visualize-ampliseq-10
categories: []
tags:
  - one tag
  - another tag
meta_img: images/image.png
description: Description for the page
---

### Todos for Tomorrow:

- Rebuild rocker/verse:4.2.0 to include boxboat/fixuid
- Visualize Ampliseq 
  - check diverity for boxplot visualization
  - modify uncompress diverity
  - add a new process for boxplot
- Host microbiome interaction
  - new paper
  
### Rstudio docker image

```dockerfile
FROM rocker/verse:4.2.0

# creates user "docker" with UID 1000, home directory /home/docker, and shell /bin/sh
# creates group "docker" with GID 1000

RUN addgroup --gid 1000 docker && \
    adduser --uid 1000 --ingroup docker --home /home/docker --shell /bin/sh --disabled-password --gecos "" docker

# Install fixuid in the container, ensure that root owns the file, make it execuatble, and enable the setuid bit. 
# Create the file /etc/fixuid/config.yml with two lines, user: <user> and group: <group> using the user and group from step 1.
  
RUN USER=docker && \
    GROUP=docker && \
    curl -SsL https://github.com/boxboat/fixuid/releases/download/v0.5.1/fixuid-0.5.1-linux-amd64.tar.gz | tar -C /usr/local/bin -xzf - && \
    chown root:root /usr/local/bin/fixuid && \
    chmod 4755 /usr/local/bin/fixuid && \
    mkdir -p /etc/fixuid && \
    printf "user: $USER\ngroup: $GROUP\n" > /etc/fixuid/config.yml
    
# Set the default user/group to user:group and set the entrypoint to fixuid

USER docker:docker
ENTRYPOINT ["fixuid"]

# docker run --rm -it -u 1000:1000 <image name> sh
```

This dockerfile did not work for my use case but I was able to find the [params I needed](https://rocker-project.org/images/versioned/rstudio.html)

##### 4.1.4 USERID and GROUPID

The UID and GID of the default non-root user can be changed as follows:

```bash
docker run --rm -ti -e USERID=1001 -e GROUPID=1001 -p 8787:8787 rocker/rstudio
```

### Visualize Ampliseq

#### Fix process 10 

I updated main to use qiime to generate the diversity pairwise comparisons for unifrac

visualize ampliseq rev: c1ee5fd503bba30df9705b911ca5fc853a23fa8a
ampliseq benchmark rev: 15c33da5f6243330fc5a4deda9ebe1fd63e1af80
slurm sub: 15723902

```bash
[-        ] process > ORDERIOI -
Process `UNCOMPRESSDIVMATS` declares 3 input channels but 2 were specified

 -- Check script '/home/bjl34716/.nextflow/assets/lorentzben/visualize-ampliseq/main.nf' at line: 67 or see '.nextflow.log' fi

```

Whoops I mixed up which process is which, so I decided to just flip flop since the order isn't important. 

visualize ampliseq rev: 1c476e4e8aa7304e45b455c2040329623c86f4c2
ampliseq benchmark rev: 15c33da5f6243330fc5a4deda9ebe1fd63e1af80
slurm sub: 15725716

```bash

No such variable: path

 -- Check script '/home/bjl34716/.nextflow/assets/lorentzben/visualize-ampliseq/main.nf' at line: 765 or see '.nextflow.log' f$
[-        ] process > ORDERIOI                       -
```
needed to give a pathname for uncompress div mat

visualize ampliseq rev: 3212921f62abdedf29520556b64e0abaaccc6a79
ampliseq benchmark rev: 15c33da5f6243330fc5a4deda9ebe1fd63e1af80
slurm sub: 15725970

```bash

```
### Host Microbe interaction