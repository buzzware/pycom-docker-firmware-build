# pycom-docker-firmware-build

In particular, the changes are :
* only the micropython-sigfox-git-tag parameter is required. The esp-idf-git-tag 
will be extracted unless provided. It is recommended that you don't provide it to 
use the extracted value for IDF_HASH.
* micropython-sigfox-git-tag and esp-idf-git-tag can be anything normally given to git 
checkout eg. a commit hash, and don't have to be a branch or tag.
* it isn't required to provide any python code to include in the build

### usage:


# Tool for building MicroPython firmware, and optionally adding your MicroPython code frozen in the flash

### usage:
```
docker build -t buzzware/pycom-docker-firmware-build . && sudo docker run -v `pwd`:/opt/frozen -it buzzware/pycom-docker-firmware-build build board-type your-project-version-code [micropython-sigfox-git-tag] [esp-idf-git-tag]
```
where board in `WIPY LOPY SIPY GPY FIPY LOPY4` and your-project-version-code is a tag for your project eg. 
output file example: `output/LoPy-1.20.2.rc10-demo.tar.gz`

### example:
```
cd pycom-docker-fw-build
docker build -t buzzware/pycom-docker-firmware-build . && docker run -v `pwd`:/opt/frozen -it buzzware/pycom-docker-firmware-build build LOPY demo v1.20.2.rc10
```



### example:

If you have your MicroPython project in the current directory `.` just type:

```
sudo docker run -v `pwd`:/opt/frozen -it buzzware/pycom-docker-firmware-build  build LOPY4 myproject
```
For building against a specific revision (ex:v1.20.0.rc0 idf_v3.1) you can use:
```
sudo docker run -v `pwd`:/opt/frozen -it buzzware/pycom-docker-firmware-build  build FIPY myproject v1.20.0.rc0 idf_v3.1
```


### note:

The Frozen code implementation does support sub-directories in MicroPython code.

The Frozen code implementation does not support adding assets (ex: db files, json,)

### re-generate this buzzware/pycom-docker-firmware-build docker image:

```
docker build -t buzzware/pycom-docker-firmware-build .
```
