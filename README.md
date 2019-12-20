# conex test-repository

You need conex from master branch to use this, `opam pin add conex --dev` should do the trick!

To test `conex_verify`, you need to add the following to your `$(OPAMROOT)/config`:

```
repository-validation-command: [
  "/path/to/conex_verify_openssl" "--quorum" "%{quorum}%"
  "--trust-anchors" "%{anchors}%"
  "--repo" "%{repo}%"
  "--dir=%{dir}%" { ! incremental }
  "--patch=%{patch}%" { incremental }
  "--incremental" { incremental }
]
```

To add this repository you have to type:

```bash
$ opam repo add hannes-jackline-repo https://github.com/hannesm/jackline-opam.git 1 sha256=6b70cd24656868f22bba1ac574f4166093fa640850ccd81852915a64b6999e08
```

For a full setup:

```bash
# get opam 2.0.0 and conex via second channel
$ opam switch create --empty jackline
$ opam repo add jackline-opam git+https://github.com/hannesm/jackline-opam.git 1 sha256=6b70cd24656868f22bba1ac574f4166093fa640850ccd81852915a64b6999e08
$ opam repo --set-repos jackline-opam
$ opam install jackline
$ eval `opam env`
```
