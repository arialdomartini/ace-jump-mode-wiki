## What's this project?
It is a minor mode for Emacs, enabling fast cursor-moving in current view.

## Where does minor mode come from ?
 
  When I first use EasyMotion plugin in vim. It really attract me a
lot.  EasyMotion is a insteresting plugin in vim. EasyMotion
provides a much simpler way to use some motions in vim. It takes
the <number> out of <number>w or <number>f{char} by highlighting
all possible choices and allowing you to press one key to jump
directly to the target. So I decide to write one for Emacs.


## What's ace-jump-mode ?

  ace-jump-mode is an Emacs version of the motion style in EasyMotion.
EasyMotion mode is not the first one which uses such motion style.
So, I must thank to :

  Bartlomiej P.    for his PreciseJump

  Kim Silkebækken  for his EasyMotion


## Do you implement everything from EasyMotion ?

  No, and I don't want to make ace-jump exactly the same as
EasyMotion in vim. I think the moving style itself is really cool,
so I rewrite it in emacs. But I do not mean to copy everything.

  If you have any cool suggestion, feel free to tell me at any
time.  I will put that to top of my TODO list :D

## How to start it?

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




