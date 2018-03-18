# upbo
> :curly_loop: Emacs karma integration that support mode line report!
Upbo is the Korean pronunciation of karma.

* [Features](#Features)
* [Installation](#Installation)
* [Getting Started](#Getting Started)
* [Caveat](#Caveat)

## Features

### Mode line reporting

### And also terminal log view

## Installation

## Getting Started
Upbo recognizes project in the current buffer based on the git root.
You can apply project-specific test settings using the `define-upbo-test` function
If you have not set up the project, upbo will find the `kama.conf.js` in git root.

Upbo uses `upbo-karma-command` variable as `karma-cli` path. If `upbo-karma-command` is nil, then by default it looks for a karma executable in global, and if it does not find it, it tries to execute in the project using npx.

### define-upbo-test

``` emacs-lisp
(upbo-define-test
  :path "/path/to/your/project/git/root"
  :browsers "ChromeHeadless"
  :conf-file "/path/to/your/karma-conf/karma.conf.js")
```

* `path` is project git root path
* `browsers` uses as karma `--browsers` option, Currently we support one browser for mode line reporting.
* `conf-file` is karma configuration to use in the project

### Key Bindings

