# Apheleia CDN

This repository contains assets hosted for
[Apheleia](https://github.com/raxod502/apheleia). This is so that code
formatters without binary downloads available can be installed quickly
during CI runs for Apheleia.

## Maintenance

This section contains instructions on how to produce the artifacts in
this repository, if they ever need to be updated.

### Brittany

```
% apt update
% apt install libtinfo-dev
% export STACK_ROOT="/usr/local/.stack"
% curl -fsSL https://get.haskellstack.org/ | sh
% stack --stack-root "$STACK_ROOT" install --local-bin-path /usr/local/bin \
    --fast --resolver lts-16.25 brittany
```

Extract the binary from `/usr/local/bin`.
