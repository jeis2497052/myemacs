# myemacs
Useful emacs settings
```
;;; https://stackoverflow.com/documentation/emacs/1960/starter-kits
;;; using spacemacs after emacs-live died in info under smtp 21 Sep 2017

(require 'package)
(add-to-list 'package-archives
             '("melpa" . "https://melpa.org/packages/") t)
(when (< emacs-major-version 24)
  ;; For important compatibility libraries like cl-lib
  (add-to-list 'package-archives '("gnu" . "https://elpa.gnu.org/packages/")))
(package-initialize)



(global-set-key (kbd "<f2>") 'eshell)
(global-set-key (kbd "<f3>") 'flyspell-buffer)
(global-set-key (kbd "<f5>") 'shell)
(global-set-key (kbd "<f8>") 'magit-status)

(defun kill-default-buffer ()
  "Kill the currently active buffer -- set to C-x k so that users are not asked which buffer they want to kill."
  (interactive)
  (let (kill-buffer-query-functions) (kill-buffer)))

(global-set-key (kbd "C-x k") 'kill-default-buffer)

;; Highlight tabulations
(setq-default highlight-tabs t)

;;; Show trailing white spaces
(setq-default show-trailing-whitespace t)

;;; Remove useless whitespaces before saving a file
(add-hook 'before-save-hook 'whitespace-cleanup)
(add-hook 'before-save-hook (lambda() (delete-trailing-whitespace)))

;;https://www.reddit.com/r/emacs/comments/56ntg0/how_to_simplifying_magit_workflow/
(defun magit-quick-commit ()
  (interactive)
  (magit-stage-modified)
  (magit-commit))

(global-set-key (kbd "C-c q") 'magit-quick-commit)



(setq user-full-name "John Eismeier"
      user-mail-address "john.eismeier@gmail.com")

(setq send-mail-function 'smtpmail-send-it)

(setq smtpmail-stream-type 'ssl)
(setq smtpmail-smtp-server "smtp.gmail.com")
(setq smtpmail-smtp-service 465)
```
