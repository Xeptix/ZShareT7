# ZShare T7

**Weapon sharing for Black Ops III Zombies**

by Xep

[**Download the latest release**](https://github.com/Xeptix/ZShareT7/releases/latest)

[![ko-fi](https://ko-fi.com/img/githubbutton_sm.svg)](https://ko-fi.com/F6L1285ROA)

Trade guns with a teammate, hand them points, give away a box hit or a Pack-a-Punch you
don't want, and pay for a teammate's perk, spin or pack. All of it from the use button,
with prompts that read like the game's own.

- Look at a teammate and press **use** to trade weapons. Ammo, attachments, camo and the
  Alternate Ammo Type go with the gun.
- **Crouch** first and the same press gives them 1000 points instead.
- Crouch and press use at the **box** while the weapon you paid for is up, and anyone can
  take it. The same at the **Pack-a-Punch**.
- Crouch and press use at a **perk machine**, or at the box or the Pack-a-Punch while
  nobody is using it, and the next teammate to use it pays nothing.

This is the Black Ops III port of [ZShare](https://github.com/Xeptix/ZShare). Every port has
the same settings, with the same names, defaults and meanings.

---

## Requirements

Black Ops III zombies, on a client that loads a loose GSC script. No other mods or
dependencies.

**Only the host needs this file.** Every part of ZShare runs on the host and reaches
everyone else as ordinary server-to-client traffic - the prompts, the swap, the box, the
machines, the points, the sounds. Players joining your game install nothing.

Works on the stock maps and on custom ones, as long as they are built on the stock zombies
scripts.

---

## Install

The download carries the script laid out for each route. Copy the folder that matches how
you play:

| You play with | Copy | Into |
|---|---|---|
| **BOIII** or **Ezz BOIII** | `Black Ops III\boiii\custom_scripts\zshare.gsc` | your Black Ops III folder |
| **BOIII**, per user | `AppData\boiii\data\custom_scripts\zshare.gsc` | `%localappdata%` |
| **T7x** | `t7x\custom_scripts\zshare.gsc` | your Black Ops III folder |
| **The injected build** | `t7-compiler\scripts\zshare\main.gsc` | your compiler project |

Original BOIII reads both of its script folders, so either works there; the one under
`%localappdata%` survives verifying the game's files, and the one in the game folder travels
with a copied install. Use one, not both.

**Ezz BOIII clears its AppData folder every time it launches**, taking anything it didn't put
there with it - so on Ezz BOIII, use the game folder. A copy in AppData is gone before the
game has started.

**T7x runs compiled scripts only**, so its copy is not readable text like the others - it
is the same ZShare, compiled. It goes in the `t7x` folder inside your Black Ops III folder,
under the name `zshare.gsc`.

**The settings menu is the `ui_scripts\zshare` folder beside each of those**, and it is
optional - ZShare runs without it, and every setting is still a dvar. Copy it the same way
you copied the script: whichever route you used carries a `ui_scripts\zshare` folder next to
its `custom_scripts`, and the installer writes both. The injected build has none: it loads
into a game that reads no menus of its own.

### Or the Steam Workshop

ZShare is on the Steam Workshop as well, as an ordinary mod:
[**subscribe here**](https://steamcommunity.com/sharedfiles/filedetails/?id=3802815009). Pick it under **Mods**; nothing to copy, and it
updates itself.

The two are the same script and you only need one of them. The Workshop version is the
easier install and works on a stock copy of the game; the loose script needs a client that
loads one, and leaves your mod slot free for something else.

**The Workshop version speaks every language Black Ops III is sold in** - English, French,
Italian, Spanish, German, Portuguese, Russian, Polish, Japanese, and Traditional and
Simplified Chinese. Each player reads the prompts and messages in the language their own
game is set to, so a French host and a Japanese teammate each read their own. The loose
script is in English.

**With both installed**, whichever loads first runs and the other stands down - they do not
stack. `zs_only_script` and `zs_only_mod` force the choice if you want to test one against
the other, and the build stamp in the corner says which one you are looking at.

**Running Xep's other Z mods as well?** Black Ops III runs one mod at a time, so two
Workshop mods means choosing between them.
[**ZBundle**](https://steamcommunity.com/sharedfiles/filedetails/?id=3802815997) is ZPause,
ZShare, ZStats and ZTweaks in one mod - the same scripts and the same settings, in one
subscription.

### Or run the installer

The download has an **`installer`** folder, one for each system:

```
installer\windows\install.bat
installer/linux/install.sh
```

Each one finds your Black Ops III folder and installs for every client you have -
**BOIII**, **Ezz BOIII** and **T7x** - skipping any that aren't there, so it never makes a
folder for a client you don't use. Keep a copy of the game folder for each client -
`Call of Duty Black Ops III EzzBOIII` beside `Call of Duty Black Ops III` - and a copy with
a client folder of its own is installed to as well. It shows you what it is about to copy
and asks once.
`install.bat -Yes` and `install.sh --yes` copy without asking, `-Uninstall` / `--uninstall`
removes what an install put there, and `-Find` / `--find` only shows what it detects. When it
can't find your game, `-To <folder>` / `--to <folder>` points it there.

You don't need to restart the game to load a script - just end the current game and start
a new one.

---

## Usage

Every action is a prompt on screen, the same kind the game shows at a door or a wall buy.
What a prompt says is what a press of **use** will do.

| Prompt | When you see it | What the press does |
|---|---|---|
| `Hold [use] to trade weapons` | Looking at a teammate | Offers them the weapon in your hands |
| `Hold [use] to accept the trade` | Looking at a teammate who offered you a trade | Swaps their offered weapon for the one you're holding |
| `Hold [use] to cancel the trade` | Looking at the teammate you offered a trade to | Withdraws the offer |
| `Hold [use] to give 1000 points` | **Crouched**, looking at a teammate | Gives them 1000 points |
| `Hold [use] to thank them (100 points)` | **Crouched**, looking at someone who just did you a good turn | Sends them 100 of your points |
| `Hold [use] to share this weapon` | **Crouched** at the box or the Pack-a-Punch, with the weapon you paid for waiting | Lets anyone take it |
| `Hold [use] to take the shared weapon` | Looking at a box or Pack-a-Punch somebody shared | Takes it |
| `Hold [use] to buy this perk for a teammate [Cost: 2500]` | **Crouched** at a perk machine | Pays for the next drink from it |
| `Hold [use] to buy a spin for a teammate [Cost: 950]` | **Crouched** at the box while nobody is using it | Pays for the next spin |
| `Hold [use] to buy a Pack-a-Punch for a teammate [Cost: 5000]` | **Crouched** at the Pack-a-Punch while nobody is using it | Pays for the next pack |
| `Hold [use] to take back your payment` | **Crouched** at a machine you paid for | Gives you your points back |
| The machine's own prompt, at `[Cost: 0]` | At a machine a teammate paid for | Uses it for free |

Crouching is the whole modifier. Stand up and every prompt goes back to what it always was;
crouch and it turns into giving. Nothing else changes about how you play.

A few chat words, for when you've already walked away:

| Action | Input |
|---|---|
| Share the box hit or Pack-a-Punch you paid for | type `!share` |
| Thank whoever just did you a good turn | **Crouch**, look at them, press **use** - or type `!thank` |
| Send any amount of points | type `!tip 500`, or `!tip <name> 500` |

---

## Trading

What you offer is **the weapon in your hands** when you press. Your teammate can see it
there; nothing needs naming. What you get back is **whatever they're holding** when they
accept - so they switch to the gun they want to give before pressing.

An offer stays open for 10 seconds. It lapses on its own if you switch to your other
weapon, if the two of you move more than twice the prompt range apart, or if either of
you goes down. Pressing use on them again withdraws it. Offering to somebody else replaces
it, and both of you are told either way.

**What travels with a gun:** the ammo, the attachments, the camo and the Alternate Ammo
Type it was carrying. It arrives as the same weapon that left.

**What can't be traded:** grenades, the knife, shields, mines, equipment, hero weapons and
anything the box itself won't sell you.

**Same gun twice.** A trade that would leave someone holding a gun they already carry - or
the other half of it, plain against Pack-a-Punched - is refused.

---

## Sharing a box hit

You pay, the weapon rises, and it's yours to take. **Crouch and press use** at the box and
it's everyone's: the box prompt changes for the whole room, and whoever presses use takes
it - you included, if nobody's quicker.

This is the state the game already puts a box in after the hacker re-spins it, so the box
is doing nothing it doesn't do on its own.

## Sharing at the Pack-a-Punch

The same at the machine. Crouch and press use while your upgraded weapon is waiting, and
anyone can take it. Whoever does gets it exactly as the machine would have handed it to
you.

## Giving points

Crouch, look at a teammate, press use: 1000 points move from you to them. Each press is one
gift, a second apart, so three presses is 3000. You need the points to give them.

---

## Paying for a teammate

Crouch at a perk machine, or at the box or the Pack-a-Punch while nobody is using it, and
the prompt turns into an offer to pay for a teammate. Press use and you pay the machine's
price. From then on the machine's prompt reads **`[Cost: 0]`**, and the next teammate to
use it pays nothing - a drink from a perk machine, a spin from the box, a pack from the
Pack-a-Punch. Everybody hears about it, and whoever paid is told who used it.

One payment waits at a machine at a time. While yours is waiting, crouch at the machine
again and the prompt offers your points back. If you don't own that perk yourself, you can
stand up and drink it too.

| When | What happens |
|---|---|
| A paid spin turns up the teddy bear | The spin cost nothing, so the game's own refund is nothing - whoever paid gets their points back instead |
| The box moves | The paid spin moves with it |
| A fire sale is on | Nobody can pay at the box while it's cheap, and a payment already waiting holds until the sale ends |
| The teammate already holds as many perks as they're allowed | They're refused the way the machine refuses a purchase, and the drink stays paid for |
| A GobbleGum is already making things free | Paying is refused while it's active, since nobody would be paying for anything |
| You're playing solo | There's nobody to pay for, so the prompt never appears |

Stand up and every machine works exactly as it always has.

## The perk limit

`zs_perk_limit` sets how many perks a player can hold. `0`, the default, is the game's own
limit of four. Any other number replaces it, and `-1` removes the limit.

It's one limit whether a perk is bought or paid for by a teammate, and a map that hands out
extra slots of its own keeps them on top of whatever number you set.

---

## Configuration

Every setting is at the top of the file under `zs_load_config()`, and each one is also a
dvar of the same name. The script creates each dvar with its default on load, so you can
set them straight from the console:

```bash
zs_points_amount 500
```

The config is re-read every five seconds while the game runs, and again on every press,
so a change takes effect **almost straight away** - no map restart needed. Anything
already set in your config before the map loads is left alone.

`set zs_config_print 1` in the console prints every setting that isn't at its default to
the host's screen, then puts the switch back so it can be used again.

### The settings menu

Every setting below has a page of its own, on the Workshop build and on BOIII, Ezz BOIII and
T7x, so none of them needs the console. On the Workshop build, load ZShare from the Mods
menu; on the other three the installer puts the menu in the game folder's `ui_scripts`,
beside the script.

The host gets to it two ways, and both open the same page:

- the zombies lobby has a **ZSHARE SETTINGS** button;
- the game's own pause menu has a **ZSHARE SETTINGS** row, under RESUME GAME, during a match.

A category for each part of ZShare across the top - **TRADING**, **POINTS**, **THANKS**,
**SHARING**, **PAYING**, **PERKS**, **PRESENTATION** and **SOUNDS**. The bumpers move between
them, or **Q** and **E**, or the arrows either side of the strip, or a click on the category
itself; the names either side and `CATEGORY n / total` say where you are and what is next. The
settings are down the left, seven at a time with the rest scrolled, and the panel on the right
says what the one under the cursor does, what it is called in the console, what its default is,
what a change to it waits for and who it is for. Left and right change a setting. **DEFAULT**
leaves it to the script's own default. Opening it from the pause menu does not close the pause
menu.

**Y**, or **F** on a keyboard, takes everything still at its default out of the category you
are on, so a long one shows only what has been changed; press it again, or change category, to
put them back.

Along the bottom: **BACK**, **RESET TAB**, **RANDOMIZE** and **RESET ALL**. The last three ask
before they do anything, with **NO** already under the cursor, and RANDOMIZE says so before it
runs - DEFAULT is one of the values it can pick. RESET TAB is the category you are on; RESET
ALL is every ZShare setting there is.

A change lands within five seconds, whichever way in you used - the script re-reads its
settings on every press and on a timer besides. Two are the exception and the panel says
which: `zs_show_hint` is drawn as a player spawns and `zs_range` is read as a prompt is built.
It is saved as well, so it is still set the next time the game starts. Black Ops III keeps no
dvar once it closes, so that goes into the offline zombies loadouts, which nothing in a
zombies game shows or uses - the mod's own copy of them on the Workshop build, your own on the
three loose clients, which have no mod to keep them in. The t7-compiler route has no way in at
all: it injects into a game that loads no menus of its own.

It is the host's page only: every setting is one of the host's dvars, and a guest changing one
would change nothing. The sound rows offer the four aliases ZShare itself uses, plus silence -
the others in [Sounds](#sounds) are still the console's.

The page is the one Xep's other Black Ops III mods draw, so a bundle of them puts every mod's
settings on one screen with a category each and the title **ZBUNDLE SETTINGS**, which names the
mod owning the category you are on. Each mod keeps its own settings in its own place; nothing
here reads or writes another's. A bundle also gets a **MODS** category, first, which switches
each of those mods on and off - ZShare's row there is `zs_enabled`, and it lands on the next
match. Last, in every build, is **CHANGED**, which lists everything moved off its default in one
place, whichever mod owns it.

The Workshop build draws the page over a background image of its own. BOIII, Ezz BOIII and T7x
draw the same page over a half-transparent black panel - an image has to come out of a
fastfile, and there is none on those routes.

| Dvar | Default | What it does |
|---|---|---|
| `zs_enabled` | `1` | ZShare itself. Off, the script loads and does nothing else - no prompts, no hooks, no threads. **Read when the match loads**, so it takes on the next one. |
| `zs_only_script` | `0` | Debug. With both the loose script and the Workshop mod installed, run only the loose one. |
| `zs_only_mod` | `0` | Debug. The same, the other way round. Both off - the default - is whichever loads first. Both on leaves nothing running. **Read when the script loads**, so end the game and start a new one for a change to take. |
| `zs_debug` | `0` | Print what the script decides and why, to the first player's screen. |
| `zs_trade` | `1` | Trade weapons with a teammate. |
| `zs_trade_offer_time` | `10` | Seconds an offer stays open. |
| `zs_trade_upgraded` | `1` | Pack-a-Punched weapons can be traded. Off, and the prompt says so when you try. |
| `zs_range` | `64` | How close you have to be for the prompt to appear, in units. An offer lapses at twice this. |
| `zs_points` | `1` | Crouch and press use on a teammate to give them points. |
| `zs_points_amount` | `1000` | How many points one press gives. |
| `zs_points_cooldown` | `1` | Seconds between gifts from one player. |
| `zs_thank` | `1` | Thank whoever did you a good turn, and the `!tip` word. |
| `zs_thank_amount` | `100` | What one thank sends. Comes out of your own points. |
| `zs_thank_time` | `30` | How long a good turn stays thankable, in seconds. |
| `zs_box_share` | `1` | Crouch and press use at the box to share the weapon you paid for. |
| `zs_pap_share` | `1` | The same at the Pack-a-Punch. |
| `zs_perk_pay` | `1` | Crouch and press use at a perk machine to pay for a teammate's drink. Off stops new payments; one already waiting still works and can still be taken back. |
| `zs_box_pay` | `1` | The same at the box, for the next spin. |
| `zs_pap_pay` | `1` | The same at the Pack-a-Punch, for the next pack. |
| `zs_perk_limit` | `0` | How many perks a player can hold. `0` is the game's own limit, a number replaces it, `-1` is no limit. See [The perk limit](#the-perk-limit). |
| `zs_show_hint` | `1` | Tell players what the prompts do, once, shortly after they spawn. |
| `zs_messages` | `1` | The one-line messages - who traded with whom, who shared or paid for what, who gave points. Off leaves the prompts and the sounds. |
| `zs_offer_sound` | `zmb_perks_packa_ready` | Played to the player an offer is made to. `none` = silent. |
| `zs_trade_sound` | `zmb_perks_packa_ready` | Played to both players when a trade goes through. `none` = silent. |
| `zs_share_sound` | `zmb_perks_packa_ready` | Played to everyone else when a weapon is shared or a machine is paid for. `none` = silent. |
| `zs_points_sound` | `zmb_cha_ching` | Played when points are given, paid or handed back. `none` = silent. |
| `zs_deny_sound` | `zmb_no_cha_ching` | Played when a press can't do what the prompt said - not enough points, a weapon that can't be traded. `none` = silent. |

### Sounds

All five are stock aliases, so the script stays a single drop-in file. A custom sound would
have to be installed by **every player** rather than just the host, so ZShare uses the
game's own audio instead.

Swap one in from the console, or silence one with `none`:

```bash
zs_trade_sound none
```

---

## How this port differs

The same features with the same settings as every other port, allowing for what Black Ops
III gives a script:

- **The chat word is heard per player.** Every other port hears chat once, for the whole
  server; this engine tells the player who typed, so each player carries a listener. What
  you type is the same.
- **It ships twice.** A loose script for the clients that load one, and a Workshop mod for
  everybody else - the same script in the dialect the mod tools want. Black Ops II's port
  does the same thing with its mod folder, and the same two settings pick between them.
- **The Workshop version is translated.** A mod built with the mod tools carries its own
  words for every language the game ships, and each player's game draws them in its own
  language. A loose script has nowhere to carry them, so it is in English, as every other
  port is.
- **Nothing stock is replaced.** The other ports replace one or two of the game's own
  functions. This port uses the hooks the game already offers and, where it needs a loop of
  its own, ends the stock one the way the game ends it and runs its copy in the same frame
  - so the same script works on every client rather than only the ones that can replace a
  function.
- **`none` silences a sound.** An empty dvar can't be set from in game on this engine.

---

## How it works

**The prompts on players are the game's own use triggers.** Every player carries one per
teammate, linked to them the way the revive prompt links to a downed player, so it follows
them and only lights up when that teammate looks at them.

**A weapon changes hands through the game's own locker mechanism** - the same pair of
functions the weapon locker uses to put a gun away and take it back out - with the
Alternate Ammo Type carried across the way Zetsubou's clone plant carries it.

**The box already knows how to be shared, and how to be free.** After the hacker re-spins a
box, the stock code marks it and hands the weapon to whoever presses use; sharing sets that
mark. After the hacker summons a box, the stock code opens it for the next player without
charging; a paid spin sets those two.

**A paid drink goes through the game's own validation hook**, so the drink, the animation
and the perk are the machine's own work from start to finish.

**Points go straight onto your score**, so a gift doesn't count as points you earned.

**Every prompt is one of a fixed handful of strings.** Hint strings are configstrings, a
pool that doesn't recycle, so a weapon name or a player name never goes on a prompt. Names
go in the chat line, which isn't one.

---

## Notes

- **Prompts and other prompts.** A teammate standing in front of a door or a machine shares
  the space with it; the engine shows whichever prompt you're looking at most directly.
- **Crouching over a downed teammate** revives them. The pay prompt steps aside for a
  revive, the same way the machine's own prompt does.
- **Downed players** have no prompt and can't accept one. Going down lapses an open offer
  in either direction.
- **GobbleGums that change prices** are left alone: while one is making things free there
  is nothing to pay for, and ZShare says so rather than taking your points.
- **Custom maps** get all of it: the prompts, the box and the machines read nothing but the
  stock script structures every Black Ops III zombies map is built on.

---

## Testing

Black Ops III has no script compiler this project can run - gsc-tool answers "not
implemented" for both of its dialects - so ZShare T7 is checked against the stock script
dump instead: every function it calls is a real call a zombies script can reach, and every
entity field, notify, flag and sound alias it borrows exists there.

---

## Ports

| Game | Repo |
|---|---|
| Black Ops 4 (T8) | [ZShareT8](https://github.com/Xeptix/ZShareT8) |
| Black Ops III (T7) | ZShareT7 - you are here |
| Black Ops II (T6) | [ZShare](https://github.com/Xeptix/ZShare) |
| Black Ops (T5) | [ZShareT5](https://github.com/Xeptix/ZShareT5) |
| World at War (T4) | [ZShareT4](https://github.com/Xeptix/ZShareT4) |

Versions are kept in step: the same version number means the same feature set, allowing
for what each engine can actually do.

**All five in one download.** The [Treyarch
Bundle](https://github.com/Xeptix/ZShare/releases/latest) carries every game ZShare runs
on, laid out as each drops in - the `Plutonium` tree for three of them, this game's
folders, Black Ops 4's mod folder - with one installer that asks which of them to install.

---

## Changelog

### v1.3

- **A settings screen.** Every setting has a page of its own, with a category strip, a
  description panel, a changed-only filter and DEFAULT, RESET, RANDOMIZE and RESET ALL along
  the bottom -- reached from a **ZSHARE SETTINGS** button in the zombies lobby and a row of
  the same name on the game's own pause menu, both for the host. It is on the Workshop build,
  BOIII, Ezz BOIII and T7x, and a change is saved so it is still set the next time the game
  starts. It is the page every one of Xep's Black Ops III mods draws, so a bundle of them
  shows one **ZBUNDLE SETTINGS** page with a category for each mod's settings and a **MODS**
  page that switches each of them on and off. See [The settings menu](#the-settings-menu).
- **`zs_enabled`.** ZShare itself, on by default. Off, the script loads, says so to any other
  mod that asks, and does nothing else: no prompts, no hooks over the stock scripts, no chat
  words and no threads. Read as the match loads, so a change takes on the next one.
- **Other mods can find ZShare.** It registers `level.zmods["zshare"]` as it finishes
  loading -- its version, whether it is switched on, a way to make it re-read its settings,
  and two perk-limit readers: the limit the map would give on its own, and the one ZShare is
  actually holding it to. A mod that sets a limit of its own can ask rather than guess, and
  keep the extra slots a map hands out. Switched off, the descriptor still goes up saying so.
- **Trading a Pack-a-Punched gun keeps its Alternate Ammo Type.** The AAT was read off the
  wrong player and handed over in a form the game does not store, which lost the giver's and
  corrupted the receiver's.
- **A perk payment is only spent at the machine it was left at.** A free perk from Der
  Wunderfizz, Zetsubou's fruit or the spider quest spent a payment waiting across the map.
- **Reviving comes first again.** The check meant to keep the pay prompt away while you stand
  over a downed teammate was reading the wrong player's field and never fired.
- **Paying with Shopping Free is refused** rather than spending the gobblegum on somebody
  else's turn and leaving a payment worth nothing.
- **A trade offer lapses again.** Every offer after the first was counted the same, so it never
  timed out, never cancelled when you put the weapon away, and never cleared on a down.
- **`!tip` works on every client again.** The check that skips a leading character a client
  can put in front of a chat message compared one character too few, so `!tip` was ignored
  wherever that happens. A message that only starts with the word -- "!tipsy" -- is no
  longer read as one either.

### v1.2

- **Nacht der Untoten, Verruckt and Shi No Numa load with the Workshop mod.** ZShare no
  longer forces the Pack-a-Punch system to load on maps which do not have the machine,
  keeping their original clientfield registration tables unchanged.

### v1.1

- **Paying at a perk machine or the Pack-a-Punch works.** Crouched at either, the machine's
  own prompt was the one on screen, so the press bought the perk rather than paying for a
  teammate. ZShare's prompt shows now, for the player it is meant for, and the machine's
  comes back the moment they stand up.
- **Paying for a perk works on maps that power their machines their own way.** A custom map
  whose power doesn't go through the stock perk power script never offered the pay prompt.
- **A trade of two identical guns is refused** - "You already have that weapon" - the way
  Black Ops II has always refused it. Only the same gun both ways; a plain gun for its
  Pack-a-Punched version still trades.

### v1.0

- Initial release.
- **Trade weapons** with a teammate from the use prompt. Ammo, attachments, camo and the
  Alternate Ammo Type travel with the gun.
- **Give points** with a crouched press of the same prompt. `zs_points_amount` sets how
  many.
- **Share a box hit** or a **Pack-a-Punch** with a crouched press at the machine, or with
  `!share` from chat.
- **Pay for a teammate** at a perk machine, the box or the Pack-a-Punch with a crouched
  press, and take the payment back the same way. `zs_perk_pay`, `zs_box_pay` and
  `zs_pap_pay` switch each one.
- **Thank a teammate** who paid for you, shared a hit or gave you points: for a while the
  crouched prompt on them offers a small thank, or type `!thank`. The points come out of
  your own. `zs_thank_amount` and `zs_thank_time` set how much and how long.
- **Tip any amount** with `!tip 500`, or `!tip <name> 500`.
- **`zs_perk_limit`** - how many perks a player can hold, or `-1` for no limit.
- **The Workshop version in eleven languages**, each player reading their own: English,
  French, Italian, Spanish, German, Portuguese, Russian, Polish, Japanese, and Traditional
  and Simplified Chinese.
- Every setting is a dvar, re-read while the game runs, and `set zs_config_print 1` lists
  the ones you've changed.

---

## Credits

- **Xep** - author
- **Treyarch** - `_zm_magicbox.gsc`, `_zm_perks.gsc`, `_zm_weapons.gsc`, `_zm_laststand.gsc`: everything this stands on
- **[Serious](https://github.com/shiversoftdev)** - t7-source, and the compiler the injected build is made with
- **D3V Team** - L3akMod, which the Workshop build's settings menu is built with
- **[BOIII](https://github.com/momo5502/boiii)**, **[T7x](https://github.com/shiversoftdev/t7x)** - the clients this runs on

---

## License

MIT - see [LICENSE](LICENSE). Use it, fork it, ship it in a server pack. Keep the
copyright notice and the header block at the top of `zshare.gsc`.

That covers ZShare's own code. Treyarch's stock scripts are referenced here, not
included, and are not mine to license.
