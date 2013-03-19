### I want to do something before real jump happens, is it possible?
Of course, there is already a hook for you. I give am example here:

    (add-hook 'ace-jump-mode-before-jump-hook (lambda ()
                                                (message "I am jumping")))

### I don't like to gray background, how to disable it.

    (setq ace-jump-mode-gray-background nil)

Or you can change the color by customizing `ace-jump-face-background`.

### I don't like the default move keys, is it possible to change it.
I have to remind one thing before you change the default move keys. You have to notice that the less move key you use, the more time you possibly need to press the key to reach the exact location finally. If it is possible, please use the keys not less than 10 , that can make AceJump really effective.
for example:

- you only want to use lower case character:

        (setq ace-jump-mode-move-keys
              (loop for i from ?a to ?z collect i))

- you want to use number only:

        (setq ace-jump-mode-move-keys
              (loop for i from ?0 to ?9 collect i))

The default value in AceJump:

    (setq ace-jump-mode-move-keys
          (nconc (loop for i from ?a to ?z collect i)
                 (loop for i from ?A to ?Z collect i))

### Can I use case insensitive for the AceJump mode?
You can custom the flag to this feature:

        (setq ace-jump-mode-case-fold t)

BTW,
The default setting to ace-jump-mode-case-fold is use the same value as 'case-fold-search'.


### I enter the word mode, but I want to change to char mode, is there is quick way?
Yes, now you can use `C-c C-c` to quickly change between word-mode and char-mode when you already enter one of these two mode. Of course, the query char you input will use as the default input char between each mode.

### I don't want to input the head char for word mode, is it possible to mark all the word?
Although i do not suggest to use, cause it may result in more times key press. But you can indeed do that:

        (setq ace-jump-word-mode-use-query-char nil)

### I want to use my own sub-mode sequence that triggered by different "C-u" + "C-c SPC", is it possible?
Currently, we have three sub mode, which is `char mode`, `word mode`, and `line mode`, they map to the function called `ace-jump-char-mode`, `ace-jump-word-mode`, and `ace-jump-line-mode`.

You can change the sequence by setting `ace-jump-mode-submode-list`.

For example, the default value is :

    (setq ace-jump-mode-submode-list
          '(ace-jump-word-mode              ;; the first one always map to : C-c SPC
            ace-jump-char-mode              ;; the second one always map to: C-u C-c SPC            
            ace-jump-line-mode) )           ;; the third one always map to ：C-u C-u C-c SPC

You can change the sub mode sequence as you wish.


### Is it possible to use ace jump within the current window or current frame only?
Yes, you can control the effective scope of ace jump by set `ace-jump-mode-scope`.

There is three possible value for this:

- `'global` : ace jump can work across any window and frame, this is also the default in verion 2.0
- `'frame`  : ace jump will work for the all windows in current frame.
- `'window` : ace jump will only work on current window only. This is the same behavior for 1.0 version.

### I don't want to search punctuation under word mode as default behavior
Yes, now we have an option for this:  `ace-jump-mode-detect-punc`.
Be default, its value is t, which means, when you input a punctuation under word mode, ace jump will detect it and use char mode to process this punctuation. Of course, if you do not like this behavior, you can set it to nil. And word mode will only handle the digit and alpha, and report a error when you input a punctuation.

### Why is `(global-)pop-mark` not enough, and when should I activate `ace-jump-mode-pop-mark`?
The problem is that, the original push/pop mark facility cannot handle the scenario that we need to jump back across window and frame. This is not a problem for version 1.0, as the version 1.0 only jump within the current window. But for version 2.0, we can jump across window and frame, but `(global-)pop-mark` only work on the current window, that means, even you jump back to previous position acrss window/frame, `(global-)pop-mark` only show that buffer in current window, never try to jump back to the original window/frame.

That's why `ace-jump-mode-pop-mark` comes out, and if you also to want the across window/frame jump back facility, please activate the `ace-jump-mode-pop-mark`.


### What does `ace-jump-mode-enable-mark-sync` do? When should I activate it?
Now, if you use `ace-jump-mode-pop-mark` function, we will jump back based on the information stored in `ace-jump-mode-mark-ring`. But sometimes, you may also want to use original `(global-)pop-mark`.

`ace-jump-mode-enable-mark-sync` is used to automatically sync between the `(global-)mark-ring` and `ace-jump-mode-mark-ring`, make it better use experience when you are going to mix the usage of orginal `(global-)pop-mark` and `ace-jump-mode-pop-mark`.

BTW,

`ace-jump-mode-enable-mark-sync` will add some advice on the `global-pop-mark` and `pop-mark`. If you found these advice potentially affect some of other extension and want to disable it, you can just remove `ace-jump-mode-enable-mark-sync` this call from your init file, or call `ace-jump-mode-disable-mark-sync` if you already enable it.

### I find compile error/warning, and open file error under windows, what's the problem?
Some one report this problem under windows platform, usually, this is not the problem of ace jump source code. The problem is git(msysgit) usuallly convert the carriage/line feed to windows format, which is CRLF.
But the ace jump mode use "utf-8-unix" as the "coding".

So, close this auto convertion, and checkout again.
> git config --global core.autocrlf false



### There is only one query char for word, why don't you add more?
I think someone may also be confused about when should I use `isearch` or when should I use `ace jump`. Does `ace jump` duplicate with `isearch`? Why don't you add more keys to replace the isearch?
I agree that it is a little confusing when you try the `ace jump` at the very beginning. I am also using the `ace jump` and `isearch` under different circumstance. Let me explain about the major difference between them: 

- The superiority of isearch is that it help you to find something which you usually do not know where it is, and then move cursor to the possible position. So the main **purpose of isearch** is to **search something you have not found it yet**, although I sometimes also use it to "locate" in current view before I write ace jump.

- The superiority of ace jump is that i can quickly move to a specific position, which you already see it, without having to combine too much M-f, Left, Right, Up, Down, etc. The **purpose of ace jump** is to **move your cursor to the exact position you already see it**.

So, when you want to search a content, use `isearch` for that. When you have already see it in the one of emacs window and want to move to it, try `ace jump`.