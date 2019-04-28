# multi-libvterm.el

This is similiar with [multi-term.el](https://github.com/milkypostman/multi-term) but it integrates with [emacs-libvterm](https://github.com/akermu/emacs-libvterm)

# Installation

Follow [emacs-libvterm](https://github.com/akermu/emacs-libvterm) to install `emacs-libvterm`

## Install by source code

```
(use-package multi-libvterm
  :load-path "/path/to/multi-libvterm")
```

# Usage

| Command                         | Description                                     |
|---------------------------------|-------------------------------------------------|
| multi-libvterm                  | Create new terminal                             |
| multi-libvterm-next             | Switch to next terminal                         |
| multi-libvterm-prev             | Switch to previous terminal                     |
| multi-libvterm-dedicated-toggle | Toggle dedicated terminal                       |
| multi-libvterm-projectile       | Create/toggle terminal based on current project |

# For Evil users

I'm using Evil. This is my personal config to use libvterm with `evil`


```elisp
(use-package vterm
	:load-path "/path/to/emacs-libvterm"
	:config
	(setq vterm-keymap-exceptions nil)

	(add-hook 'vterm-mode-hook
			(lambda ()
			(setq-local evil-insert-state-cursor 'box)
			(evil-insert-state)))

	(define-key vterm-mode-map [return]                    #'vterm-send-return)
	(evil-declare-key 'insert vterm-mode-map (kbd "C-e") #'vterm--self-insert)
	(evil-declare-key 'insert vterm-mode-map (kbd "C-f") #'vterm--self-insert)
	(evil-declare-key 'insert vterm-mode-map (kbd "C-a") #'vterm--self-insert)
	(evil-declare-key 'insert vterm-mode-map (kbd "C-v") #'vterm--self-insert)
	(evil-declare-key 'insert vterm-mode-map (kbd "C-b") #'vterm--self-insert)
	(evil-declare-key 'insert vterm-mode-map (kbd "C-w") #'vterm--self-insert)
	(evil-declare-key 'insert vterm-mode-map (kbd "C-u") #'vterm--self-insert)
	(evil-declare-key 'insert vterm-mode-map (kbd "C-d") #'vterm--self-insert)
	(evil-declare-key 'insert vterm-mode-map (kbd "C-n") #'vterm--self-insert)
	(evil-declare-key 'insert vterm-mode-map (kbd "C-m") #'vterm--self-insert)
	(evil-declare-key 'insert vterm-mode-map (kbd "C-p") #'vterm--self-insert)
	(evil-declare-key 'insert vterm-mode-map (kbd "C-j") #'vterm--self-insert)
	(evil-declare-key 'insert vterm-mode-map (kbd "C-k") #'vterm--self-insert)
	(evil-declare-key 'insert vterm-mode-map (kbd "C-r") #'vterm--self-insert)
	(evil-declare-key 'insert vterm-mode-map (kbd "C-t") #'vterm--self-insert)
	(evil-declare-key 'insert vterm-mode-map (kbd "C-g") #'vterm--self-insert)
	(evil-declare-key 'insert vterm-mode-map (kbd "C-SPC") #'vterm--self-insert)
	(evil-declare-key 'insert vterm-mode-map (kbd "C-c") #'vterm--self-insert)
	(evil-declare-key 'normal vterm-mode-map (kbd "C-d") 'vterm--self-insert)

	(evil-declare-key 'normal vterm-mode-map (kbd ",c") #'multi-libvterm)
	(evil-declare-key 'normal vterm-mode-map (kbd ",n") #'multi-libvterm-next)
	(evil-declare-key 'normal vterm-mode-map (kbd ",p") #'multi-libvterm-prev)
	(evil-declare-key 'normal vterm-mode-map (kbd "i") 'evil-insert-resume)
	(evil-declare-key 'normal vterm-mode-map (kbd "<return>") 'evil-insert-resume)
	(evil-declare-key 'normal vterm-mode-map (kbd "o") 'evil-insert-resume))
```
