# upbo
> :curly_loop: Emacs Javascript Test Runner integration that support mode line report!

Upbo is the Korean pronunciation of karma.

* [Features](#features)
* [Installation](#installation)
* [Getting Started](#getting-started)

## Features

### Mode line reporting (upbo minor mode)

#### Success
![SUCCESS](https://user-images.githubusercontent.com/389021/37750016-2023624c-2dce-11e8-8dbf-449e54147f3c.png)

#### Failed
![FAILED](https://user-images.githubusercontent.com/389021/37750013-1aea8788-2dce-11e8-98e0-3a7f41c7d111.png)

#### Error
![ERROR](https://user-images.githubusercontent.com/389021/37750020-23ad1a66-2dce-11e8-871b-765269ec1549.png)

### And also terminal log view(upbo view mode)
![TERMINAL](https://user-images.githubusercontent.com/389021/37750023-2703983e-2dce-11e8-988f-22a14f95d40f.png)

## Installation
### Using package.el

You can install upbo with package-install:

`M-x package-install [RET] upbo [RET]`

Or by add following code to emacs initialize file

``` emacs-lisp
(unless (package-installed-p 'upbo)
  (package-install 'upbo))
```

If the installation have problem try package-refresh-contents:

`M-x package-refresh-contents [RET]`

### Using use-package

``` emacs-lisp
(use-package upbo
  :ensure t)
```

## Getting Started
Upbo recognizes project in the current buffer based on the git root.
You can apply project-specific test settings using the `define-upbo-test` function in your `init.el`
If you have not set up the project, upbo will find the `kama.conf.js` in git root.

Upbo uses `upbo-karma-command` variable as `karma-cli` path. If `upbo-karma-command` is nil, then by default it looks for a karma executable in global, and if it does not find it, it tries to execute in the project using npx.

### Enable upbo mode

To enable in major buffer automatically, add upbo-mode to your major buffer mode hook like this:
``` emacs-lisp
(add-hook javascript-mode-hook 'upbo-mode)
(add-hook js2-mode-hook 'upbo-mode)
```

### define-upbo-test

``` emacs-lisp
(upbo-define-test
  :path "/path/to/your/project/git/root"
  :browsers "ChromeHeadless"
  :conf-file "/path/to/your/karma-conf/karma.conf.js")
```

* `path` is project git root path
* `browsers` uses as karma `--browsers` option, Currently we support one browser for mode line reporting. if you don't have set, Upbo uses the `browsers` option of the karma configuration.
* `conf-file` is karma configuration to use in the project

### Key Bindings

#### In Minor mode

Keybinding           | Description
---------------------|---------------
<kbd>C-c, C-u, s</kbd> | Execute karma single run.
<kbd>C-c, C-u, w</kbd> | Execute karma with auto watch.
<kbd>C-c, C-u, r</kbd> | Open project upbo process view, you need to run karma first.

#### In upbo view mode

Keybinding           | Description
---------------------|---------------
<kbd>s</kbd>         | Execute karma single run.
<kbd>w</kbd>         | Execute karma with auto watch.
<kbd>k</kbd>         | Kill upbo process of current project.
<kbd>q</kbd>         | Close upbo view.



