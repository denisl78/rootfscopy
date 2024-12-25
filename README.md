# RootFSCopy

## info
`filefscopy` is a script to copy binaries files and dependent libraries from build stage to application container. 

## usage

In a dockerfile, typical use will look like:

```
FROM some_builder_imager AS builder_container

...

# install a bunch of dependencies
...

COPY filefscopy /usr/local/bin/
RUN filefscopy \
        /some/dependency \
        /some/dependency \
        /some/service

FROM some_base_image AS app_container

COPY --from=builder /rootfs /rootfs

```
