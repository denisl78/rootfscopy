# RootFSCopy

* RootFSCopy is a script to copy binaries and dependent libraries from build stage to application container. 
* Initial realese only for ubi docker images

## usage

In a dockerfile, typical use would look like:

```
FROM some_builder_imager AS builder_container

...

# install a bunch of dependencies
...

COPY rootfscopy /usr/local/bin/
RUN rootfscopy \
        /some/dependency \
        /some/dependency \
        /some/service

FROM some_base_image AS app_container

COPY --from=builder /rootfs /rootfs

```
