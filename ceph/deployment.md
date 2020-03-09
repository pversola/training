# Deploy
## Environment
- CPU 4 core
- Memory 8 GB
- Disk OS
- Disk for OSD ~ 100GB
- DIsk for OSD ~ 100GB

## Concept
RGW (RADOS GATE WAY)
- Object Storage
- for Access public (http)
- Speed low performance
- Application

RBD (RADOS BLOCK Device)
- Block Device
- for Host/VM
- for private network
- Speed High Performance
- Acesss one on one

CEPHFS
- Share drive r/w manny
- for private network

LIBRADOS
- library tools

RADOS
- Manage object transfer file to disk
- flat namespace

CRUSH 
- manage control replica object


## MGR (daemon)
ceph-mon (monitor)
- is agent
- performance is importance

ceph-mgr (manager)
- Dashboard




## Palcement Group
