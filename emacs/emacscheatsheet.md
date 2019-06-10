
# Emacs Quick Reference

Just the basic getting around in Emacs
More inclusive reference card here:
https://www.gnu.org/software/emacs/refcards/pdf/refcard.pdf

C == Ctrl

M == Alt

| Command           | Description                        |
|-------------------|------------------------------------|
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
|------------------|-------------|
| u                | Up          |
| n                | Next        |
| p                | Previous    |

| Buffer Commands       | Description                               |
|-----------------------|-------------------------------------------|
| M-x kill-some-buffers | Kills buffers (but asks for confirmation) |
|                       |                                           |

Org

| Command        | Description                          |
|----------------|--------------------------------------|
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
|---------|---------------------------|
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
|-----------|------------------------------------------------------|
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
|-------------------|---------------------------|
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

| Command          | Description                     |
|------------------|---------------------------------|
| M-x magit-status | Repo status (Remapped to C-x g) |
| s                | Stage                           |
| u                | Unstage                         |
| c                | Commit                          |
| C-c C-c          | Add commit message              |
| p                | Push                            |
| M-x magit-init   | Initialize repo                 |
| M-x magit-clone  | Clone repo                      |

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
;Various
(setq-default major-mode 'text-mode)
(add-hook 'text-mode-hook 'turn-on-visual-line-mode)
(set-default 'truncate-lines t)
(add-to-list 'load-path "~/.emacs.d/lisp/")

;Save files
(setq backup-directory-alist `(("." . "~/.saves")))

;Markdown preview tool (does this work?)
(setq markdown-command "C:/Users/andre/AppData/Local/Pandoc/pandoc.exe")

;Keybindings
(global-set-key (kbd "C-x g") 'magit-status)

;;Org
(global-set-key (kbd "C-c l") 'org-store-link)
(global-set-key (kbd "C-c a") 'org-agenda)
(global-set-key (kbd "C-c c") 'org-capture)

;Use Aspell for spell check
(add-to-list 'exec-path "C:/Program Files (x86)/Aspell/bin/")
(setq ispell-program-name "aspell")
(setq ispell-personal-dictionary "C:/path/to/your/.ispell")
(require 'ispell)

(add-hook 'text-mode-hook 'flyspell-mode)
(add-hook 'prog-mode-hook 'flyspell-prog-mode)

;;MELPA (Stable) 
(require 'package)
(add-to-list 'package-archives
	     '("melpa" . "http://melpa.milkbox.net/packages/")
             ;;'("melpa-stable" . "http://stable.melpa.org/packages/")
	     t)

(autoload 'gmail2bbdb-import-file "gmail2bbdb" nil t nil)

;; Added by Package.el.  
(package-initialize)

```
Packages


| Package Name and Version | Version       | Status     | Desc.                                                  |
|--------------------------|---------------|------------|--------------------------------------------------------|
| atom-dark-theme          | 20181022.1602 | installed  | An Emacs port of the Atom Dark theme from Atom.io.     |
| buffer-flip              | 2.1           | installed  | Cycle through buffers like Alt-Tab in Windows          |
| cl-generic               | 0.3           | installed  | Forward cl-generic compatibility for Emacs<25          |
| exwm                     | 0.22          | installed  | Emacs X Window Manager                                 |
| fireplace                | 20181211.1927 | installed  | A cozy fireplace for emacs                             |
| fsm                      | 0.2.1         | installed  | state machine library                                  |
| gitconfig                | 1.0.0         | installed  | Emacs lisp interface to work with git-config variables |
| gitter                   | 1             | installed  | An Emacs Gitter client                                 |
| gmail2bbdb               | 20170423.1144 | installed  | import email and name into bbdb from vcard.            |
| jabber                   | 20180927.2325 | installed  | import email and name into bbdb from vcard.            |
| jabber                   | 20180927.2325 | installed  | A Jabber client for Emacs.                             |
| leuven-theme             | 20190107.1035 | installed  | Awesome Emacs color theme on white background          |
| magit                    | 20190104.1519 | installed  | A Git porcelain inside Emacs.                          |
| markdown-mode            | 20181229.1430 | installed  | Major mode for Markdown-formatted text                 |
| org                      | 9.2           | installed  | Outline-based notes management and organizer           |
| srv                      | 20180715.1959 | installed  | perform SRV DNS requests                               |
| sublimity                | 20160629      | installed  | smooth-scrolling, minimap and distraction-free mode    |
| w3m                      | 20181022.855  | installed  | an Emacs interface to w3m                              |
| xkcd                     | 1.1           | installed  | View xkcd from Emacs                                   |
| xterm-color              | 1.7           | installed  | ANSI & XTERM 256 color support                         |
| zone-rainbow             | 20160120.1334 | installed  | Zone out with rainbow                                  |
| zone-sl                  | 20160201.1210 | installed  | Zone out with steam locomotives.                       |
| async                    | 20181224.454  | dependency | Asynchronous processing in Emacs                       |
| dash                     | 20180910.1856 | dependency | A modern list library for Emacs                        |
| git-commit               | 20190102.107  | dependency | Edit Git commit messages                               |
| magit-popup              | 20181204.2031 | dependency | Define prefix-infix-suffix command combos              |
| moz                      | 20150805.1706 | dependency | Lets current buffer interact with inferior mozilla.    |
| popwin                   | 20150315.1300 | dependency | Popup Window Manager.                                  |
| with-editor              | 20181113.1845 | dependency | Use the Emacsclient as $EDITOR                         |
| xelb                     | 0.17          | dependency | X protocol Emacs Lisp Binding                          |
