# DEPRECATED: Apheleia CDN

This repository previously contained assets hosted for
[Apheleia](https://github.com/raxod502/apheleia). This was so that code
formatters without binary downloads available could be installed quickly
during CI runs for Apheleia.

However, I solved that problem in a different way by setting CI to only
test changed formatters on PRs. See <https://github.com/raxod502/apheleia/pull/72>.
As a consequence, this repository is now obsolete.

## Maintenance

This section contains instructions on how to produce the artifacts in
this repository, if they ever need to be updated.

### Brittany

```
% apt install zlib-dev
% apt install cabal-install
% cabal update
% cabal install Cabal cabal-install
% export PATH="$HOME/.cabal/bin:$PATH"
% cabal install brittany --installdir=/usr/local/bin --install-method=copy --overwrite-policy=always
```

Extract the binary from `/usr/local/bin`. NB:

* Runtime dependency on GHC because it needs to read
  `/usr/lib/ghc/settings` for some reason
* This needs to be built in the same environment as it will run in,
  because of ridiculous dynamic linking shenanigans

### ocamlformat

```
% curl -fsSL --output install.sh \
    https://raw.githubusercontent.com/ocaml/opam/master/shell/install.sh
% chmod +x install.sh
% echo "" | ./install.sh
% opam init --disable-sandboxing -y
% opam install --destdir=/usr/local -y ocamlformat
```

Extract the binary from `/usr/local/bin`. NB:

* `echo` handles the unremoveable prompt from the install script
