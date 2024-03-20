# Instructions to create a new image. 
example used ubuntu-20-04

navigate to /var/lib/libvirt/images/virl-base-images/
copy desired image
```
cp -a ubuntu-20-04-<date> <target name>

```
cd into newly created file and edit yaml file
- change yaml file name to match vm directory
- edit yaml file contents to
  - name
  - version
  - readonly = false

restart cml service

```
systemctl restart virl2.target

```

log into cml and start lab/ start vm 

# update and add any packages to customize the node. 

```
sudo -E -s
apt update && apt upgrade -y 
apt install iperf3 mtr net-tools

```

# find lab id then navigate to /var/loca/virl2/images
cd into node by id
# nodedisk_0 contains changes to node. 
```
file nodedisk_0
```
commit image to def
```
qemu-im commit nodedisk_0
```
