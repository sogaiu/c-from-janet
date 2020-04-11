# Calling C Code from Janet

A reproduction of the steps for calling C code from Janet in [The Janet C API](https://janet-lang.org/capi/index.html) docs.

## Prerequisites

* C compiler
* Janet source code
* `janet` and `jpm` in `PATH`

## Steps

* Clone this source:
  ```
  $ git clone https://github.com/sogaiu/c-from-janet
  ```

* Build the module:
  ```
  $ cd c-from-janet
  $ jpm build
  ```

  Look in `build` for results.

* Test from `janet`:
  ```
  $ janet
  Janet 1.9.0-dev-02f17bd  Copyright (C) 2017-2020 Calvin Rose
  janet:1:> (import build/mymod :as mymod)
  nil
  janet:2:> (mymod/myfun)
  hello from a module!
  nil
  janet:3:>
  ```
