# docker-volume-backup

A simple tool for backing up volumes from Docker containers.

When I say simple, I mean it. This is basically just a Fedora image with tar
installed. In the future, I may add helper scripts, and container
introspection, and some form of automation to make the backup process less
manual.

But for now, if you have more sophisticated backup needs, look elsewhere.

# Building

To build the image, run:

```.shell
$ docker build -t volume-backup .
```

# Running

To back up a volume, run:

```.shell
$ docker run -i --rm --volumes-from=my-container ajsmith/volume-backup tar cz /path/to/volume > my-backup.tar.gz
```

To restore from a back up, run:

```.shell
$ cat my-backup.tar.gz | docker run -i --rm --volumes-from=my-container ajsmith/volume-backup /bin/bash -c "cd /; tar xz"
```

Replace `my-container` and `my-backup` with the appropriate container
identifier and backup file name, respectively.

Note: The above example requires the volume path be absolute.
