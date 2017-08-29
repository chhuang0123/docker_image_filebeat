## Docker Filebeat Image

[Filebeat](https://www.elastic.co/products/beats/filebeat) is a lightweight shipper for logs. This Docker Filebeat image to provide convenient way to test your log messages from console input (stdin), parse them via json codec and finally display them on console (stdout) as well.

### Filebeat Version
* [5.5.2, latest (Dockerfile)](https://github.com/chhuang0123/docker_image_filebeat/blob/master/5.5.1/Dockerfile)
* [5.5.1 (Dockerfile)](https://github.com/chhuang0123/docker_image_filebeat/blob/master/5.5.1/Dockerfile)

### Features
* Support console input immediately
* Support [console output](https://www.elastic.co/guide/en/beats/filebeat/current/console-output.html) (codec.json)
* Support multiple filebeat configuration files (/conf.d)
    * [config_dir](https://www.elastic.co/guide/en/beats/filebeat/current/configuration-global-options.html): the full path to the directory that contains additional configuration files.

### How to Run?

```
# interactive mode
$ docker run -it chhuang/docker_image_filebeat:latest

```

When docker container is created. You could paste you log message on console and press ENTER key. It will parse your log message and output on console.

#### Run Example:
[![demo](https://asciinema.org/a/pcRpowA31CN4TgjFVBZiVPMvG.png)](https://asciinema.org/a/pcRpowA31CN4TgjFVBZiVPMvG?autoplay=1)

### How to use your configuration files?

```
$ docker run \
  -it -v /path/to/config_folder:/conf.d \
  chhuang/docker_image_filebeat:latest
```

Or, you could customize it on your Dockerfile:

```
# Dockerfile
FROM chhuang/docker_image_filebeat:latest
COPY /path/to/config_folder /conf.d

$ docker build -t namespace/repo .
$ docker run namespace/repo

```


### Reference:
* [Filebeat configuration details](https://www.elastic.co/guide/en/beats/filebeat/current/filebeat-configuration-details.html)

