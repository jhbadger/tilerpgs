# Tile RPGs

Single-file, tile-based role-playing games in Python and Tk. Each game is one
executable script built on the engine from Penultimate: one adventurer on a map of
squares, people you talk to by keyword, shops, dungeons, synthesized sound
and music, and tiles drawn in code, so there are no image or sound files.

| Game | Setting | Rules |
| --- | --- | --- |
| [Miskatonic](#miskatonic) | Arkham, Massachusetts, 1925 | Call of Cthulhu, 5th edition |
| [Hyperspace Homeroom](#hyperspace-homeroom) | Marigold Bay, California, prom week | Teenagers From Outer Space |
| [Clover Vale](#clover-vale) | a valley of magic ponies, the week of the Lantern Festival | the pony roleplaying game (Renegade Game Studios) |
| [Lazarus Deep](#lazarus-deep) | a dead ice-mining station on a frozen moon, four days before the Company arrives | Mothership (Tuesday Knight Games) |

## Running a game

The games need only Python 3 with Tk; there is nothing to install.

```bash
./miskatonic
```

```bash
./homeroom
```

```bash
./clovervale
```

```bash
./lazarus
```

If Python reports `No module named '_tkinter'`, install your Python's Tk
package (for example `brew install python-tk` on macOS with Homebrew Python,
or `sudo apt install python3-tk` on Debian and Ubuntu).

To build a macOS app with an icon, run the game with `--build-app`. It
writes `<game>.app` next to the script, or in a folder you name:

```bash
./clovervale --build-app ~/Applications
```

The app holds a copy of the game, and it starts with the Python that built
it, so rebuild it after you change the game or that Python.
`./<game> --icon-png SIZE [OUT.png]` writes just the icon.

Every game has a few things in common:

- **Saving:** the game saves itself to `~/.<game>.json` whenever you change
  place and when you quit, and picks up from there the next time.
- **Controls:** keyboard, mouse or touch (tap a square to walk there), and a
  gamepad on Linux and the Steam Deck. Press `?` in a game for its keys.
- **Sound:** played with `afplay` on macOS, `paplay` or `aplay` on Linux,
  or pygame's mixer; with none of these the game is silent. Music is cached
  in `~/.cache/<game>`.
- **Icon:** drawn in code like the tiles. Miskatonic has a tentacle rising
  from the sea, Hyperspace Homeroom a flying saucer, Clover Vale a
  four-leaf clover with a horseshoe, and Lazarus Deep the Dig tower on
  the ice under a gas giant. It is the window icon on every system,
  and the app icon on macOS.
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
  anyone else, then ask them about the CHANGE) and a Cosmic Battle Bikini.
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

## Clover Vale

*A gentle adventure of magic ponies, friendship and the Lantern Festival.*

Clover Vale, the week of the Lantern Festival. Every midsummer the ponies of
the valley light the Great Lantern in the Lantern Hall, and its light keeps
the Greymist, a fog that drains the colour and the cheer out of everything,
back in the hills for another year. This year somepony has taken the
Lantern's four Heartstones and hidden them around the valley. Find them,
bring them to Grandmare Thistlewick at the Star Tower, and light the Great
Lantern on Lantern Night, Saturday between sunset (8 pm) and midnight.

Each turn is a minute. You start at home on Monday morning.

### Every week is different

A new game deals a new week. The Heartstones lie in four of six places: the
old gem mine under Pebble Hill, the heart of the Hollow Wood, the Cloud
Castle above the north-east hills, the grotto under Lily Lake, the Clockwork
Attic over the toy shop, and the cellars of Thornwall Keep. The ponies of
Clover Vale change, and one of the town's grown-ups is a Gloom in disguise.
Find proof and ask them about the GREYMIST, or meet them on Lantern Night as
the Greymist Wyrm.

### Ponies

Be a meadow pony, a pegasus or a unicorn, and choose a Calling (the talent
your heartmark shows) and a Heart (the virtue you live by).

- **Origins:** meadow ponies are tough and can buck things (a monster, a
  stuck gate, an apple tree). Pegasi fly over water, hedges and holes, and
  walk on clouds. Unicorns cast spells and fetch things with telekinesis.
- **Callings:** Baker, Bookworm, Adventurer, Animal Friend, Performer,
  Tinkerer, Athlete, Fashion Pony, Farmer or Party Planner. The Calling sets
  your heartmark Skill (always an upshift, and specialized), what you've
  practised and what you start with.
- **Hearts:** Generosity, Honesty, Kindness, Laughter, Loyalty or Wonder.
  Each adds to two Essences, gives a gift of its own, and earns Friendship
  Points when you live by it.
- **Essences and Skills:** twelve points go between Strength, Speed, Smarts
  and Social (move them in the creation dialog), and your Origin and Heart
  add four more. Each Essence's points become ranks in its Skills, from d2 to
  d12, and each Essence plus ten is a Defense.
- **Rolls:** a d20 plus the Skill's die against a Difficulty (10 routine, 15
  challenging, 20 difficult). Upshifts and downshifts move the die up and
  down the ladder. With no rank in a Skill you roll two d20s and keep the
  worse. Rolling the die's highest number on a success is a Critical
  Success; a natural 1 on a failure is a fumble, which earns a Friendship
  Point. Every roll is shown in the log.
- **Magic:** each spell costs downshifts to your Spellcasting, which come
  back a rank a turn. Push past zero and it costs Health instead. Grandmare
  Thistlewick teaches a spell for each Heartstone you bring home, to any
  pony, horn or no horn.

Each Heartstone brought home is also a level: raise a Skill (and its
Essence) from the menu.

### Health, friendship and befriending

A hit costs Health. At zero you're Defeated for a few turns, and then you
pick yourself up. Get Defeated three times in one place and somepony carries
you to the Healer's Cottage, or home if it's late. Food, salve, sleep and
Nurse put Health back.

Most monsters would rather be friends. Befriend one (`T`) with the Skill
that reaches it: Animal Handling for beasts, Persuasion for anything that
talks, Technology for clockwork, Performance to make a spook laugh. Each
Heartstone's guardian takes a few tries, and hands the stone over when you
win it round. Looking the guardian up at the library first helps.

Friendship Points buy a pep talk (full Health), a hint where a Heartstone
is, or a run of luck (Edge on every roll), from the menu. Each morning brings
you back up to three.

### Talking and friends

Walk into a pony, or into a counter with someone behind it, then choose or
type a word. Everypony knows NAME, JOB and BYE, and most know NEWS. Words in
CAPITALS are worth asking about, and worth looking up at the Inkwell Library
or the Star Tower. Shopkeepers answer BUY.

Help a pony with an errand, or GIVE them a gift, and they become your
friend. Ask a friend to COME along and they'll follow you, lend a hoof on
every roll, and join in the scuffles. Say STAY to send them home.

You can't go to Lantern Night without a festival ribbon. Well, you can, but
somepony will tut.

### Keys

| Key | Action |
| --- | --- |
| Arrows / WASD | Move (walk into ponies to talk, into monsters to scuffle) |
| Space | Wait a turn |
| E | Search |
| F | Throw a pie or a buckball |
| T | Befriend a creature |
| C | A talent or a spell (fly, buck, telekinesis, magic) |
| U | Use something |
| I | Your pony |
| J | Journal |
| M | Map |
| ? | Help |

Gamepad: the d-pad or stick moves, A waits or chooses, B backs out, X
throws, Y uses a talent or spell, LB uses something, RB opens the journal,
View shows the map and Start opens the menu.

### Files

- `clovervale`: the game
- `~/.clovervale.json`: the saved game
- `~/.cache/clovervale/`: cached music

---

## Lazarus Deep

*Survival horror on a dead mining station under the ice.*

Lazarus Deep is a Halvorsen-Kade ice mine on Tisiphone, a frozen moon of the
gas giant Megaera. Nineteen days ago it stopped shipping ice and stopped
answering. You are the first of the four contract crew of the tug Patience
to come out of cryo, and the station's mind, VESPER, has just clamped your
ship to the docking ring and won't let it go. Something four kilometres down,
at the bottom of the Dig, is singing. The Company's ship, the Due Diligence,
docks on the evening of the fourth day. It isn't coming to help.

There is no list of things to collect. What happened here, who is still what
they seem, who can be saved and how to make it stop are for you to find out,
and you probably won't manage all of it:

- **Survive:** free the Patience and leave. The Director's override code,
  VESPER's core in the Underdeck, or a pilot mad enough to fire the drive
  with the clamps still on.
- **Solve:** find the evidence (the Director's Directive 9, the foreman's
  Survey Log, the doctor's autopsy notes, the Magdalene's manifest) and
  broadcast it to the public relay, where the Company can't bury it.
- **Save:** the survivors will go aboard the Patience and wait in the hold,
  if they trust you. Errands win their trust: dog tags, a wedding ring, a
  child's cat, a box of insulin, a failing CO2 scrubber, a pilot hiding in
  the flooded cistern.
- **Stop it:** put back what was taken from the Reliquary, and bring the
  Dig down on top of it.

One of the survivors is not a survivor. Every night at two, the Second Skin
goes walking and somebody doesn't come back. The people who've noticed
things will tell you, and a medscanner, a bioscanner, infrared goggles or
VESPER's head count will too. Take it aboard the Patience and it goes where
you go. Only fire keeps it down.

Each turn is a minute. You wake aboard the Patience at 08:00 on Day 1.

### Every station is different

A new game deals a new station: the survivors' names change, a different one
of them is the Second Skin, the people who've noticed something change, and
the things you need (the Blasting Store key, a scrubber filter, a
flamethrower, a medscanner) lie on different bodies in different places
below. The Ring stays where it is. Below it are the Dig, the Underdeck, the
sealed dorms of Sector 7, the airless ore hauler Magdalene and the flooded
Reclamation tanks.

### Crew

Roll your Stats (Strength, Speed, Intellect, Combat: 2d10+25 each) and Saves
(Sanity, Fear, Body: 2d10+10 each), and roll again until you like them. Then
choose a class and a speciality:

- **Marine:** +10 Combat, +10 Body, +20 Fear and a Wound to spare. When you
  Panic, whoever is with you may run. Rifleman, Breacher or Old hand.
- **Android:** +20 Intellect, -10 Speed, +60 Fear and a Wound to spare.
  People find you hard to trust, but you don't breathe, and the Psalm has
  nothing in you to hollow out. Systems, Medical or Security.
- **Scientist:** +10 Intellect, +5 more Intellect and +30 Sanity, and a
  Master Skill. When you fail a Sanity Save, whoever is with you loses their
  nerve. Physician, Xenobiologist, Cyberneticist or Archaeologist.
- **Teamster:** +5 to every Stat and +10 to every Save. Once a day you take
  Advantage on a Panic Check. Mechanic, Miner or Pilot.

Your class and roll give you a loadout (armour, a weapon, some kit), a few
credits, a trinket and a patch.

### Rolls, Stress and Panic

- **Checks and Saves:** roll d100 under a Stat or Save, plus your best
  relevant Skill (+10 Trained, +15 Expert, +20 Master). 90-99 always fails.
  Doubles are critical, either way. Advantage rolls twice and takes the
  better, Disadvantage the worse. Every roll is shown in the log.
- **Stress:** every failed roll is a point. A critical failure, the first
  sight of a horror or a death means a Panic Check: a d20 that must beat
  your Stress, or you roll on the Panic table (adrenaline, nightmares,
  cowardice, a heart attack, or giving up altogether). Stress past 20 eats
  into your worst Save.
- **Rest:** a bunk sheds Stress with a Rest Save, and six hours' sleep can
  put your Health back. The Patience and the chapel are safe. Nowhere else
  is.

### Wounds and dying

Damage comes off Health, but armour ignores any hit smaller than its Armor
Points, and is wrecked by any hit that isn't. At zero Health you take a
Wound and roll on the Wounds table for its kind (blunt force, bleeding,
gunshot, fire, gore). That might mean a broken leg, Bleeding every turn
until you stop it, or a lethal injury with a few turns left to treat it.
Run out of Wounds and you make a Death Save.

When you die, the next of the Patience's crew comes out of cryo and carries
on, from where things stand. Your body stays where it fell, with your kit.
When all four are gone, it's over.

Vacuum, cold, radiation, steam and bad air all hurt too. Fit a scrubber
filter before Day 3, and wear a sealed suit with air in it on the Magdalene.

### Talking and trust

Walk into someone, or into a counter with someone behind it, then choose or
type a word. Everyone knows NAME, JOB and BYE, and most know NEWS. Words in
CAPITALS are worth asking about. The quartermaster, the bartender, the
doctor, the cook and (once she trusts you) the deputy answer BUY.

Do someone a favour and they'll trust you. Ask the people who trust you to
go aboard the PATIENCE and they'll wait in its hold, or ask them to COME
with you (STAY sends them back). Ask about HOLLOW when you're sure enough.

### Keys

| Key | Action |
| --- | --- |
| Arrows / WASD | Move (walk into people to talk, into things to fight them) |
| Space | Wait a turn |
| E | Search |
| F | Fire your weapon, or throw a grenade |
| R | Reload |
| U | Use something (medicine, scanners, suits, weapons, charges) |
| I | Your crew member |
| J | Journal |
| M | Map |
| ? | Help |

Gamepad: the d-pad or stick moves, A waits or chooses, B backs out, X fires,
Y reloads, LB uses something, RB opens the journal, View shows the map and
Start opens the menu.

### Files

- `lazarus`: the game
- `~/.lazarus.json`: the saved game
- `~/.cache/lazarus/`: cached music

---

## Licence

MIT; see [LICENSE](LICENSE).
