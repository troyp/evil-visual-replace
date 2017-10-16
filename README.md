# Evil Visual-Replace

Search and replace within Emacs evil-mode's visual blocks (rectangle selections).

[![MELPA](https://melpa.org/packages/evil-visual-replace-badge.svg)](https://melpa.org/#/evil-visual-replace)
[![MELPA Stable](https://stable.melpa.org/packages/evil-visual-replace-badge.svg)](https://stable.melpa.org/#/evil-visual-replace)

- [Introduction](#introduction)
- [Installation](#installation)
- [Key Bindings](#key-bindings)
- [PCRE](#pcre)
- [Known Limitations](#known-limitations)
- [License](#license)

## Introduction

The evil-visual-replace package provides versions of the emacs `query-replace`
(<kbd>M-%</kbd>) and `replace-regexp` (<kbd>C-M-%</kbd>) commands which work
for evil-mode visual-state, including visual blocks (rectangular regions).

The native emacs versions don't understand evil's visual blocks, and treat them
as normal regions.

Note that these commands are specifically intended for visual state and have
barely been tested in non-visual states. Rather than globally replacing
the native commands, it is recommended to rebind them in `evil-visual-state-map`.

## Installation

Install from melpa or by placing `evil-visual-replace.el` on your `load-path` and
executing:

    (require 'evil-visual-replace)

## Key Bindings

To replace the <kbd>M-%</kbd> and <kbd>C-M-%</kbd> bindings in
`evil-visual-state-map`, simply call:

```lisp
(evil-visual-replace-visual-bindings)
```

If you prefer to give the commands their own bindings, you can bind them like this:

```lisp
(define-key evil-visual-state-map (kbd "C-x M-%")   'evil-visual-replace-query-replace)
(define-key evil-visual-state-map (kbd "C-x C-M-%") 'evil-visual-replace-replace-regexp)
```

Or to bind them with evil-leader (eg. on <kbd>`<leader>`</kbd> <kbd>M-%</kbd> and
<kbd>`<leader>`</kbd> <kbd>C-M-%</kbd>):

```lisp
(evil-leader/set-key
  "M-%"    'evil-visual-replace-query-replace
  "M-C-%"  'evil-visual-replace-replace-regexp )
```

## PCRE

If [pcre2el](https://github.com/joddie/pcre2el) is installed, the command
`evil-visual-replace-pcre-replace-regexp` can be used instead of
`evil-visual-replace-replace-regexp`. Bind it as above, for example:

```lisp
(define-key evil-visual-state-map (kbd "C-x C-M-%") 'evil-visual-replace-pcre-replace-regexp)
```

Alternatively, pass a non-nil argument to `evil-visual-replace-visual-bindings`:

```lisp
(evil-visual-replace-visual-bindings t)
```

For consistency, this will also bind <kbd>C-M-%</kbd> to
`pcre-query-replace-regexp` for non-visual states.

## Known Limitations

Due to the line-wise processing of visual-blocks, the behaviour of <kbd>!</kbd>
is different in a visual block replace. Rather than replacing all remaining
occurrences, it only replaces those on the current line. Similarly, replacements
of newline characters will not work in visual blocks.

## License

[GPL version 2](https://www.gnu.org/licenses/old-licenses/gpl-2.0.en.html)
