# Use zprint to format entire source files
There are several ways to use zprint to format entire source files:
## 1. High Performance Prebuilt Binaries
  * High performance: startup is fast < 50ms
  * Available for macOS and Linux
  * Does not require Java -- available as standalone binaries
  * Accepts source on stdin, produces formatted source on stdout
  * Reads configuration from `~/.zprintrc`
  * Accepts options map on command line

```
zprintm '{:width 90}` < myfile.clj > myfile.out.clj
```
Get it for:  
  * [macOS](../getting/macos.md)
  * [Linux](../getting/linux.md)

## 2. Java Uberjar
  * Works anywhere you can install Java
  * Startup in a few seconds
  * Java appcds will cache startup info, making startup about 1s
  * Accept source on stdin, produces formatted source on stdout
  * Reads configuration from `~/.zprintrc`
  * Accept options map on command line

Uberjar example:

```
java -jar zprint-filter '{:width 90}' < myfile.clj > myfile.out.clj
```
Get the: 
  * Uberjar
  * Appcds setup script (automates appcds setup)

## 3. Lein zprint
  * Leiningen plugin: `[lein-zprint "0.5.n"]`
  * Accepts configuration from `:zprint` key in project.clj
  * Will (optionally) replace existing source files with reformatted versions
  * Reads configuration from `~/.zprintrc`
  * Accept options map on command line

```
lein zprint '{:width 90}' src/myproj/*.clj
Processing file: src/myproj/myfile.clj
Processing file: src/myproj/myotherfile.clj
```
Get it: put `[lein-zprint "0.5.4"]` in the vector that is the value of
the `:plugins` key in `project.clj`:

```
(defproject zpuse "0.1.0-SNAPSHOT"
  :description "FIXME: write description"
  :url "http://example.com/FIXME"
  :license {:name "EPL-2.0 OR GPL-2.0-or-later WITH Classpath-exception-2.0"
            :url "https://www.eclipse.org/legal/epl-2.0/"}
  :plugins [[lein-zprint "0.5.4"]]
  :dependencies [[org.clojure/clojure "1.10.0"]]
  :repl-options {:init-ns zpuse.core})
```

## 4. Other approaches
Prior the prebuilt, high performance binaries (see above), a number of
approaches were created to execute in various Javascript/Clojurescript
engines.  At this point, the pre-built binaries startup as fast or faster 
and run much faster than any Javascript based zprint.
