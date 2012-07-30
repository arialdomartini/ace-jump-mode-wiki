## What's this project?
Ace jump mode is a minor mode of emacs, which help you to move the cursor within Emacs. 

You can move your cursor to **any exact position** (across window and frame ) in emacs by using only **3 times key press**. 

Have a try and I am sure you will love it.

## Is there a demo?
Yes, here is a demo for version 1.0. [Demo](http://dl.dropbox.com/u/3254819/AceJumpModeDemo/AceJumpDemo.htm), it can show you the basic usage of ace jump mode.

Thanks emacsrocks website, they make a great show to ace jump mode, refer to [here](http://www.youtube.com/watch?feature=player_embedded&v=UZkpmegySnc#!)

## What's new in 2.0 version?
In 1.0 version, ace jump mode can only work in current window.

However, this limitation has already been broken in 2.0 version.  With
ace jump mode 2.0, you can jump to any position you wish across the
bounder of window(c-x 2/3) and even frame(c-x 5).


## Where does the inspiration come from ?
 
  The inspiration for AceJump comes from a vim plugin called EasyMotion, which attract me a lot when I first meet it.
 So I decided to implement it in elisp for Emacs, and make it more powerful.

So here I want to thank to:

> Bartlomiej P.    for his PreciseJump

> Kim Silkebækken  for his EasyMotion

## How to install it?

Add the following code to your init file, of course you can bind ace-jump-mode to a key of your choice.

    (add-to-list 'load-path "which-folder-ace-jump-mode-file-in/")
    (require 'ace-jump-mode)
    (define-key global-map (kbd "C-c SPC") 'ace-jump-mode)
    (define-key global-map (kbd "C-x SPC") 'ace-jump-mode-pop-mark)
    
    ;;If you also use viper mode :
    (define-key viper-vi-global-user-map (kbd "SPC") 'ace-jump-mode)
    ;;If you use evil
    (define-key evil-normal-state-map (kbd "SPC") 'ace-jump-mode)


For more detail, see the help of ace-jump-mode ( c-h f ace-jump-mode )

## How to use it?
If you use the default configuration, which binds to "C-c SPC".

"C-c SPC" ==>  ace-jump-word-mode

>enter first character of a word, select the highlighted key to move to it.

"C-u C-c SPC" ==>  ace-jump-char-mode

>enter a character for query, select the highlighted key to move to it.

"C-u C-u C-c SPC" ==>  ace-jump-line-mode

>each non-empty line will be marked, select the highlighted key to move to it.

## I want to know more about customized configuration?
See [FAQ ](http://github.com/winterTTr/ace-jump-mode/wiki/AceJump-FAQ)

