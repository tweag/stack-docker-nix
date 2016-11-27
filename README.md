# Provision Haskell Stack Docker images using Nix

This is a Docker image suitable for use with [Stack][stack]. It uses
a `shell.nix` file for specifying what software packages to provision,
so that `stack --nix` (see [here][stack-nix]) and `stack --docker`
(see [here][stack-docker]) use the same specification.

[stack]: https://haskellstack.org
[stack-docker]: https://docs.haskellstack.org/en/stable/docker_integration/#configuration
[stack-nix]: https://docs.haskellstack.org/en/stable/nix_integration/#configuration

## License

Copyright (c) 2016 EURL Tweag.

All rights reserved.

sparkle is free software, and may be redistributed under the terms
specified in the [LICENSE](LICENSE) file.

## About

![Tweag I/O](http://i.imgur.com/0HK8X4y.png)

sparkle is maintained by [Tweag I/O](http://tweag.io/).

Have questions? Need help? Tweet at
[@tweagio](http://twitter.com/tweagio).
