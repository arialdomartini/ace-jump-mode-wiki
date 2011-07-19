## What's this project?
It is a minor mode for Emacs, enabling fast/direct cursor-moving in current view.

## Where does minor mode come from ?
 
  I firstly see such kind of moving style is in a vim plugin called EasyMotion. It really attract me a lot. EasyMotion provides a much simpler way to use some motions in vim. It takes the <number> out of <number>w or <number>f{char} by highlighting all possible choices and allowing you to press one key to jump directly to the target. So I decide to write one for Emacs.

So I must thank to :

  Bartlomiej P.    for his PreciseJump

  Kim Silkebækken  for his EasyMotion


## What's ace-jump-mode ?

  ace-jump-mode is an fast/direct cursor location minor mode. It will create the N-Branch search tree internal and marks all the possible position with predefined keys in current view. Allowing you to move to the character/word/line almost directly.


## What do you implement now ?

  I do not implement everything from EasyMotion. Because I what to make AceJump as simple as possible, and you don’t even need to spend more than 2 minutes to learn how to use it. So now, there is only three sub-mode, which can help you to quick move to a specific character , word and (non-empty) line. Enjoy it~

Of course, if you have any cool suggestion, feel free to tell me at anytime. I will put that to top of my TODO list :D

## How to install it?

Add the following code to your init file, of course you can select the key which you prefer to.

    (add-to-list 'load-path "which-folder-ace-jump-mode-file-in/")
    (require 'ace-jump-mode)
    (define-key global-map (kbd "C-c SPC") 'ace-jump-mode)
    
    ;;If you also use viper mode :
    (define-key viper-vi-global-user-map (kbd "SPC") 'ace-jump-mode)


For more detail, see the help of `ace-jump-mode'.

## How to use it?
If you use the default configuration, which binds to "C-c SPC".

"C-c SPC" ==>  ace-jump-word-mode

>enter first char of a word, select the highlight key to move to.

"C-u C-c SPC" ==>  ace-jump-char-mode

>enter a char for query, select the highlight key to move to.

"C-u C-u C-c SPC" ==>  ace-jump-line-mode

>each non-empty line will be marked, select the highlight key to move to.




