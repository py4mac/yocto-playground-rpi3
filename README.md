# Credits
* https://github.com/cpb-/yocto-cooker
* https://www.blaess.fr/christophe/2022/02/03/5973/
* https://github.com/cpb-/stacking-yocto


# Pre-requisites

* Build docker image
A based docker image must be built previously. See https://github.com/py4mac/dotfiles

* Run docker env

```sh
docker-compose run virtual-env
```

> **_NOTE:_**  In case of issue, increase watch file using command ```sudo sysctl -n -w fs.inotify.max_user_watches=1048576```

# Build/Test x86 image

* Build image
```sh
cooker cook rpi_v2.json x86
```

* Test image
```sh
cooker  shell  x86
runqemu nographic slirp
```

login is `stack` and password is `stack`

The new binary file imported is then
```sh
noclue
```

* Exit
```sh
sudo  /sbin/halt
```


# Build/Test rpi3 image

* Build image
```sh
cooker cook rpi_v2.json rpi3
```

* Copy image on sd card
```sh
sudo dd if=./builds/build-pi3/tmp/deploy/images/raspberrypi3/core-image-base-raspberrypi3.rpi-sdimg of=/dev/sdd 
```