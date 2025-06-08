# Uno

This is an experimental new version of the Uno bot. DO NOT pester Ratismal with bugs in this, unless you have verified that they also occur in his original version.

## Table of Contents

1. [Description](#description)
2. [Configurable Rules](#configurable-rules)
3. [Tupperbox Integration](#tupperbox-integration)
4. [Selfhosting](#selfhosting)
5. [Disclaimer](#disclaimer)

## Description

This is an Uno bot designed for the Discord chat platform. The intent of this bot is to provide a fun and fulfilling Uno experience with your friends!

I was feeling the original Uno bot, while quite fun, was lacking some important customization features, in particular playing with Uno decks other than the classic one. For this reason, I created this fork.

### Commands

```
UNO HELP - Shows this message!
UNO SUPPORT - Gets a link to my support guild! Will be temporarily disabled when new features are added, until the experimental version has its own support guild.
UNO JOIN - Joins (or creates) a game in the current channel!
UNO QUIT - Quits the game! Party pooper.
UNO START - Starts the game! Can only be used by the player who joined first.
UNO TABLE - Shows everyone at the table.
UNO PLAY <color> <value> [pile] - Plays a card! Colors and values are interchangeable. Pile defaults to 1 (values higher than the amount of piles are treated as 1).
UNO PICKUP - Picks up a card!
UNO CALLOUT - Calls a player out for only having one card left!
UNO HAND - Checks your hand!
UNO RULES - Checks or sets the game rules!
UNO! - Let everyone know that you only have one card left!

You can execute up to two commands in a single message by separating them with &&!
```

The player will get their cards in a PM by the bot itself but to the command needs to be executed in the room where the players are playing (not privately).

## Configurable Rules

One of the features of Uno is configurable rules, to make sure your games are as customizable as possible! You can view these using the `uno rules` command.

To set, the creator of the game has to run the command: `uno rules <key> <value>`.

Current and upcoming rules:

### Decks

Key: `DECKS`
Type: integer (soon string)
Default: 1 (soon `classic`)

This is the number of decks to use in the game.

It's planned to change this into a comma-separated list of decks (allowing for values such as `party,all_wild,teams,spin,addon_swap,addon_reverse`). The same deck can be included more than once, so the current functionality can be achieved with a value of e.g. `classic,classic,classic`.

Note that it will **NOT** be verified that the decks provided form a playable set of cards. If all cards in the deck except up to 1 are in players' hands (so that the Draw Pile is empty and the Discard Pile can't be shuffled to form a new Draw Pile), the game will instantly end in a tie.

Supported values for deck names will be (in the first full release of this feature):
- `classic`: Uno Classic (112 cards)
- `addon_swap`: Uno Core Add-On Packs -- Swap Pack (16 cards)
- `addon_speed`: Uno Core Add-On Packs -- Speed Pack (16 cards)
- `addon_reverse`: Uno Core Add-On Packs -- Reverse Pack (16 cards)
- `addon_stack`: Uno Core Add-On Packs -- Stack Pack (16 cards)
- `themed_mario`: Uno Super Mario (112 cards)
- `themed_mario_kart`: Uno Mario Kart (112 cards)
- `party`: Uno Party (224 cards)
- `attack`: Uno Attack
- `all_wilds`: Uno All Wilds (112 cards)
- `flip`: Uno Flip (112 cards)
- `themed_flip_transformers`: Uno Flip Transformers (112 cards)
- `flex`: Uno Flex (104 cards)
- `no_mercy`: Uno Show 'Em No Mercy (168 cards)
- `addon_no_mercy`: Uno Show 'Em No Mercy - Expansion Pack
- `teams`: Uno Teams (112 cards)
- `dos`: Dos (108 cards)
- `dos2`: Dos Second Edition (108 cards)
- `infinity`: Uno Infinity

### Spin Roulette (upcoming)

Key: not yet implemented, will be `SPIN_ROULETTE`
Type: string
Default: `"standard"`

This is the Spin roulette used when playing a deck that features Spin cards. TBD which values besides `"standard"` will be supported.

### Amount of Discard Piles (upcoming)

Key: not yet implemented, will be `DISCARD_PILES`
Type: integer
Default: 1

This is the amount of discard piles used by the game.

### Summing Cards (upcoming)

Key: not yet implemented, will be `SUM`
Type: boolean
Default: false

This is whether cards can be played across multiple discard piles such that their sum matches one of the discard piles. `DISCARD_PILES` must be 2 or higher for a value of `true` to have any meaningful effect.

### Amount of Flex Power Cards (upcoming)

Key: not yet implemented, will be `POWER_CARDS`
Type: integer
Default: 0

This is the amount of Flex Power Cards each player has.

### Players Per Team (upcoming)

Key: not yet implemented, will be `TEAM_PLAYERS`
Type: integer
Default: 1

This is the amount of players in each team.

### Initial Cards

Key: `INITIAL_CARDS`
Type: integer
Default: 7

This is how many cards to pick up at the beginning of the game.

### Draws Skip

Key: `DRAW_SKIP`
Type: boolean
Default: true

This is whether pickup cards (+2, +4) should also skip the next person's turn.

### Must Play

Key: `MUST_PLAY`
Type: boolean
Default: false

This is whether a player has to play a card if they're able to, instead of drawing.

### Callouts

Key: `CALLOUTS`
Type: boolean
Default: true

This is whether other players are able to call someone out for having only one card but not saying uno!

### Callout Penalty

Key: `CALLOUT_PENALTY`
Type: integer
Default: 2

This is how many cards a player has to pick up with someone successfully calls them out.

### False Callout Penalty

Key: `FALSE_CALLOUT_PENALTY`
Type: integer
Default: 2

This is how many cards a player has to pick up if they try to call someone out, but everyone has more then one card.

### Automatically Play After Draw

Key: `DRAW_AUTOPLAY`
Type: boolean
Default: false

Automatically plays a card after drawing, if possible. If a wild card is drawn, will give a prompt for color.

## Tupperbox Integration

The current state of compatibility with [Tupperbox](https://tupperbox.app/) has not yet been tested. Long-term goals are:
- Any amount of Tuppers, including multiple with the same owner, can take part in an Uno game.
- Tuppers can run Uno commands as if they were regular users.
- A Tupper's owner can join a game alongside their Tuppers.
- Basically, Tuppers are treated the same as regular users, and are treated as separate from their owner.

## Selfhosting

You may selfhost (AKA run your own instance of) this bot under the following circumstances:
- Your instance (referred to as a "clone") must be **private**.
    - As such, your clone must not be listed on any sort of public bot listing.
- Self-hosting support will be provided, within limits of knowledge, for this fork only.
- You acknowledge that issues and feature requests specifically related to self-hosting will be lower priority than the fork owner's feature ideas. If you want things done on that front, your best bet is to start the pull request yourself.
- You acknowledge that a fork's issues belong in that fork, not here.

### Configuration

config.json (`config.example.json`), the oauth part is not mandatory (it is used for the web interface) but if you don't needed you need to leave the settings with default values.

config/config.json (`config/config.example.json`), support various database with this example will use SQLite.

### Dependencies

After running `npm install` it is required to migrate the new database (after put the configuration files) and run `npm run sequelize db:migrate`.
Now, you can run the bot with `node index.js`.

## Disclaimer

This bot is not associated with Uno or Mattel, nor the maker of Uno Infinity in any ways.
