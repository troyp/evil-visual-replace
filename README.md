# Evil Visual-Replace

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

Or to bind them with evil-leader (eg. on <kbd>leader</kbd><kbd>M-%</kbd> and
<kbd>leader</kbd><kbd>C-M-%</kbd>):

```lisp
(evil-leader/set-key
  "M-%"    'evil-visual-replace-query-replace
  "M-C-%"  'evil-visual-replace-replace-regexp )
```

## License

[GPL version 2](https://www.gnu.org/licenses/old-licenses/gpl-2.0.en.html)
