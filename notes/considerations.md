# Considerations

This document gives other considerations and things I
would like to change about the design or implementation.

- I don't like using js to resize the board, but using pure CSS
in this case proved to be quite a difficult challenge. Chess.com appears
to use some fancy IEEE-754 truncation to solve the resize by
8 pixels at a time. I do not understand fully how it works, so I'm not
using it.

- I don't like that the ChessBoard and Sidebar are one component, but I don't
want a separate layout component that needs to contain them in order for them
to display properly.

- I used a bit of padding on the entire app. I like to give everything a little
of breathing room.

- I added a small animation to the sidebar to emphasize where the new data is
being added.

- I much preferred the look of the chess board and sidebar being centered together
instead of aligned to the left.
