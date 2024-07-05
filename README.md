#### Python10.xx GDAL3.8.5 PROJ9.xx Docker Image

```bash
$ export CR_PAT=YOUR_PAT
$ echo $CR_PAT | docker login ghcr.io -u trimbleava --password-stdin
$ docker build . -f Dockerfile -t ghcr.io/trimbleava/gdal-docker/py10-gdal3.8.5:latest
$ docker push ghcr.io/trimbleava/gdal-docker/py10-gdal3.8.5:latest
$ display packages: https://github.com/users/trimbleava/packages/container/package/
$ Run container and start an interactive bash session as root
```

```bash
$ docker pull ghcr.io/trimbleava/gdal-docker:main
$ docker run -it ghcr.io/trimbleava/gdal-docker:main bash
```
