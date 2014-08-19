##Tooling

For this project I've decided to use Stylus as a CSS preprocessor and Grunt to make the development faster (not to rebuilt it by hand each time I make changes)

Grunt `watch:styles` task, as you might have already guessed, watches for any ***.styl** file changes and makes ***.styl -> *.css** conversion

Since it's just a test project the repository already contains the latest processed CSS file uncompressed and with all comments preserved

Icomoon web-based app was used to create a custom webfont with glyphs limited to those used as pieces

##Assumptions

The layout make heavy use of the flexbox layout model which behavior depends on `writing-mode` and `direction` properties

So, here we assume that `writing-mode` is set to `horizontal-tb` and direction has value of `ltr` which is common for most latin based languages like English, Spanish, French or Ukrainian

##Styleguide

Each game has it's own container `.game`

To distinguish between games the following class naming convention is used `.game.{name}`.
Where `{name}` is one of the following:
- chess
- checkers
- othello

Inside the container you'll find:
 - game statistics `.stats` section and
 - game board `.board-container` section


The board (`.board`) consists of rows (`.row`) which in turn has cells (`.cell`)
In order to place a piece on the board just add the `.piece` element with the `.piece-{name}` class into the cell.

By default every `.piece` element on the board has the color of the active player.

To change the color to the opponent's either mark the piece itself or the cell `.cell` with the `.opponent` class.

To tell one piece from another the following class naming convention is used `.piece.piece-{name}`.
Where `{name}` is one of the following:
- king
- queen
- rook
- bishop
- knight
- pawn
- checker


Developers might also be interested in the statistics section (`.stat`)

The statistic section has score container (`.score`) one for every player which in turn can have three (3) states (layouts):

- numeric score with the piece bucket (`.piece-bucket`) - the default
- the piece bucket alone OR
- just plain numeric score without a bucket

The latter one differ somewhat from the former two in layout and must be triggered by adding the `.no-bucket` class to the `.stat` container

As has already been said each player has it's own score (`.score`) box with or without a bucket (`.piece-bucket`).
In order to change the numeric value or add a piece into the bucket one should query for a `.score` container for the score of the active player or `.score.opponent` for the opponent's score accordingly.

Withing the score container pieces that go into active player's bucket will automatically have opponent's color and vice versa.

In case of a `.no-bucket` layout the font color of the score (`.score`) container will have the player's color and the background will get the opponent's font color and the other way round.

You might have noticed that on the Desktop the board flips some when you hovering the mouse over it. There is no such a way as rollover state on the mobile world, however.
To make it work on Mobile you may listen to the `onclick` or `ontouchstart` or `pointerdown` evens and toggle the `.active` class of the `.game` container.
If you want to stop board flipping to occur you can add `.over` class to the `.game` container.

In order to communicate current game state to the user you may utilize prompts (`.prompt`)

Once the game outcome is known please add the `.won` or `.lost` class to the game container. It will hide the `.prompt` and show the result to the user right over the board.



