# Tile RPGs

Single-file, tile-based role-playing games in Python and Tk. Each game is one
executable script built on the engine from Penultimate: one adventurer on a map of
squares, people you talk to by keyword, shops, dungeons, synthesized sound
and music, and tiles drawn in code, so there are no image or sound files.

| Game | Setting | Rules |
| --- | --- | --- |
| [Miskatonic](#miskatonic) | Arkham, Massachusetts, 1925 | Call of Cthulhu, 5th edition |
| [Hyperspace Homeroom](#hyperspace-homeroom) | Marigold Bay, California, prom week | Teenagers From Outer Space |

## Running a game

The games need only Python 3 with Tk; there is nothing to install.

```bash
./miskatonic
```

```bash
./homeroom
```

If Python reports `No module named '_tkinter'`, install your Python's Tk
package (for example `brew install python-tk` on macOS with Homebrew Python,
or `sudo apt install python3-tk` on Debian and Ubuntu).

Every game has a few things in common:

- **Saving:** the game saves itself to `~/.<game>.json` whenever you change
  place and when you quit, and picks up from there the next time.
- **Controls:** keyboard, mouse or touch (tap a square to walk there), and a
  gamepad on Linux and the Steam Deck. Press `?` in a game for its keys.
- **Sound:** played with `afplay` on macOS, `paplay` or `aplay` on Linux,
  or pygame's mixer; with none of these the game is silent. Music is cached
  in `~/.cache/<game>`.
- **Self-test:** `./<game> --selftest` builds every map, room, level and
  tune of several generated games without opening a window.

---

## Miskatonic

*A tile-based investigation of the Cthulhu Mythos.*

Arkham, Massachusetts, Thursday the 22nd of October, 1925. Professor
Nathaniel Ashcroft of Miskatonic University has vanished, and with him the
four leaves of the Ashcroft manuscript: the Rite of Dismissal, an
incantation that can close a door no one should open. Dr. Henry Armitage,
the University's librarian, believes the Order of the Pale Lantern means to
open that door on the stones of the river island at midnight on Hallowe'en.
Find the leaves, bring them to Armitage, and be on the island before the
stars are right.

Each turn is a minute, which gives you about ten days.

### Every case is different

A new game deals a new case. The leaves lie in four of six places: a
mausoleum in the Old Arkham Graveyard, the cellars of the Witch House, the
Sanitarium basement, the University's steam tunnels, a Rivertown warehouse,
and a cave in the western woods. The people of Arkham change, and one of its
respectable citizens secretly leads the cult. The town itself, laid out after
the rulebook's map, stays where it is.

### Investigators

Choose one of eight occupations and roll characteristics the Call of Cthulhu
way: STR, CON, DEX, APP and POW on 3D6, SIZ and INT on 2D6+6, and EDU on
3D6+3. Occupation skill points (EDU×20) and personal interest points (INT×10)
are spent for you. Hit points are (CON+SIZ)/2, magic points equal POW, and
Sanity and Luck are POW×5.

Investigators are not fighting machines. Most of the work is done with
skills, each rolled on D100 with the result shown in the log:

- **Spot Hidden** finds what's hidden (`E` searches).
- **Listen** hears something coming before you see it.
- **Library Use** researches the words you've heard. Walk into a library's
  shelves.
- **Psychology** sees through liars.
- **Persuade, Fast Talk and Credit Rating** get you keys, permission and
  better prices.
- **Locksmith** opens locks, **Sneak** keeps you unnoticed, **Dodge** keeps
  you whole.

Skills you use successfully are checked. Each leaf you bring to Armitage
improves the checked skills, and he teaches you spells as the manuscript
comes together. Spells: Elder Sign, Shrivelling, Dominate, and the Rite of
Dismissal itself.

### Sanity

The first sight of each kind of horror costs Sanity, less if you make your
Sanity roll.

- **Temporary insanity:** lose 5 or more at once and make an Idea roll. If
  it succeeds, you have understood what you saw, and you may faint, panic,
  babble or hallucinate.
- **Lasting disorders:** lose a fifth of your Sanity within an hour and you
  gain one, until the Arkham Sanitarium treats it.
- **Cthulhu Mythos:** knowledge from tomes and horrors lowers your maximum
  Sanity to 99 minus your Cthulhu Mythos skill.

At zero Sanity or zero hit points your investigator is lost. A friend takes
up the case, along with the notes.

### Talking

Walk into a person, or into a counter with someone behind it, then choose or
type a word. Everyone knows NAME, JOB and BYE, and most people know NEWS.
Words in CAPITALS are worth asking about, and many are worth looking up in
the library. Shopkeepers answer BUY.

### Keys

| Key | Action |
| --- | --- |
| Arrows / WASD | Move (walk into people to talk, into enemies to fight) |
| Space | Wait a turn |
| E | Search |
| F / R | Fire / reload |
| C | Cast a spell |
| U | Use or ready an item |
| I | Investigator sheet |
| J | Journal |
| M | Map |
| ? | Help |

Gamepad: the d-pad or stick moves, A waits or chooses, B backs out, X fires,
Y casts, LB uses an item, RB opens the journal, View shows the map and Start
opens the menu.

The Rite of Dismissal must be spoken (`C`) in the stone circle beneath the
island, or at its threshold, and takes three uninterrupted turns.

### Beyond Arkham

Arkham is the first place. The roads out of town, toward Innsmouth,
Kingsport and Dunwich, and the bus and train ticket clerks are where more
places are meant to go.

### Files

- `miskatonic`: the game
- `~/.miskatonic.json`: the saved game
- `~/.cache/miskatonic/`: cached music

---

## Hyperspace Homeroom

*A lighthearted romp of aliens, prom week and giant rubber monsters.*

Marigold Bay, California, the Monday before the Spring Formal. Marigold Bay
High has been chosen to host the Galactic Spring Formal, and if the Galaxy's
party judges like it, Earth gets listed as a Fun Planet. If they don't, it
gets listed as a rest stop. Someone has smashed the Hyperdisco, the mirror
ball that makes a dance heard across four hundred light-years, into four
Disco Shards and hidden them around town. Find them, bring them to Dr.
Fizzwick in the science lab, find a date if you can, and get the Hyperdisco
spinning in the gym between 8 pm and midnight on Saturday.

Each turn is a minute. You start when school lets out on Monday afternoon.

### Every week is different

A new game deals a new week. The shards lie in four of six places: the
boiler room under the school, the mall's sub-basement, the storm drains, a
crashed saucer up behind Lover's Point, a broken arcade machine, and the
reel store under the drive-in. The people of Marigold Bay change, and one of
the town's grown-ups is secretly an agent of the planet Snorr, where fun has
been illegal since 1742. Unmask them early with the right evidence, or face
them when they crash the Formal as the fifty-foot Bore-Lord.

### Teeners

Be a Human, or an alien (Near Human, Not Very Near Human or Real Weirdie),
and pick one of eight cliques: Jock, Brain, Gearhead, Prep, Rebel, Surfer,
Band Geek or Exchange Student. Your clique sets your Knacks, your starting
gadgets and your Traits.

- **Stats:** Smarts, Bod, RWP (Relationship With Parents), Luck, Driving,
  Looks, Cool and Bonk are rolled on one die each. Move points between them
  in the creation dialog, never above 6 or below 1.
- **Rolls:** a die plus the Stat (plus a Knack that fits) against a die plus
  a difficulty from 1 to 10. Ties go to the other side, and every roll is
  shown in the log.
- **Powers:** aliens pick three of five tables and roll a power on each:
  Fly, Zap, Monster Out, Teleport, Shapechange, Get Small, Three's a Crowd,
  Magical Girl and more. Humans roll on the Humans Only table (Toughness,
  Lucky Break, Incredible Cute, Lose It Completely and others), and all of
  them can Fake Out an alien.
- **Gadgets:** the mall's Gadget Galaxy sells zap guns, goop guns, popcorn
  grenades, rocket sneakers, Boy/Girl guns (point one at yourself or at
  anyone else) and a Cosmic Battle Bikini.
- **Wheels:** humans have the family car and aliens a used saucer (unless
  they can teleport). Zeb's lot sells jetbikes and superdrives; the surf
  shop sells an antigravity boogie board.

Each shard you bring to Dr. Fizzwick earns Teener Points and a gadget from
her lab. Spend Teener Points on Knacks, or cash them in, from the menu.

### Bonk, and your folks

Nobody gets hurt. Every hit costs Bonk. At zero you stand around looking
stupid for a turn, plus a turn for every point below zero, and then your
Bonk comes back all at once. Get Bonked out three times in one place and you
wake up in the nurse's office, or at home if it's late.

The first sight of each kind of monster calls for a Cool roll. If you fail,
you might scream, faint, get the giggles or run around in circles.

Your RWP drops when you're out past curfew (11 pm on school nights), cut
class (8 to 3 on weekdays), wreck the town or get brought home. It comes
back after a day without trouble, from chores, from going to class and from
a nice phone call. Wake up with RWP below zero and you're grounded: beg,
do your chores, or climb out of the bedroom window.

### Talking and dating

Walk into a person, or into a counter with someone behind it, then choose or
type a word. Everyone knows NAME, JOB and BYE, and most people know NEWS.
Words in CAPITALS are worth asking about, and worth looking up at the
library or the video store. Shopkeepers answer BUY.

Ask a classmate to the FORMAL. You roll your Cool or Looks against their
Cool or Smarts. A corsage, formalwear, a favour you did them, or (for an
alien) a good Fake Out all help. Don't do too well, or they'll follow you
everywhere.

### Keys

| Key | Action |
| --- | --- |
| Arrows / WASD | Move (walk into people to talk, into monsters to clobber them) |
| Space | Wait a turn |
| E | Search |
| F | Fire what you hold |
| C | Use a power |
| U | Use a gadget or a snack |
| G | Get in or out of your wheels |
| I | Teener sheet |
| J | Journal |
| M | Map |
| ? | Help |

Gamepad: the d-pad or stick moves, A waits or chooses, B backs out, X fires,
Y uses a power, LB uses a gadget, RB opens the journal, View shows the map and
Start opens the menu.

### Files

- `homeroom`: the game
- `~/.homeroom.json`: the saved game
- `~/.cache/homeroom/`: cached music

---

## Licence

MIT; see [LICENSE](LICENSE).
