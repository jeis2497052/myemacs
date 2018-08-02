# myemacs from summer 2018 with prelude

```
(global-set-key (kbd "<f2>") 'eshell)
(global-set-key (kbd "<f5>") 'shell)
(defun kill-default-buffer ()
  "Kill buffer without prompt"
  (interactive)
  (let (kill-buffer-query-functions) (kill-buffer)))

(global-set-key (kbd "C-x k") 'kill-default-buffer)
(set-scroll-bar-mode 'nil)
;;;(setq electric-pair-mode 'enabled)
(electric-pair-mode 1)
(blink-cursor-mode 1)


;; This is needed to allow msmtp to do its magic:
(setq message-sendmail-f-is-evil 't)

;;need to tell msmtp which account we're using
(setq message-sendmail-extra-arguments '("--read-envelope-from"))
(setq message-send-mail-function 'message-send-mail-with-sendmail)
;; we substitute sendmail with msmtp
(setq sendmail-program "/usr/bin/msmtp")
;;need to tell msmtp which account we're using
(setq message-sendmail-extra-arguments '("-a" "john.eismeier"))
;; you might want to set the following too
(setq mail-host-address "gmail.com")
(setq user-full-name "John E")
(setq user-mail-address "john.eismeier@gmail.com")

```



#Useful emacs settings


```elisp
;;; package --- Summary
;;; Commentary:
;;; https://stackoverflow.com/documentation/emacs/1960/starter-kits
;;; using spacemacs after emacs-live died in info under smtp 21 Sep 2017

;;;(require 'package)
;;; Code:


(global-set-key (kbd "<f2>") 'eshell)
(global-set-key (kbd "<f3>") 'flyspell-buffer)
(global-set-key (kbd "<f4>") 'highlight-symbol)
(global-set-key (kbd "<f5>") 'shell)
(global-set-key (kbd "<f8>") 'magit-status)
(global-set-key (kbd "<f9>") 'delete-trailing-whitespace)

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
;;;(add-hook 'before-save-hook 'whitespace-cleanup)
;;;(add-hook 'before-save-hook (lambda() (delete-trailing-whitespace)))

;;https://www.reddit.com/r/emacs/comments/56ntg0/how_to_simplifying_magit_workflow/
(defun magit-quick-commit ()
  (interactive)
  (magit-stage-modified)
  (magit-commit))

(global-set-key (kbd "C-c q") 'magit-quick-commit)

;;;https://www.railstutorial.org/book/beginning
;;;https://www.wpi.edu/sites/default/files/docs/Offices/Human-Resources/Medical-Insurance-Matrix-FY2018.pdf
;;;https://github.com/puppetlabs/r10k/blob/master/doc/dynamic-environments/quickstart.mkd

(setq user-full-name "John Eismeier"
      user-mail-address "john.eismeier@gmail.com")

;;; https://superuser.com/questions/476714/how-to-configure-emacs-smtp-for-using-a-secure-server-gmail/476715
;;;(setq send-mail-function 'smtpmail-send-it)
;;;(setq smtpmail-stream-type 'ssl)
;;;(setq smtpmail-smtp-server "smtp.gmail.com")
;;;(setq smtpmail-smtp-service 465)


;;;(setq smtpmail-auth-credentials
;;;      (expand-file-name "~/.authinfo")
;;;      smtpmail-debug-info t)

(require 'smtpmail)

;;; https://www.emacswiki.org/emacs/NoTabs
(setq-default indent-tabs-mode nil)

;;; https://github.com/mooz/js2-mode/issues/163
;;;(setq js2-idle-timer-delay 2)
(provide 'startnml)
;;; startnml.el ends here

```
