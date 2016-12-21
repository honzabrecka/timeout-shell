# timeout-shell [![Clojars Project](https://img.shields.io/clojars/v/timeout-shell.svg)](https://clojars.org/timeout-shell)

A library that works the same way as [clojure.java.shell/sh](https://clojuredocs.org/clojure.java.shell/sh) does, but with ability to specify timeout.

Requires Java 1.8 as it depends on the `java.lang.Process.waitFor(long timeout, TimeUnit unit)` method internally.

## Installation

```clj
[timeout-shell "1.0.0"]
```

## Use

```clj
(require '[jx.java.shell :refer [timeout-sh]])

(timeout-sh 10 "sleep" "2")
; -> after ~2 seconds it returns {:exit 0, :out "", :err "", :timeout false}

(timeout-sh 2 "sleep" "10")
; -> after ~2 seconds it returns {:exit 1, :out "", :err "", :timeout true}
```
