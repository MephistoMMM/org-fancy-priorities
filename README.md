# Org Fancy Priorities

Org mode is great. It is powerful, versatile and customizable. Unfortunately, I
always found the task priorities functionality a bit underwhelming, not in
terms of usability, but more in the visual department.

Inspired by [https://github.com/sabof/org-bullets](org-bullets), I created a
minor mode that displays org priorities as custom strings. This mode does
**NOT** change your files in any way, it only displays the priority part of a
heading as your preferred string value.

## Screenshots

![Screenshot 1](screenshots/screenshot1.png?raw=true)
![Screenshot 2](screenshots/screenshot2.png?raw=true)

## Installation

Add the file to your load path, set the `org-fancy-priorities-list` variable, and
add a hook to load it when org-mode is loaded. The code bellow will display the
highest priority in each org file as ⚡, with the rest of the symbols following in
descending priority.

``` emacs-lisp
(require 'org-fancy-priorities)
(setq org-fancy-priorities-list '("⚡" "⬆" "⬇" "☕"))
(add-hook 'org-mode-hook 'org-fancy-priorities-mode)
```

## Customization

If you use custom priority values for different files, you can explicitly set a
different string that will be matched to each one of them. See example below:

``` emacs-lisp
(setq org-fancy-priorities-list '((?A . "❗")
                                 (?B . "⬆")
                                 (?C . "⬇")
                                 (?D . "☕")
                                 (?1 . "⚡")
                                 (?2 . "⮬")
                                 (?3 . "⮮")
                                 (?4 . "☕")
                                 (?I . "Important")))
```

The "?" before each character is needed to convert each character to its integer
value, since Characters in Elisp are just integers.
