Vim-sum: Sum numbers in select or operator-pending mode
=======================================================

This plugin is to sum some numbers in a visual selection. 
Recommanded to use with vim-textobj-word-column.

Examples
--------

Let's sum some numbers:

    |Item        Price       Description
    -------------------------------------------
    Chair       143         A magnificient chair
    Table       250         A decent table
    Lamp        9.8         A terrible lamp
    Beer        2.3         A not-so-free beer

Different ways to do it:

    - CTRL-V, then select an area with the numbers, then <Leader>a.
    - Press <Leader>a directly, putting you in operator-pending mode, then
        either G (till end of file), or 5j or } (end of paragraph),
    - V5j <Leader>a (visually select 5 lines downward, and some the numbers within)
    - [With textobj-word-column]: Move caret over a number, then
      viC (visual in whole column), then press <Leader>a

        Note1:
            Numbers used in the calculation are highlighted 
            so you can check everything went well.

        Note2:
            The sum (here: 405.5) will be echoed in 
            the status bar, and copied into the unnamed register. 
            You can paste it anywhere you like using 'p' or your
            other favorite way.

Installation and mappings
-------------------------

Use your favorite package manager, e.g. vim-pathogen.

Default mappings are **not** defined. You will need something like this
in your .vimrc file:

```
    nmap <Leader>a <Plug>VimSumOperatorPending
    vmap <Leader>a <Plug>VimSumVisual
```

I use `<A-a>` for vim-sequence and `<A-A>` for vim-sum. Choose whatever works
for you.

Valid numbers
-------------

Numbers should be separated by spaces or newlines.

Here are some examples that will be recognized:

>    52         Positive integer
>    92.25      Float
>    .525       Number without a leading zero
>    -.226      Negative number
>    92,25      Float using a comma, not a dot (as used by french and others)

Following are NOT supported at this time:

>    Scientific number, e.g. 42.352e23
>    Hexadecimal, octal, binary numbers (Might be nice though) 
>    Numbers not separated by a space, to minimize risks of error e.g.:
>    45min    will be discarded, because the number does not stand alone
>    100-35   will be discarded for similar reason. But 100 -35 will work
>    1. 2. 3. will all be discarded, so as not to confuse them with list 
>             items (1. is refused but .1 is accepted as a valid number)

Hide highlighted numbers
------------------------

To hide highlighted numbers, use `:match None`.


