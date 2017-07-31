## Docker Filebeat Image

[Filebeat](https://www.elastic.co/products/beats/filebeat) is a lightweight shipper for logs. This Docker Filebeat image to provide convenient way to test your log messages from console input (stdin), parse them via json codec and finally display them on console (stdout) as well.

### Filebeat Version
* [5.5.1, latest (Dockerfile)](https://github.com/chhuang0123/docker_image_filebeat/blob/master/5.5.1/Dockerfile)

### Features
* Support console input immediately
* Support [console output](https://www.elastic.co/guide/en/beats/filebeat/current/console-output.html) (codec.json)
* Support multiple filebeat configuration files (/conf.d)
    * [config_dir](https://www.elastic.co/guide/en/beats/filebeat/current/configuration-global-options.html): the full path to the directory that contains additional configuration files.

### How to Run?

```
# interactive mode
$ docker run -it chhuang/filebeat:5.5.1

```

When docker container is created. You could paste you log message on console and press ENTER key. It will parse your log message and output on console.

#### Run Example:
<script type="text/javascript" src="https://asciinema.org/a/Rt6F99fKOUUnLhuF0CHWdln4M.js" id="asciicast-Rt6F99fKOUUnLhuF0CHWdln4M" async></script>


### How to use your configuration files?

```
$ docker run \
  -v /path/to/config_folder:/conf.d \
  chhuang/filebeat:5.5.1
```

Or, you could customize it on your Dockerfile:

```
# Dockerfile
FROM chhuang/filebeat:5.5.1
COPY /path/to/config_folder /conf.d

$ docker build -t namespace/repo .
$ docker run namespace/repo

```


### Reference:
* [Filebeat configuration details](https://www.elastic.co/guide/en/beats/filebeat/current/filebeat-configuration-details.html)

