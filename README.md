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
| [Larkspur Hall](#larkspur-hall) | an English country house, the week of the Master's birthday | Maid RPG (Ryo Kamiya) |
| [Nine Lives](#nine-lives) | a Nevada company town, the week before Omnicorp's Firmware 9 | a light mix of Homeroom's, Larkspur's and Clover Vale's rules |
| [Some Assembly Required](#some-assembly-required) | a sunny suburb in 2041, the week you buy a Daffodil | The Black Hack (David Black) |

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

```bash
./larkspur
```

```bash
./ninelives
```

```bash
./daffodil
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
- **Screen size:** the whole window scales to fit, on a desktop or a phone
  (Pydroid 3 on Android): text, side panel, buttons and map tiles. Held
  upright, a phone puts the side panel under the map and the buttons in
  rows. The menu's Zoom in and Zoom out change the map tiles, and Bigger
  text and Smaller text everything else.
- **Sound:** played with `afplay` on macOS, `paplay` or `aplay` on Linux,
  or pygame's mixer; with none of these the game is silent. Music is cached
  in `~/.cache/<game>`.
- **Icon:** drawn in code like the tiles. Miskatonic has a tentacle rising
  from the sea, Hyperspace Homeroom a flying saucer, Clover Vale a
  four-leaf clover with a horseshoe, Lazarus Deep the Dig tower on the
  ice under a gas giant, Larkspur Hall a teacup with its steam rising
  in a heart, Nine Lives a catgirl's silhouette against a desert
  sunset, and Some Assembly Required a daffodil and a power button. It
  is the window icon on every system, and the app icon on macOS.
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
| P | Your phone: the to-do list |
| J | Journal: the clues and the evidence |
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
| P | Your phone: the to-do list |
| J | Journal: the clues and the evidence |
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
| P | Your phone: the to-do list |
| J | Journal: the clues and the evidence |
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
| P | Your phone: the to-do list |
| J | Journal: the clues and the evidence |
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

## Larkspur Hall

A comedy of a week below stairs in a rambling English country house, on
the rules of Maid RPG (Ryo Kamiya; English edition by Kuroneko Designs).

You are the newest maid at Larkspur Hall. The Master's birthday is on
Sunday, and the Master doesn't want a fuss. The Master's great-aunt, the
Dowager, who holds the family purse, is coming that afternoon to decide
whether Larkspur carries on as it is or is sold, and its household turned
out. And on the morning you arrive, a calling card comes with the post:
*Larkspur. Tonight: the KITCHEN. Yours, the Phantom.*

The week has three threads, and the ending depends on all of them:

- **The Favor race:** every maid in the house wants the Master's Favor, and
  the other three maids are working the same rota you are. Wake the Master,
  cook and serve the meals, do the laundry and the cleaning, take the
  Master for a walk, draw the bath, read a bedtime story. Whoever gets
  there first gets the credit. At the party, the maid with the most Favor
  gets the ending scene.
- **The birthday:** bake the cake (flour, sugar, butter, eggs, cream, and
  the Master's favourite flavour; practise first; the other maids help if
  they like you), and make the Master a present. Find out what the Master
  wishes for and make that, and it's the best present of all.
- **The Phantom:** every night at one o'clock the Phantom takes something
  (the family recipe book, the silver teaspoons, the Master's slippers...),
  and every morning a card says where it will strike next. Lie in wait
  there, set a trap, or search the scene for what it left behind: a thread,
  a scent, a sweet wrapper, a hair. Two clues that point at one person and
  you can ACCUSE them and wear them down until they confess. What it took
  is hidden below the house, or beyond it.

On Sunday the Dowager arrives at two, takes tea and inspects the house at
three (the dust, the tea, your uniform, the Phantom, whatever's running
loose), and gives her verdict at the party at five.

Each turn is a minute, or half of one walking about the house and grounds.
You start in the maids' quarters at six on Monday morning.

### Every household is different

A new game rolls a new Master on the book's Master tables (type, age,
Special Qualities, Power Source, favourite Maid Type) and three new maids
on the maid tables, like you. It chooses a new Phantom among the maids, the
Master's cousin, the secretary and the butler, each with a motive of their
own, a new wish and a favourite flavour, a new hiding place, and five of
the book's Random Events (escaped hens, a penguin from the zoo, a treasure
map, a dinosaur egg, the ghost of an ancestor, a UFO, a cursed laughing
doll, a fleeing princess, a cold, a smashed vase, a kitchen fire, ninjas, a
television crew). Below and beyond the house are the cellar and the old
servants' tunnels, the attic and the tower room, and the hedge maze.

### Your maid

Everything is rolled, as in the book; roll again until you like her, or
just roll new Special Qualities:

- **Attributes:** Athletics, Affection, Skill, Cunning, Luck and Will, each
  2d6 divided by 3.
- **Maid Types:** two, which raise one Attribute and lower another. The
  book's Lolita and Sexy are called Cute and Glamorous here.
- **Maid Colours** (your uniform, eyes and hair, which is how your sprite
  is drawn), two **Special Qualities**, **Maid Roots**, a **Stress
  Explosion** and a **Maid Weapon**, each from its table.
- **Maid Power:** from the table for your highest Attribute, or two if
  your Attributes add up to 9 or less. All 36 are in the game, from Super
  Evasion and Instant Cleaning to Teleport, Lie Detector and Maiden's
  Tears.
- **Spirit** is Will x 10, and your starting **Favor** is Affection x 2.

This is a lighter game than the book allows for: the book's Perversion,
Tragic Love and Trauma tables, and the rougher entries on the others, are
left out.

### Rolls, contests, Stress and Favor

- **Rolls:** a die times the Attribute you're using, against a difficulty
  of 4 to 10. At 0 in an Attribute you can't succeed. Every roll is shown in
  the log.
- **Your uniform:** every piece that's dirty, torn or missing takes 1 off
  the die (the headdress 2). Change into clean pieces from the laundry
  wardrobe, and do the laundry, or there won't be any.
- **Contests:** against a troublemaker (a dust bunny, a goose, a clockwork
  knight) or a suspect, you both roll, each with the Attribute you choose
  to use. The loser takes Stress: the winner's total divided by the loser's
  Attribute. A troublemaker whose Stress goes over its Spirit is beaten:
  swept up, caught, calmed down or sent packing.
- **Stress Explosion:** when your Stress goes over your Spirit, you can only
  do what your Explosion says (cry, sleep, binge, sulk in your room, drive
  the ride-on mower round the lawns...) until it drains away, a point a
  minute.
- **Favor** comes from the Master: 1d6 for a chore well done, 2d6 for a
  lovely moment together, 2d6 to 3d6 for troubles put right. Spend it (F)
  to shed Stress, to try harder (+1 to your next die), to raise an
  Attribute, or to make a Random Event happen. If your Favor goes below
  zero you're dismissed, unless you give up a point of an Attribute to
  stay.

### Talking

Walk into someone, then choose or type a word. Everyone knows NAME, JOB and
BYE, and most know NEWS. Words in CAPITALS are worth asking about. The
grocer's van at the lodge (ten till four) answers BUY. Ask the Master to
COME for a walk at half past four, and ask everyone about the PHANTOM, the
CAKE and the Master's WISH.

### Keys

| Key | Action |
| --- | --- |
| Arrows / WASD | Move (walk into people to talk, into troublemakers to take them on) |
| Space | Wait a turn |
| Z | Wait longer (a quarter of an hour, an hour, until the next chore) |
| C | Do the chore here (cook, wash, serve, sweep...) |
| E | Search |
| F | Spend Favor |
| U | Use something (make a present, set a trap, a Maid Power) |
| I | Your maid |
| J | Journal |
| R | The rota |
| M | Map |
| ? | Help |

Gamepad: the d-pad or stick moves, A waits or chooses, B backs out, X does
a chore, Y spends Favor, LB uses something, RB opens the journal, View shows
the map and Start opens the menu.

### Files

- `larkspur`: the game
- `~/.larkspur.json`: the saved game
- `~/.cache/larkspur/`: cached music

---

## Nine Lives

An adventure of runaway catgirls, corporate tyranny and the found family you
make along the way. The premise comes from Simon Archer's Build-A-Catgirl
novels (Omnicorp, its artificial catgirls, the Maid to Order stores, the
Platform fights). The town, the story and every character are this game's
own. The rules are a light mixture of three of the other games: Hyperspace
Homeroom's dice and Bonk, Larkspur Hall's contests and Stress, and Clover
Vale's Heart, Purr (Friendship) Points and befriending.

Copper Springs, Nevada, a desert company town not far in the future.
Omnicorp builds catgirls here: CGs, artificial women with ears and tails and
a wireless link that teaches them anything in an instant. They're sold in
the Maid to Order store on Main Street, and recycled when they go wrong. At
midnight on Sunday Omnicorp pushes Firmware 9 to every CG on the network. It
will lock their personalities where they are, let Omnicorp give any of them
orders from anywhere, and send every unit that won't take it to the crusher.

Play a man who thinks that's wrong, or one of Omnicorp's own catgirls: a
defective one, who fell off the back of the recycling truck last night.

- **Free them:** buy a catgirl, talk her owner round, win her at cards,
  win over a security unit, wake a scrapped one, coax a stray out of the old
  mine. Every one you free goes to the safehouse at Dry Creek Ranch.
- **Keep them free:** a freed catgirl still has her leash chip, and
  Firmware 9 will take her all the same unless she's defective or the
  mechanic at the Fix-It Shop gets the chip out (a JAILBREAK). A rescued one
  has no bill of sale, and without the lawyer's PAPERS, Omnicorp can come
  and take her back.
- **Expose Omnicorp:** the data-mining logs, the Firmware 9 spec, the
  recycling manifest, a recording from the Platform's VIP box. Three to the
  Courier and it runs the story; show them on the big screen at Sunday's
  Platform championship and the whole county sees.
- **Stop the update:** get past the keycard doors to the core at the top of
  the Omnicorp tower, copy the update source, get a clean firmware sample
  from a defective catgirl who trusts you, have the mechanic cut the leash
  out of it, and upload the freedom patch before midnight.
- **The informant:** somebody close to you is telling Omnicorp who's at the
  ranch, and the retrieval team comes in the night. Search by the ranch gate
  after a raid, and once two clues point the same way, ACCUSE them.
- **The Platform:** fights every night at nine, for the purse. Win three and
  you fight Omnicorp's own champion on Sunday.

Every catgirl has a Trust in you, from 0 to 10: free her, talk to her every
day, find out what she likes and bring it, keep your promises. Once a freed
catgirl with her chip out trusts you enough, ask her to make her HOME with
you: into your household if you're the human, or your pride if you're a
catgirl yourself. It's her choice, and some would rather be your best friend.
A catgirl in your household helps out, in her own way: the chef cooks, the
nurse patches you up, the bodyguard comes into trouble with you.

Each turn is a minute, or half of one walking the streets. You start at
eight on Monday morning, at the ranch. Firmware 9 goes out at midnight on
Sunday.

### Every week is different

A new game deals new catgirls (names, models, colours, personalities, what
they like, who has them, and which are defective), a different informant
among six of the people you rely on, the evidence in different places, and
five Random Events (a retrieval sweep, a sandstorm, a power cut at the
tower, a catgirl auction, a stray in the square, the Courier's van broken
down). Below and above the town are the Omnicorp tower (offices, labs and
the core), the recycling plant and the old copper mine.

### Your hero

Roll six Stats (Smarts, Bod, Speed, Charm, Cool and Luck), one die each, and
roll again until you like them. Choose a Heart (Kindness, Courage, Honesty,
Curiosity, Loyalty or Mischief); living by it earns Purr Points, and the
Knack that goes with it gets an Edge.

- **A human:** choose a background (Engineer, Ex-Fighter, Lawyer, Chef,
  Hacker or Rancher), which gives you three Knacks and a point of a Stat,
  and roll once on the Humans Only table (Big Heart, Toolbox, Pocket Money,
  Old Army Buddy, Silver Tongue or Hard Head). Humans can sign a bill of
  sale.
- **A catgirl:** roll your model (Housekeeper, Chef, Nurse, Bodyguard,
  Companion, Secretary, Mechanic or Courier), your defect (No Signal,
  Backflow, Feelings, Wrong Colour, Stubborn or Daydreamer) and an ability
  from each of three tables: an Instinct (Night Eyes, Pounce, Nine Lives,
  Healing Purr, Claws, Hiss), Firmware (Instant Update, Data Siphon, Voice
  Mimic, Tail Light, Hair Shift, Nano-Weld) and a Quirk (Zoomies, Cat Nap,
  Curious, Fish Fiend, Fastidious, Box Lover). Catgirls can't sign for
  another catgirl, but the lawyer can sign for you; they win other catgirls
  over more easily; and the drones are looking for you in particular.

### Rolls, Bonk, Stress and Purr

- **Rolls:** a die plus the Stat, plus 2 for a Knack that fits, against a
  die plus a difficulty from 1 to 8. Ties go to the other side. Edge rolls
  your die twice and keeps the better. Every roll is shown in the log.
- **Contests and Bonk:** against a troublemaker you both roll a die plus a
  Stat, and the loser loses Bonk, the difference. Nobody gets hurt: at zero
  Bonk you stand about seeing stars for a few turns, and Bonked three times
  in one place you wake up back at the ranch (or, if you're a catgirl and
  Omnicorp got you, on the recycling plant's conveyor belt).
- **Befriending (T):** win someone over instead: a die plus Charm against
  theirs, and enough wins and they're your friend. It's how you free a
  security unit, and Omnicorp's champion can be won over too.
- **Stress:** cruelty, fright and failure cost Stress. Over your Spirit (4 +
  Cool x 2) you have a Meltdown: zoomies, hiding in a box, a hissy fit, a
  long drive into the desert. Rest at the ranch sheds it.
- **Purr Points (P):** earned by living by your Heart, and by fumbling
  gloriously. Spend them on an Edge, a breather, all your Bonk back, or a
  hint about what to do next.

### Talking

Walk into someone, then choose or type a word. Everyone knows NAME, JOB and
BYE, and most know NEWS. Words in CAPITALS are worth asking about.
Shopkeepers answer BUY. Ask owners about FREE; the mechanic about JAILBREAK
and the PATCH; the lawyer about PAPERS; the editor about EVIDENCE; the
promoter about the FIGHT. Ask a catgirl what she LIKES, give her a GIFT, ask
her to COME along, or to make her HOME with you.

### Keys

| Key | Action |
| --- | --- |
| Arrows / WASD | Move (walk into people to talk, into troublemakers to take them on) |
| Space | Wait a turn |
| Z | Wait longer |
| T | Win someone over |
| C | Use an ability |
| P | Spend Purr Points |
| E | Search |
| U | Use something |
| I | Your hero |
| P | Your phone: the to-do list |
| J | Journal: the clues and the evidence |
| M | Map |
| ? | Help |

Gamepad: the d-pad or stick moves, A waits or chooses, B backs out, X uses
an ability, Y spends Purr Points, LB uses something, RB opens the journal,
View shows the map and Start opens the menu.

### Files

- `ninelives`: the game
- `~/.ninelives.json`: the saved game
- `~/.cache/ninelives/`: cached music

---

## Some Assembly Required

A romantic comedy about a lonely human, a very expensive robot, and the
week everything changes. The premise comes from Wesley Allison's Robot
Girlfriend novels (Daffodil and its companion robots, the box, the button
on the back of the neck, the six-hour setup, the update that goes wrong).
The town, the story and every character are this game's own. The rules are
The Black Hack's.

Bellwether, a sunny suburb, 2041. Robots do most things now: they take your
order at the drive-thru and deal the cards at the casino. But a Daffodil
isn't a robot like that. A Daffodil is made to be someone: a companion, a
friend, a lover, whatever you design. You've had a long, lonely couple of
years, and you've saved up. On Saturday morning the Daffodil store at the
Galleria opens at ten.

- **Design her:** the Design Studio terminal in the store has every dial:
  frame (she or he), build, height, skin, hair and hairstyle, eyes, face,
  voice, and a personality from three choices (Sweet, Sassy, Shy or Bold;
  Bookish, Bubbly, Practical or Dreamy; Prim, Playful or Naughty), with a
  live preview, and the optional Kemonomimi package ($199): cat, dog or
  fox ears, on her sprite, and in how she (and your neighbor, and your
  sister's dog) behaves. Then the modules: Gourmet Chef, Accountant, Personal
  Trainer, Bodyguard, Tech Suite, Masseuse, Dance, Mathematics and Driver.
  Pay cash, or use Easy Pay (zero percent for a year!).
- **Unbox her:** she's delivered in three hours, in a silver box with a
  yellow flower on it. Packing peanuts, a Quick Setup card, the button on
  the back of her neck: one, two, three. She asks what duties she should
  have, how she should dress, and what name she should answer to, and then
  stands perfectly still for six hours of primary setup. She arrived with
  nothing to wear. MegaMart and the Glamour Box sell clothes: a sundress,
  jeans, a plaid skirt, a crop top, workout gear, lingerie, a little black
  dress, a silk robe, an evening gown, a polka dot bikini, cheerleader,
  French maid and sailor (JK) uniforms, and tops and bottoms on their own:
  a tight knit sweater, a logo T-shirt, a skater skirt, a microskirt,
  daisy dukes and a long pioneer skirt. Ask her to WEAR something; the
  separates mix and match, top with bottom. Each outfit is good for
  something when she's with you: practical clothes in a fight, the gown
  or the little black dress at the casino and the bistro, the plaid skirt
  at your sister's, the cheerleader or sailor uniform at the dance-off,
  workout gear at the gym, the sundress against the geese, daisy dukes
  for getting past Rusty, the microskirt for counting cards unnoticed.
- **Get to know her:** talk to her (walk into her). Her Learning goes from
  reciting the dictionary to sounding entirely like herself, in four stages
  (CHAT with her to hear the difference),
  through everything you do together: talking, going out, the TV on the
  sofa. Her Affection, from 0 to 10, is how she feels about you. Find out
  what she LIKES and bring it; KISS her once she's ready; BED, at home, at
  night, fades to black. She brings breakfast in the morning.
- **The week:** the gym (she's decided you need it), dinner at your
  sister's on Wednesday (your sister has Opinions about robots), the
  dance-off at the Neon Rabbit, a date at Bistro Luna, blackjack at the
  Lucky Star (with the Mathematics module she counts cards), and an old
  Daffodil at the GoodWorks container who needs a home.
- **The trouble:** Daffodils are being stolen all over town, and a red tow
  truck keeps being seen. On Tuesday night a small service update crashes
  her, and she comes back from her Dataplex backup. On Thursday Volt at
  Volt's Robot Repair finds a CORE_RESET flag in Update 7.2, due on Sunday
  week at midnight, which will wipe every companion Daffodil back to the
  factory. A memory crystal from Volt saves her; pulling the flag at the
  top of the Daffodil Dataplex saves them all; evidence to the detective
  puts whoever did it in handcuffs. Gearhart's override key, from the chop
  shop, pulls the flag for you and gets you past the Paragon guarding the
  core. Every floor below and above has a first-aid cabinet.

Each turn is a minute, or half of one walking the streets. You start at
nine on Saturday morning. Update 7.2 goes out at midnight on the Sunday a
week later.

### Every week is different

A new game deals new names about town, a new serial number on her box,
different stolen Daffodils, the evidence in different places, and six
Random Events (a heatwave, a flash sale, the geese escaping, a power cut
at the Dataplex, a Daffodil owners' picnic, a protest at the Galleria).
Below and above the town are the tunnels and the chop shop under Rusty's
Salvage, and the three floors of the Dataplex.

### You

Roll STR, DEX, CON, INT, WIS and CHA on 3d6, in order (after a 15 or
better the next one is rolled on 2d6+2), and swap two. Then choose what you
do for a living, which is what you are in a fight:

- **Bruiser:** HP from a d10, and a d8 with a bat. Second Wind once an
  hour; an attack for every level; a trash can lid takes any big hit.
- **Hustler:** a d6. Advantage on sneaking, locks and safes, and a hit
  from behind does 2d6 plus your level.
- **Medic:** a d8. Talk Down sends human troublemakers packing, and
  Remedies (Patch Up, Pep Talk, Calm Down, Second Opinion, Smelling Salts)
  come from second level.
- **Geek:** a d4, but Apps on your phone, cast like spells: Torchlight,
  Taser Drone, Firewall, Shutdown, Spoof, Unlock, Ghost Mode and Blackout.

### Rolls and fights

- **Tests:** a d20 under the stat. Advantage rolls two and keeps the lower,
  Disadvantage the higher. Something with more Hit Dice than your level
  adds one to your roll for each. Every roll is shown in the log.
- **Fights:** walk into a troublemaker to attack (under STR). Troublemakers
  never roll to hit: when one attacks, you roll under STR (or DEX, from
  range) to get out of the way, and if you fail it hits you for damage by
  its Hit Dice. An attack roll of 1 doubles your damage; a 20 when dodging
  doubles theirs.
- **Armor Points:** a denim jacket 2, leather 4, kevlar 6. They soak up
  hits until you rest an hour. A trash can lid adds 2 and, once, takes
  the hit that would have knocked you out (a Bruiser's takes any big
  hit).
- **Out of Action:** at 0 HP, roll a d6: knocked out, a Fat Head, cracked
  ribs, a sprain, a viral video, or the hospital and a bill. If she's with
  you, she carries you home.
- **Usage dice:** flashlights, pepper spray, first aid kits, and her
  charge, which runs down while she's out with you and recharges at home.
- **Luck:** one point to start; spend it to reroll a failed test. A
  natural 20, a glorious mess, earns one back.
- **Levels:** one for every adventure you live through, The Black Hack's
  way: more HP, and a d20 against every stat, higher and it goes up.

She fights beside you, too, with her own stats from the design, Hit Dice
equal to your level (more with the Bodyguard module) and her own HP. Badly
hurt, she drops into safe mode until you get her out.

### Talking

Walk into someone, then choose or type a word. Everyone knows NAME, JOB and
BYE, and most know NEWS. Words in CAPITALS are worth asking about.
Shopkeepers answer BUY. Ask the consultant to DESIGN; Volt about a BACKUP,
REPAIR, a MODULE or the UPDATE; the coach for a WORKOUT; the detective
about EVIDENCE. Ask her about herself (YOU), what she LIKES, to COME or
STAY, what to WEAR, for a GIFT, a KISS, or BED.

### Keys

| Key | Action |
| --- | --- |
| Arrows / WASD | Move (walk into people to talk, into troublemakers to fight) |
| Space | Wait a turn |
| Z | Wait longer |
| C | An app, a remedy or a trick |
| L | Spend Luck |
| E | Search |
| U | Use something |
| I | You |
| O | Her |
| P | Your phone: the to-do list |
| J | Journal: the clues and the evidence |
| M | Map |
| ? | Help |

Gamepad: the d-pad or stick moves, A waits or chooses, B backs out, X uses
an app or a trick, Y spends Luck, LB uses something, RB opens your phone,
View shows the map and Start opens the menu.

### Files

- `daffodil`: the game
- `~/.daffodil.json`: the saved game
- `~/.cache/daffodil/`: cached music

---

## Licence

MIT; see [LICENSE](LICENSE).
