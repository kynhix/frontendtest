# Welcome

These notes take you through my thought process on
design decisions, as well as give insight into my motivations and reasoning.
Throughout the different sections, I wrote down an important feature or attribute
I believe that component should have, and then I gave a reason, motivation, or 
implementation detail.
## Board

Resizes in increments of 8 pixels to prevent squares from being different
sizes. If the squares are different sizes, then the board will appear uneven
and cause potential bugs. This requires creating an event listener for resize.

Consumes all available space to make the design responsive. With media
queries to shift between desktop and mobile layout.

Should *never* be larger than the display in either width or height.
I do not want the user to have to scroll to see the whole board.

Yields space to sidebar. Sidebars should be a constant size,
unless on mobile layout.

## Sidebar

Displays the most recent action at the *top*. The most relevant
information should always be the most visible to the user.

Displays a **friendly** message to the user when empty.
This will hopefully encourage the user to interact with the board.

Should be one contiguous scroll on mobile. There should be no separate scroll bar inside
of the sidebar when in mobile view. This is a much better UX than having
to scroll down to the sidebar, and then having to scroll within the sidebar.

## Other

I tend to use flexbox for default display. Flexbox is just amazing.
