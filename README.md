# flymake-ansible-lint.el - A Flymake backend for ansible-lint
[![MELPA](https://melpa.org/packages/flymake-ansible-lint-badge.svg)](https://melpa.org/#/flymake-ansible-lint)
![Build Status](https://github.com/jamescherti/flymake-ansible-lint.el/actions/workflows/ci.yml/badge.svg)
![License](https://img.shields.io/github/license/jamescherti/flymake-ansible-lint.el)
![](https://raw.githubusercontent.com/jamescherti/flymake-ansible-lint.el/main/.images/made-for-gnu-emacs.svg)

The `flymake-ansible-lint` Emacs package provides a Flymake backend for `ansible-lint`.

## Requirements

- [ansible-lint](https://github.com/ansible/ansible-lint) >= 6.0.0

## Installation

To install the `flymake-ansible-lint` from MELPA:

1. If you haven't already done so, [add MELPA repository to your Emacs configuration](https://melpa.org/#/getting-started).

2. Add the following code to your Emacs init file to install `flymake-ansible-lint` from MELPA:
```emacs-lisp
(use-package flymake-ansible-lint
  :ensure t
  :commands flymake-ansible-lint-setup
  :hook (((yaml-ts-mode yaml-mode) . flymake-ansible-lint-setup)
         ((yaml-ts-mode yaml-mode) . flymake-mode)))
```

## customize

You can configure `ansible-lint` parameters using the `flymake-ansible-lint-args` variable:

```emacs-lisp
(setq flymake-ansible-lint-args '("--offline"
                                  "-x" "run-once[play],no-free-form"))
```

## License

The `flymake-ansible-lint` Emacs package has been written by [James Cherti](https://www.jamescherti.com/) and is distributed under terms of the GNU General Public License version 3, or, at your choice, any later version. This package uses flymake-quickdef, by Karl Otness.

Copyright (C) 2024 James Cherti

This program is free software: you can redistribute it and/or modify it under the terms of the GNU General Public License as published by the Free Software Foundation, either version 3 of the License, or (at your option) any later version. This program is distributed in the hope that it will be useful, but WITHOUT ANY WARRANTY; without even the implied warranty of MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE. See the GNU General Public License for more details. You should have received a copy of the GNU General Public License along with this program.

## Frequently asked questions

### Why are some ansible-lint error messages truncated?

This issue is a known bug in `ansible-lint`, not in `flymake-ansible-lint`.

It is `ansible-lint` that cuts off error messages:
```
$ ansible-lint -p test.yaml
test.yaml:5: yaml[truthy]: Truthy value should be one of
```

In future versions of `flymake-ansible-lint`, the author plans to utilize `ansible-lint`'s JSON output. This change will enable the parsing of structures like:
```
$ ansible-lint test.yaml -f json
[{"type": "issue", "check_name": "yaml[truthy]", "categories": ["formatting", "yaml"],
"url": "https://ansible-lint.readthedocs.io/rules/yaml/", "severity": "info",
"level": "error", "description": "Truthy value should be one of \\[false, true]",
"fingerprint": "******************************************",
"location": {"path": "test.yaml", "lines": {"begin": 5}}}]
```

The author will need to refactor the code to implement this. Contributions are welcome.

## Links

- [flymake-ansible-lint.el @GitHub](https://github.com/jamescherti/flymake-ansible-lint.el)
- [flymake-ansible-lint.el @MELPA](https://melpa.org/#/flymake-ansible-lint)
- [ansible-lint @GitHub](https://github.com/ansible/ansible-lint)

Other Emacs packages by the same author:
- [minimal-emacs.d](https://github.com/jamescherti/minimal-emacs.d): This repository hosts a minimal Emacs configuration designed to serve as a foundation for your vanilla Emacs setup and provide a solid base for an enhanced Emacs experience.
- [outline-indent.el](https://github.com/jamescherti/outline-indent.el): An Emacs package that provides a minor mode that enables code folding and outlining based on indentation levels for various indentation-based text files, such as YAML, Python, and other indented text files.
- [easysession.el](https://github.com/jamescherti/easysession.el): Easysession is lightweight Emacs session manager that can persist and restore file editing buffers, indirect buffers/clones, Dired buffers, the tab-bar, and the Emacs frames (with or without the Emacs frames size, width, and height).
- [vim-tab-bar.el](https://github.com/jamescherti/vim-tab-bar.el): Make the Emacs tab-bar Look Like Vim’s Tab Bar.
- [elispcomp](https://github.com/jamescherti/elispcomp): A command line tool that allows compiling Elisp code directly from the terminal or from a shell script. It facilitates the generation of optimized .elc (byte-compiled) and .eln (native-compiled) files.
- [tomorrow-night-deepblue-theme.el](https://github.com/jamescherti/tomorrow-night-deepblue-theme.el): The Tomorrow Night Deepblue Emacs theme is a beautiful deep blue variant of the Tomorrow Night theme, which is renowned for its elegant color palette that is pleasing to the eyes. It features a deep blue background color that creates a calming atmosphere. The theme is also a great choice for those who miss the blue themes that were trendy a few years ago.
- [Ultyas](https://github.com/jamescherti/ultyas/): A command-line tool designed to simplify the process of converting code snippets from UltiSnips to YASnippet format.
- [flymake-bashate.el](https://github.com/jamescherti/flymake-bashate.el): A package that provides a Flymake backend for the bashate Bash script style checker.
