## What's this project?
It is a minor mode for Emacs, enabling fast/direct cursor-moving in current view.

## Is there a demo?
Yes, here is one <http://dl.dropbox.com/u/3254819/AceJumpModeDemo/AceJumpDemo.htm>

## Where does minor mode come from ?
 
  The inspiration for AceJump comes from a vim plugin called EasyMotion. EasyMotion provides a much simpler way to use motions in vim. It takes the <number> out of <number>w or <number>f{char} by highlighting all possible choices and allowing you to press one key to jump directly to the target. So I decided to write something similar for Emacs.

So I must thank:

  Bartlomiej P.    for his PreciseJump

  Kim Silkebækken  for his EasyMotion


## What's ace-jump-mode ?

  ace-jump-mode is an fast/direct cursor location minor mode. It will create the N-Branch search tree internally and marks all the possible positions with predefined keys in the current view. Allowing you to move to the character/word/line almost directly.


## What is implemented now ?

  I don't implement everything from EasyMotion.  I've tried to make AceJump as simple as possible, and you shouldn't need to spend more than 2 minutes to learn how to use it. There are only three sub-modes, which can help you to quickly move to a specific character, word, and (non-empty) line. Enjoy it.

Of course, if you have any cool suggestion, feel free to tell me at anytime. I will put that to top of my TODO list :D

## How to install it?

Add the following code to your init file, of course you can bind ace-jump-mode to a key of your choice.

    (add-to-list 'load-path "which-folder-ace-jump-mode-file-in/")
    (require 'ace-jump-mode)
    (define-key global-map (kbd "C-c SPC") 'ace-jump-mode)
    
    ;;If you also use viper mode :
    (define-key viper-vi-global-user-map (kbd "SPC") 'ace-jump-mode)


For more detail, see the help of `ace-jump-mode'.

## How to use it?
If you use the default configuration, which binds to "C-c SPC".

"C-c SPC" ==>  ace-jump-word-mode

>enter first character of a word, select the highlighted key to move to it.

"C-u C-c SPC" ==>  ace-jump-char-mode

>enter a character for query, select the highlighted key to move to it.

"C-u C-u C-c SPC" ==>  ace-jump-line-mode

>each non-empty line will be marked, select the highlighted key to move to it.




