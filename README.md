**DEPRECATED** Actually this was the second *variant* of the second attempt.
Originally I named the macro `f` and quite liked it because the terminal of `f`
connects nicely with the quote: `f'something`.  Unfortunately I could not use
that name because I was told that as a deputy maintainer of Melpa, I should lead
by example and not use a name that conflicts with an existing package.  (Was
planning to ask the maintainer of `f` to donate the symbol `f`.)  `l'something`
is visually much less appealing so I went back to the drawing board and
ultimately decided, that my original approach was best after all.

Compact syntax for short lambda.

After [llama], this is my second attempt at providing such syntax
without having the power to add actual new syntax to Emacs, which
means that I have to fake it, which means that compromises cannot
be avoided.

The `l` macro allows you to write one of these three expressions:

    (l`list % %2 %*)
    (l'list % %2 %*)
    (l list % %2 %*)

all of which are turned into:

    (lambda (% %2 &rest %*)
      (list % %2 %*))

You may wish to substitute some fancy character for `l`:

    (defun my-prettify-l-symbol ()
      (cl-pushnew '("l" . ?ƒ) prettify-symbols-alist))
    (add-hook 'emacs-lisp-mode-hook 'my-prettify-l-symbol)
    (global-prettify-symbols-mode 1)

[llama]: https://git.sr.ht/~tarsius/llama
