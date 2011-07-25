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

    (defvar ace-jump-mode-move-keys
       (nconc (loop for i from ?a to ?z collect i)
              (loop for i from ?A to ?Z collect i))


### I don't want to input the head char for word mode, is it possible to mark all the word in current page?
        (setq ace-jump-word-mode-use-query-char nil)