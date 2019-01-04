
# Emacs Quick Reference

Just the basic getting around in Emacs
Full ref card here:
https://www.gnu.org/software/emacs/refcards/pdf/refcard.pdf

C == Ctrl

M == Alt

| Command | Description |
|---------|-------------|
| C-g | I didn't mean that command!|
| C-x C-f | open file |
| C-x C-s | save file |
| C-x C-w | save as |
| C-f | character forward |
| C-b | character Backward |
| C-n | line forward |
| C-p | line previous |
| C-SPC | mark |
| C-W | cut |
| M-W | copy |
| C-y | yank/paste |
| C-x 1 | one window on current buffer |
| C-x 2 | split window vertically |
| C-x 3 | split window horizontally |
| C-x o | switch to other window |
| C-x | search |
| C-x b | select buffer |
| C-x K | kill buffer |
| M-x list-packages | List packages available to install |
| C-x C-c | exit Emacs |

Modes

| M-x text-mode |
| M-x org-mode| Organizational mode |
| M-x sql-mode| SQL ANSI mode | 

Emacs init

```

(add-to-list 'exec-path "C:/Program Files (x86)/Aspell/bin/")
(setq ispell-program-name "aspell")
(setq ispell-personal-dictionary "C:/path/to/your/.ispell")
(require 'ispell)

(require 'package)
(let* ((no-ssl (and (memq system-type '(windows-nt ms-dos))
                    (not (gnutls-available-p))))
       (proto (if no-ssl "http" "https")))
  (when no-ssl
    (warn "\
Your version of Emacs does not support SSL connections,
which is unsafe because it allows man-in-the-middle attacks.
There are two things you can do about this warning:
1. Install an Emacs version that does support SSL and be safe.
2. Remove this warning from your init file so you won't see it again."))
  ;; Comment/uncomment these two lines to enable/disable MELPA and MELPA Stable as desired
  (add-to-list 'package-archives (cons "melpa" (concat proto "://melpa.org/packages/")) t)
  ;;(add-to-list 'package-archives (cons "melpa-stable" (concat proto "://stable.melpa.org/packages/")) t)
  (when (< emacs-major-version 24)
    ;; For important compatibility libraries like cl-lib
    (add-to-list 'package-archives (cons "gnu" (concat proto "://elpa.gnu.org/packages/")))))
;; Added by Package.el.
(package-initialize)

(custom-set-variables
 ;; custom-set-variables was added by Custom.
 '(custom-enabled-themes (quote (tango-dark)))
 '(package-selected-packages (quote (org))))
(custom-set-faces
 ;; custom-set-faces was added by Custom.
 )

```
