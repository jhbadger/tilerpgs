# Tile RPGs

Single-file, tile-based role-playing games in Python and Tk. Each game is one
executable script built on the engine from Penultimate: one adventurer on a map of
squares, people you talk to by keyword, shops, dungeons, synthesized sound
and music, and tiles drawn in code, so there are no image or sound files.

| Game | Setting | Rules |
| --- | --- | --- |
| [Miskatonic](#miskatonic) | Arkham, Massachusetts, 1925 | Call of Cthulhu, 5th edition |

## Running a game

The games need only Python 3 with Tk; there is nothing to install.

```bash
./miskatonic
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

## Licence

MIT; see [LICENSE](LICENSE).
