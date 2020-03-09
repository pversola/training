# Command
`ceph -s`

`ceph -w`

`ceph osd tree`

`ceph osd ls`

`ceph osd pool ls`

Disable ceph automatic  
`ceph osd set noout`

Enable ceph automatic   
`ceph osd unset noout`

`ceph osd pool ls detail`   
`ceph osd pool <POOL-NAME> <PARAMETER> <VALUE>`   
EX   
- `ceph osd pool cephfs_data size 3`
- `ceph osd pool set .rgw.root pg_num 200`
- `ceph osd pool set .rgw.root pgp_num 200`