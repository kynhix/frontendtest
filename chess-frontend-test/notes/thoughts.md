# About

This document gives other considerations and things I
would like to change about the design or implementation.

- I don't like using js to resize the board, but using pure CSS
in this case proved to be quite a difficult challenge. Chess.com appears to use some fancy
IEE-754 truncation to solve the resize by 8px at a time issue of the board.
