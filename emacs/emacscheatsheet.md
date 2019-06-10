
# Emacs Quick Reference

Just the basic getting around in Emacs
More inclusive reference card here:
https://www.gnu.org/software/emacs/refcards/pdf/refcard.pdf

C == Ctrl

M == Alt

| Command           | Description                        |
|-------------------+------------------------------------|
| C-g               | Abort!                             |
| C-f               | character forward                  |
| C-b               | character Backward                 |
| C-n               | line forward                       |
| C-p               | line previous                      |
| C-v               | page down                          |
| C-M-v             | next buffer page down              |
| C-SPC             | mark                               |
| C-W               | cut                                |
| M-W               | copy                               |
| C-y               | yank/paste                         |
| C-x C-f           | open file                          |
| C-x C-s           | save file                          |
| C-x C-w           | save as                            |
| C-x 1             | one window on current buffer       |
| C-x 2             | split window vertically            |
| C-x 3             | split window horizontally          |
| C-x o             | switch to other window             |
| C-x               | search                             |
| C-x b             | select buffer                      |
| C-x K             | kill buffer                        |
| M-x list-packages | list packages available to install |
| C-x C-c           | exit Emacs                         |
| C-h i             | Info browser                       |

| Info Browser Nav | Description |
|------------------+-------------|
| u                | Up          |
| n                | Next        |
| p                | Previous    |

| Buffer Commands       | Description                               |
|-----------------------+-------------------------------------------|
| M-x kill-some-buffers | Kills buffers (but asks for confirmation) |
|                       |                                           |

Org

| Command        | Description                          |
|----------------+--------------------------------------|
| M-RET          | New heading                          |
| M-RET          | New heading at end                   |
| TAB            | Cycle headings                       |
| S-TAB          | Cycle global (Overview-Contents-All) |
| M-LEFT         | Promote heading                      |
| M-S-LEFT       | Promote subtree                      |
| M-Down         | Move subtree down                    |
| C-c ^          | Sort                                 |
| C-c n s        | Narrow to subtree                    |
| C-c C-t        | TODO state                           |
| C-c .          | Insert Date                          |
| M-x org-agenda | Agenda dispatcher                    |
| C-c .          | Add date (S-left to pick day         |
| C-c C-x C-w    | Cut subtree                          |                             

| Command (Global) | Description    |
|------------------+----------------|
| C-c c            | Org capture    |
| C-c a            | Org agenda     |
| C-c l            | Org store link |

Folder Navigation (Directory Editor)

| Command | Description               |
|---------+---------------------------|
| C-x d   | Open Directory            |
| C-x 4 d | Directory in other frame  |
| C-x 5 d | Directory in other window |
| q       | close window              |
| d       | Mark for deletion         |
| u       | Unmark                    |
| x       | Delete File(s)            |
| C       | Copy File(s)              |
| D       | Delete                    |
| +       | Make directory            |
| C-x C-q | Edit file/folder names    |

Gnus

| Command   | Description                                          |
|-----------+------------------------------------------------------|
| M-guns    | Start Gnus                                           |
| L         | List all email groups (From cache. Use AA otherwise) |
| u         | Subscribe to group                                   |
| g         | Refresh                                              |
| q         | Quit                                                 |
| R         | Reply with quote (r without)                         |
| S W       | Wide Reply with quoted text                          |
| C-c C-c   | Send message                                         |
| B-del     | Delete article/email                                 |
| B-m       | Move article/email                                   |
| C-c RET f | Attach file                                          |

Spelling

| Command           | Description               |
|-------------------+---------------------------|
| M-$               | Spell check selection     |
| M-x ispell-buffer | Spell check entire buffer |
| <SPC>             | Skip this word            |
| a                 | Accept word               |
| A                 | Accept word this buffer   |
| r                 | Replace                   |

Shell

| Command | Description |
|---------|-------------|
| M-x shell | New shell |
| C-u M-x  | Additional new shell|
| C-up | Previous command |

Magit

| Command | Description |
|---------|-------------|
| M-x magit-status| Repo status (Remapped to C-x g)|
| s | Stage |
| u | Unstage|
| c | Commit |
| p | Push |

Modes

| Command | Description |
|---------|-------------|
| M-x text-mode |
| M-x org-mode| Organizational mode |
| M-x sql-mode| SQL ANSI mode | 

Zoning

| Command | Description |
|---------|-------------|
| M-x zone-sl | loco |
| M-x zone-rainbow | rainbow |
| M-x fireplace | a cozy fire |

Emacs init

```

;(desktop-save-mode l)
;(setq create-lockfiles nil)
(setq backup-directory-alist `(("." . "~/.saves")))


;Keybindings
(global-set-key (kbd "C-x g") 'magit-status)

;Use Aspell
(add-to-list 'exec-path "C:/Program Files (x86)/Aspell/bin/")
(setq ispell-program-name "aspell")
(setq ispell-personal-dictionary "C:/path/to/your/.ispell")
(require 'ispell)

;;MELPA (Stable)
(require 'package)
(add-to-list 'package-archives
             '("melpa-stable" . "http://stable.melpa.org/packages/") t)

;; Added by Package.el.  
(package-initialize)

(custom-set-variables
 ;; custom-set-variables was added by Custom.
 ;; If you edit it by hand, you could mess it up, so be careful.
 ;; Your init file should contain only one such instance.
 ;; If there is more than one, they won't work right.
 '(custom-enabled-themes (quote (tango-dark)))
 '(display-time-mode t)
 '(package-selected-packages
   (quote
    (buffer-flip gitconfig ## zone-sl zone-rainbow magit dad-joke fireplace markdown-mode org)))
 '(tool-bar-mode nil))
(custom-set-faces
 ;; custom-set-faces was added by Custom.
 ;; If you edit it by hand, you could mess it up, so be careful.
 ;; Your init file should contain only one such instance.
 ;; If there is more than one, they won't work right.
 )

```
Emacs packages

| Package Name and Version|
|-------------------------|
|async-20181224.454|
|buffer-flip-2.1|
|dad-joke-20170928.658|
|dash-20180910.1856|
|fireplace-20181211.1927|
|git-commit-20190102.107|
|gitconfig-1.0.0|
|magit-20190104.1519|
|magit-popup-20181204.2031|
|markdown-mode-20181229.1430|
|org-9.2|
|with-editor-20181113.1845|
|zone-rainbow-20160120.1334|
|zone-sl-20160201.1210|
