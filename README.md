# Overview

We are going to use single shared gluster volume as backend for minio instances using NAS Gateway mode.
This ansible roles will create the following setup,
- Create a Distributed Replicated Gluster Volume (2 x 3) from 6 bricks(separate VMs), so it's 6 node cluster.
- Configure three minio instances on top of the gluster volume.

# Steps

```shell
ansible-playbook -i inventory/minio-gluster/test-env/hosts minio-gluster.yml
```

# Configuration

You need to change default values in inventory/minio-gluster/test-env/group_vars/all.yml,

E.G.
If your disk path is /dev/sdb in gluster servers, then you need to update it.
```shell
disk_path: /dev/sdb
```
Also you need to update the minio access and secret keys.
