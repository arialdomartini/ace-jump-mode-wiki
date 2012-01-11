### I want to do something before real jump happens, is it possible?
Of course, actually there is a hook for you to do this, anything you want to do before the jump. I give am example here:

    (add-hook 'ace-jump-mode-before-jump-hook (lambda ()
                                                (message "I am jumping")))

### I don't like the default move keys, is it possible to change it.
I have to remind one thing before you change the default move keys. You have to know that the less move key you use, the more time you possibly need to press the key to finally reach the exactly location. If it is possible, please use the keys not less than 10 , that can make AceJump really effective.
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
The default setting to ace-jump-mode-case-fold is set the same value as 'case-fold-search'.


### I enter the word mode, but I want to change to char mode, is there is quick way?
Yes, now you can use C-c C-c to quickly change between word-mode and char-mode when you already enter one of these two mode. Of course, the query char you input will use as the default input char between each mode.

### I don't want to input the head char for word mode, is it possible to mark all the word in current page?
        (setq ace-jump-word-mode-use-query-char nil)

### I want to use my own sub-mode sequence that triggered by different "C-u" + "C-c SPC", is it possible?
Currently, there is only three sub mode, which is char mode, word mode, and line mode, they map to the function called `ace-jump-char-mode`, `ace-jump-word-mode`, and `ace-jump-line-mode`.

You can specify the sequence by setting `ace-jump-mode-submode-list`.

For example, the default value is :

    (setq ace-jump-mode-submode-list
          '(ace-jump-word-mode              ;; the first one always map to : C-c SPC
            ace-jump-char-mode              ;; the second one always map to: C-u C-c SPC            
            ace-jump-line-mode) )           ;; the third one always map to ：C-u C-u C-c SPC

You can change the sub mode sequence as you wish.

### There is only one query char for word, why don't you add more?
I think someone may also be confused about when should I use isearch or when should I use AceJump. Does AceJump duplicate with isearch? Why don't you add more keys to replace the isearch?
I totally agree that it is really confused for us to decide which is quicker and better between the isearch and AceJump. I also use the AceJump and isearch under different circumstance. But I think the major difference between two is that: 

- The superiority of isearch is it can dynamically update the view and move cursor based on your searching string, which you normally do not know where it is before you start the search. So the main **purpose of isearch** is **search something you have not found it yet**, although I sometimes also use it to "locate" in current view before I write AceJump.

- The superiority of ace jump is that i can quickly move to a specific position, which you already see it, without having to combine too much M-f, Left, Right, Up, Down, etc. The **purpose of AceJump** is to **locate to the position you already find it**.

So, finally, the thing is easy. When you want to search a content, use isearch for that. When you have already see it in the current view and want to move to it, use AceJump.
