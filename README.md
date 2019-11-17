# fizzbuzzgo-bosh-release

A Bosh release of a very simple [Go app](https://github.com/irbekrm/FizzBuzzGo). Created for practice purposes.

## Creating (this) Bosh release

1. `bosh init-release --dir fizzbuzzgo-bosh-release --git`

2. Link the source code of FizzBuzzGo app as a Git submodule. Since the app is a Go package, set the path to match Go import path for this package (`github.com/irbekrm/FizzBuzzGo`) to make it easier to build the app at compile time.

```cd fizzbuzzgo-bosh-release

      cd src

      git submodule add git@github.com:irbekrm/FizzBuzzGo.git github.com/irbekrm/FizzBuzzGo
      
      cd ..
```
