# Considerations

This document gives other considerations and things I
would like to change about the design or implementatios.

- I don't like using js to resize the board, but using pure CSS
in this case proved to be quite a difficult challenge. Chess.com appears
to use some fancy IEEE-754 truncation to solve the resize by
8 pixels at a time.

- I don't like that the ChessBoard and Sidebar are one component, but I don't
want a separate layout component that needs to contain them in order for them
to display properly.
