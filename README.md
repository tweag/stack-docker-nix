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
```

[stack]: https://haskellstack.org
[stack-docker]: https://docs.haskellstack.org/en/stable/docker_integration/#configuration
[stack-nix]: https://docs.haskellstack.org/en/stable/nix_integration/#configuration

## License

This project is hereby dedicated to the public domain, using the
[CC0][cc0] public domain dedication.

[cc0]: https://creativecommons.org/publicdomain/zero/1.0/
