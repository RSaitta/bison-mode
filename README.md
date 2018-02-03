# bison-mode

Bison major-mode for Emacs.

##Installation
Put the .el file in /.emacs.d/lisp. If it doesn't exist, make it.

Add the follow to your .emacs or .init.el file (whichever you have)

(add-to-list 'load-path "~/.emacs.d/lisp/")
(load "bison-mode")

For convenient c-function indexing, add

(add-hook 'bison-mode-hook 'imenu-add-menubar-index)

```
(setq imenu-create-index-function 
        (lambda ()
          (let ((end))
             (beginning-of-buffer)
             (re-search-forward "^%%")
             (forward-line 1)
             (setq end (save-excursion (re-search-forward "^%%") (point))
             (loop while (re-search-forward "^\\([a-z].*?\\)\\s-*\n?\\s-*:" end t)
                   collect (cons (match-string 1) (point))))))
```
## Changelog
### 0.4
Updated autoindenting for space efficiency. WIP

### 0.3

Added support for jison mode.

jison-mode is started automatically for .jison files

### 0.2

Update for compatibility with modern Emacsen, and removed dependencies
on some ancient packages.

Many byte-compiler fixes.

Fixed a crash on indentation.

bison-mode is now started automatically for .y and .l files.

### 0.1

Initial release.
