# zprint

__zprint__ is a library and command line tool providing a variety
of pretty printing capabilities for both Clojure code and Clojure/EDN
structures.  It can meet almost anyone's needs.  As such, it supports
the following major source code formattng approaches:

  * [__classic zprint__](./doc/types/classic.md) -- ignores whitespace 
  in function definitions and formats code with a variety of heuristics 
  to look as good as hand-formatted code 
  ([_see examples_](./doc/types/classic.md))
  * [__respect blank lines__](./doc/types/respectbl.md) -- similar to 
  classic zprint, but blank lines inside of function defintions are retained, 
  while code is otherwise formatted to look beautiful
  ([_see examples_](./doc/types/respectbl.md))
  * [__indent only__](./doc/types/indentonly.md) -- very different from 
  classic zprint -- no code ever changes lines, it is only correctly 
  indented on whatever line it was already on
  ([_see examples_](./doc/types/indentonly.md))

In addition, zprint is very handy [__to use at the REPL__](./types/repl.md).

## You can use zprint in many ways:

  * [to format whole files](./doc/using/files.md)
  * [while using an editor](./doc/using/editor.md)
  * [at the REPL](./doc/using/repl.md)
  * [from inside a Clojure(script) program](./doc/using/library.md)

## Get zprint:

  * [as a standalone binary for macOS](./doc/getting/macos.md)    _starts in <50 ms_
  * [as a standalone binary for Linux](./doc/getting/linux.md)    _starts in <50 ms_
  * [as an uberjar for any Java enabled platform](./doc/getting/uberjar.md)    _starts in several seconds_
  * [as an accelerated uberjar for any Java enabled platform](./doc/getting/appcds.md)    _starts in about 1s_
  * [as a library to use at the REPL](./doc/using/repl.md)

## Alter zprints formatting behavior:

  * [what do you do to change zprint's behavior](./doc/altering.md)

### I want to change...

  * [how user defined functions are formatted](./doc/options/fns.md)
  * [the indentation in lists](./doc/options/indent.md)
  * [the configuration to track the "community" standard](./doc/options/community.md)
  * [how blank lines in source are handled](./doc/options/blank.md)
  * [how map keys are formatted](./doc/options/maps.md)
  * [the colors used for formatting source](./doc/options/colors.md)
  * [how the second element of a pair is indented](./doc/options/pairs.md)
  * [how comments are handled](./doc/options/comments.md)
  * [anything else...](./doc/reference.md)


## Usage

### Clojure 1.9, 1.10, 1.10.1:

__Leiningen ([via Clojars](http://clojars.org/zprint))__

[![Clojars Project](http://clojars.org/zprint/latest-version.svg)](http://clojars.org/zprint)


### Clojurescript:

zprint has been tested in each of the following environments:

  * Clojurescript 1.10.520
    - figwheel 0.5.19
    - shadow-cljs 2.8.62
  * `lumo` 1.10.1
  * `planck` 2.24.0

It requires `tools.reader` at least 1.0.5, which all of the environments
above contain.

### Clojure CLI

Add the following to the `:aliases` section of `$HOME/.clojure/deps.edn`
file or to a project's `deps.edn`.

For example:

```clojure
$ cat > deps.edn <<< $'
{:aliases {:zprint {:extra-deps
                      {org.clojure/clojure
                         #:mvn{:version "1.9.0"},
                       zprint #:mvn{:version
                                      "0.5.4"}},
                    :main-opts ["-m" "zprint.main"]}},
 :deps {org.clojure/clojure #:mvn{:version "1.9.0"},
        zprint #:mvn{:version "0.5.4"}}}'
$ clj -A:zprint < deps.edn
$ clj -m zprint.main <deps.edn
```

Then you can use the following as filter and pretty printer:

```shell
cat /path/to/file.clj | clojure -A:zprint
```

### Clojure 1.8:

The last zprint release built with Clojure 1.8 was [zprint "0.4.15"].

In addition to the zprint dependency, you also need to
include the following library when using Clojure 1.8:

```
[clojure-future-spec "1.9.0-alpha17"]
```

## License

Copyright © 2016-2019 Kim Kinnear

Distributed under the MIT License.  See the file LICENSE for details.
