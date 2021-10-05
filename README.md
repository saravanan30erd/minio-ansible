# Distributed MinIO Cluster Installation

## Overview

MinIO in distributed mode lets you pool multiple drives (even on different machines) into a single object storage server. As drives are distributed across several nodes, distributed MinIO can withstand multiple node failures and yet ensure full data protection.

* High availability
* Data protection
* Consistency Guarantees

## Configuration

You can change default values in `inventory/minio/group_vars/all.yml` such as `minio_access_key`, `minio_secret_key`, `dns_domain`, etc.

E.G.

```shell
disk_path: /dev/xvdb
```

## Steps

```shell
ansible-playbook -i inventory/minio/hosts minio.yml
```

# Minio Installation with GlusterFS using NAS Gateway mode

## Overview

We are going to use single shared gluster volume as backend for minio instances using NAS Gateway mode.
This ansible roles will create the following setup,
- Create a Distributed Replicated Gluster Volume (2 x 3) from 6 bricks(separate VMs), so it's 6 node cluster.
- Configure three minio instances on top of the gluster volume.

## Configuration

You can change default values in `inventory/minio-gluster/group_vars/all.yml`,

E.G.
If your disk path is /dev/sdb in gluster servers, then you need to update it.
```shell
disk_path: /dev/sdb
```
Also you need to update the minio access and secret keys.

## Steps

```shell
ansible-playbook -i inventory/minio-gluster/hosts minio-gluster.yml
```
