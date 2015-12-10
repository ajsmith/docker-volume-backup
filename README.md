# docker-volume-backup

A very simple way to back up volumes from Docker containers.

When I say simple, I mean it. This is basically just a Docker image with tar
installed. If you have more sophisticated backup needs, look elsewhere.

# Building

To build the image, run:

```.shell
$ docker build -t volume-backup .
```

# Running

To back up a volume, run:

```.shell
$ docker run -i --rm --volumes-from=my-container volume-backup /path/to/volume > my-backup.tar.gz
```

Replace `my-container` and `my-backup` with the appropriate container
identifier and backup file name, respectively.
