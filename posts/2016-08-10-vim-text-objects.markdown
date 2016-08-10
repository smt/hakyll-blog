---
date: 2016-08-10 18:17:37
title: Words and Text Objects in Vim
tags: Vim, Mad Coding
---

What are text objects in Vim? Before I can answer that question, we first need to discuss **words**.

## There are words, and then there are WORDS

Not even joking, there really are two distinct types of these things. To quote Vim's help page on the subject (see `:h word`):

> A word consists of a sequence of letters, digits and underscores, or a sequence of other non-blank characters, separated with white space (spaces, tabs, EOL). This can be changed with the 'iskeyword' option. An empty line is also considered to be a&nbsp;word.
>
> A WORD consists of a sequence of non-blank characters, separated with white
space. An empty line is also considered to be a&nbsp;WORD.

Under those definitions, given the following example text to operate on:

> what-is-up; "i can't even"

Assuming a default `iskeyword` setting, the following are words:

`what`, `-`, `is`, `-`, `up`, `;`, `"`, `i`, `can`, `'`, `t`, `even`, and `"`

By contrast, in the same passage, these are considered WORDS:

`what-is-up;`, `"i`, `can't`, and `even"`

WORDS are bounded strictly go by surrounding whitespace, whereas the delineation of words is configurable. In my Vim configuration, I actually set my personal `iskeyword` option to include `$`, `%`, `&`, `#`, `-`, `'`, and `+` as "word" characters.

(As an aside, I'm on the fence about setting `'` as a "word" character. For prose, it makes sense; for programming, not so much.)

### Examples of motions over words/WORDS

We can perform **motions** over words in several useful ways. (Hint/foreshadowing: words are like text objects in this respect.)

In each example below, the caret `^` character indicates the cursor position to illustrate where it ends up after each motion.

1. We move the cursor to the **beginning** of the next word using the `w` key. Likewise, we use `W` to move to the beginning of the next&nbsp;WORD.

    - **w**: forward to start of next _word_
    - **W**: forward to start of next _WORD_

    <br>

    ```text
    Making friends is easy. Waiting-for-Superman... waiting...
             ^
    
    Making friends is easy. Waiting-for-Superman... waiting...
    w(ord)         ^
    
    Making friends is easy. Waiting-for-Superman... waiting...
    w(ord)            ^
    
    Making friends is easy. Waiting-for-Superman... waiting...
    W(ORD)                  ^
    
    Making friends is easy. Waiting-for-Superman... waiting...
    w(ord)                         ^
    
    Making friends is easy. Waiting-for-Superman... waiting...
    W(ORD)                                          ^
    
    Making friends is easy. Waiting-for-Superman... waiting...
    w(ord)                                                 ^
    ```

    <br>

2. To move the cursor to the **end** of the next word or WORD, we use the `e` or `E` key.

    - **e**: _end_ of word
    - **E**: _END_ of WORD

    <br>

    ```text
    Making friends is easy. Waiting-for-Superman... waiting...
             ^
    
    Making friends is easy. Waiting-for-Superman... waiting...
    e(nd)        ^
    
    Making friends is easy. Waiting-for-Superman... waiting...
    e(nd)           ^
    
    Making friends is easy. Waiting-for-Superman... waiting...
    E(ND)                 ^
    
    Making friends is easy. Waiting-for-Superman... waiting...
    e(nd)                         ^
    
    Making friends is easy. Waiting-for-Superman... waiting...
    E(ND)                                         ^
    
    Making friends is easy. Waiting-for-Superman... waiting...
    e(nd)                                                 ^
    ```

    <br>

3. Finally, we use `b` and `B` to move to the start of a word or WORD.

    - **b**: _back_ to start of word
    - **B**: _BACK_ to start of WORD

    <br>

    ```text
    Making friends is easy. Waiting-for-Superman... waiting...
                                                          ^
    
    Making friends is easy. Waiting-for-Superman... waiting...
    b(ack)                                          ^
    
    Making friends is easy. Waiting-for-Superman... waiting...
    b(ack)                                      ^
    
    Making friends is easy. Waiting-for-Superman... waiting...
    B(ACK)                  ^
    
    Making friends is easy. Waiting-for-Superman... waiting...
    B(ACK)            ^
    
    Making friends is easy. Waiting-for-Superman... waiting...
    b(ack)         ^
    ```

    <br>

## Operators

Now that we've got some basic word motions down, let's review some basic Vim operators that we'll use in examples of editing text objects later on.
