# Instructions to create a new image. 

This example used Ubuntu-20-04 image.

To start navigate to /var/lib/libvirt/images/virl-base-images/

Then copy desired image
```
cp -a ubuntu-20-04-<date> <target file name>
```

Change directory (cd) into newly created file and edit yaml file matching the target image name 
- change yaml file name to match vm directory
  ```
  mv ubuntu-20-04-<date>.yaml <target file name>.yaml
  ```
- edit yaml file contents to
  ```
  nano <target file name>.yaml
  ```
  - id
  - label
  - version
  - read_only: false

Restart cml service

```
systemctl restart virl2.target
```

log into cml and start lab/ start vm 

## update and add any packages to customize the node. 

```
sudo -E -s
apt update && apt upgrade -y 
apt install iperf3 mtr net-tools
```

## find lab id then navigate to /var/loca/virl2/images

cd into node by id

## nodedisk_0 contains changes to node. Use file to review contents. 

```
file nodedisk_0
```
Commit image to back to node image. This will ensure changes are saved. 

```
qemu-im commit nodedisk_0
```
