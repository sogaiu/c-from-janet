# Calling C Code from Janet

A reproduction of the steps for calling C code from Janet in [The Janet C API](https://janet-lang.org/capi/index.html) docs.

## Prerequisites

* C Compiler
  * for Linux: gcc
  * for Windows: Visual Studio or Visual Studio Build Tools (see Janet repository)
* Janet source code
* Some Janet binaries on `PATH`
  * for Linux: `janet` and `jpm`
  * for Windows: `janet.exe` and `jpm.bat`

## Linux Steps

* Clone this source:
  ```
  $ git clone https://github.com/sogaiu/c-from-janet
  ```

* Build the module:
  ```
  $ cd c-from-janet
  $ jpm build
  ```

  Look in `build` for results -- there should at least be a `mymod.so`
  file.

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

## Windows Steps

* For the steps below it is assumed that the Janet source code is
  available in `C:\Users\user\Desktop\janet` and that `janet.exe` has
  been [built](https://github.com/janet-lang/janet#windows).

* At the time of this writing, it was first necessary to copy the
  `jpm` file from the `auxbin` directory of Janet's source code to the
  `tools` sibling directory as `jpm.janet` (so copy-and-rename).  This
  was so that the `jpm.bat` in the `tools` directory could function
  appropriately.

* Clone this source:
  ```
  C:\Users\user\Desktop>git clone https://github.com/sogaiu/c-from-janet
  ```

* Open a x64 Native Tools Command Prompt and build the module:
  ```
  ...
  C:\Program Files (x86)\Microsoft Visual Studio\2019\BuildTools>cd C:\Users\user\Desktop\c-from-janet
  C:\Users\user\Desktop\c-from-janet>set JANET_HEADERPATH=C:\Users\user\Desktop\janet
  C:\Users\user\Desktop\c-from-janet>jpm build
  ```

  Look in `build` for results -- there should at least be a
  `mymod.dll` file.

* Test from `janet`:
  ```
  C:\Users\user\Desktop\c-from-janet>janet
  Janet 1.9.0-dev-local  Copyright (C) 2017-2020 Calvin Rose
  janet:1:> (import build/mymod :as mymod)
  nil
  janet:2:> (mymod/myfun)
  hello from a module!
  nil
  janet:3:>
  ```
