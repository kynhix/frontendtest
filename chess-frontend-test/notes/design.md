# Welcome

These notes take you through my thought process on
design decisions, as well as give insight into my motivations and reasoning.
Throughout the different sections, I wrote down an important feature or attribute
I believe that component should have, and then I gave a reason, motivation, or 
implementation detail. Some are design specifications that I feel are  
## Board

Must resize in increments of 8 pixels to prevent squares from being different
sizes. If the squares are different sizes, then the board will appear uneven
and cause potential bugs.

Needs to consume all available space to make the design responsive. With media
queries to shift between desktop and mobile layout.

The board should *never* be larger than the display in either width or height.
I do not want the user to have to scroll to see the whole board.

## Sidebar

Shows the most recent action at the *top*. The most relevant
information should always be the most visible to the user.

Displays a **friendly** message to the user when empty.
This will hopefully encourage the user to interact with the board.
