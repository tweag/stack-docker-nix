# Provision Haskell Stack Docker images using Nix

This is a Docker image suitable for use with [Stack][stack]. It uses
a `shell.nix` file for specifying what software packages to provision,
so that `stack --nix` (see [here][stack-nix]) and `stack --docker`
(see [here][stack-docker]) use the same specification.

To use this as a base image, add the following to your `Dockerfile`:

```
FROM tweag/stack-docker-nix

ADD shell.nix /
# Clean up non-essential downloaded archives after provisioning a shell.
RUN nix-shell /shell.nix --indirect --add-root /nix-shell-gc-root \
    && nix-collect-garbage
RUN IN_NIX_SHELL=1 nix-instantiate \
    --add-root /shell.drv --indirect /shell.nix \
    && nix-collect-garbage
```

New versions of this image are pushed to [DockerHub][dockerhub-image]
every time the `master` branch is updated.

[dockerhub-image]: https://hub.docker.com/r/tweag/stack-docker-nix/
[stack]: https://haskellstack.org
[stack-docker]: https://docs.haskellstack.org/en/stable/docker_integration/#configuration
[stack-nix]: https://docs.haskellstack.org/en/stable/nix_integration/#configuration

## License

To the extent possible under law, the author(s) have dedicated all
copyright and related and neighboring rights to this software to the
public domain worldwide. This software is distributed without any
warranty.

See the [CC0][cc0] public domain dedication for more information.

[cc0]: https://creativecommons.org/publicdomain/zero/1.0/
