# dmpower-dungeons-and-dragons-5e

A interactive terminal-based DUNGEONS & DRAGON'S 5E Toolkit. See the [MANUAL](MANUAL.md) for screenshots and information about the tools.

- [download latest release](https://github.com/mattearly/dmpower-dungeons-and-dragons-5e/releases)

---

### 1. How To BUILD & RUN

*Relies on C++ Standard 11, Boost filesystem, and Make*

*Built on Linux and will probably run best on Linux right now. Runs fine on Cygwin and WSL for Windows*

**Linux**
- open terminal
- `clone` repo (or download release and unzip)
- `cd` into directory
- `make run` (go install dependencies if something fails in the build, then try again)

**Windows**
- use [Cygwin](https://www.cygwin.com/)
- or [WSL](https://msdn.microsoft.com/commandline/wsl/about)
- should also work with mingw compilation
- In case of using the Powershell terminal, you will need to activate the ansi color escape with this command:
  - `Set-ItemProperty HKCU:\Console VirtualTerminalLevel -Type DWORD 1`
  - [more discussion on this topic](https://stackoverflow.com/questions/51680709/colored-text-output-in-powershell-console-using-ansi-vt100-codes)
- I have not tested with Visual Studio. Should work but may need some modifications or project setup.

**Mac**
- untested, should work mostly fine, may need homebrew for boost libraries.

---

### 2. Support

- For improvements and continuation of this project. I'll strive to keep the logic sound, and the program stable and useful.
- [![donate/PayPal](https://img.shields.io/badge/Donate-PayPal-green.svg)](https://www.paypal.me/mattearly) Any donations will go towards finding (funding?) time to continue work on this project. 
  - Total donations so far: $0
 
---

### 3. Credits

- Designed for Dungeons & Dragons 5th Edition Official. The core D&D data used in this program is from:

 | [Player's Handbook](http://dnd.wizards.com/products/tabletop-games/rpg-products/rpg_playershandbook) | [Dungeon Master's Guide](http://dnd.wizards.com/products/tabletop-games/rpg-products/dungeon-masters-guide) | [Sword Coast Adventurer's Guide](http://dnd.wizards.com/products/tabletop-games/rpg-products/sc-adventurers-guide) | [Volo's guide to monsters](http://dnd.wizards.com/products/tabletop-games/rpg-products/volos-guide-to-monsters) |
 | --- | --- | --- | --- |
 | [![phb](img/DnD_PHB.png)](http://dnd.wizards.com/products/tabletop-games/rpg-products/rpg_playershandbook) | [![dmg](img/DnD_DMG.png)](http://dnd.wizards.com/products/tabletop-games/rpg-products/dungeon-masters-guide) | [![scag](img/DnD_SCAG.png)](http://dnd.wizards.com/products/tabletop-games/rpg-products/sc-adventurers-guide) | [![vgtm](img/DnD_VGTM.png)](http://dnd.wizards.com/products/tabletop-games/rpg-products/volos-guide-to-monsters) |

- Programmers as accredited in the commit history - mostly me but its always nice to have help and I will accept some modifications on a case by case basis if they align with the overall goal of dmpower. That brings us to our next topic...

### 4. Contributing, what you need to know

 - When adding new variables to [characters.h](src/characters.h):
    - The dumpCharacter & retrieveCharacter functions in [campaign.cpp](src/campaign.cpp) must be updated.
      - These functions run in a very specific sequential order, which is the same order they are in the character header file.
      - All older saves will no longer work after these functions are updated, and the notes on the release update **must** reflect this. Use an older version of the program to open your older files. (I plan to make some sort of fail safe in the future so people cannot try to load bad saves, like a version tag at the top of the save.)
    - The print* functions in [character_print.cpp](src/character_print.cpp) must be updated.
- Feel free to add yourself to the [contributors file](CONTRIBUTORS.md) along with notes about what you did to halp out.


### 5. Additional Notes

- dmpower uses terminal text coloring that will probably look best in a terminal with a dark background.
- This tool is best suited for Dungeon Masters, however the character creator could be helpful for anyone.
- No known crash cases. All crash case reports are taken as highly critical and will be fixed asap.
- This toolkit does not teach the game or say many specifics about what each ability, magic item, or spell does, as that is just not the intention. These details can be found on the plethora of reference data sites and apps related to D&D 5e, as well as in the official books. I recommend purchasing official [WotC books](#3-credits).
- Use [doxygen](http://www.doxygen.nl/manual/docblocks.html) to make the documentation from the code, all new code should have doxygen comments, old code will be updated slowly (or so we can all hope).
