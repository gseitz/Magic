[![Build Status](https://secure.travis-ci.org/MedeaMelana/Magic.png?branch=master)](https://travis-ci.org/MedeaMelana/Magic)

# Magic: The Gathering in Haskell

A Haskell implementation of the rules of Wizards of the Coast's Magic: The
Gathering.

This project has multiple goals:

* to succinctly and correctly model the interactions between Magic cards;
* to provide an elegant and correct API to express Magic cards in;
* to provide a web server that is able to run a full game where clients play against each other.

## Scope

Magic is a big game. This implementation targets only a specific part of it.
For now, only two-player games and only cards, rules, card types and abilities
available and relevant in the Magic 2013 core set are targeted.

A good indication of the current progress is to open [module M13](/Magic-Cards/src/Magic/M13.hs) and see how many M13 cards have been implemented yet. A list of issues to be fixed before the whole of M13 can be implemented can be [found on GitHub](https://github.com/MedeaMelana/Magic/issues/milestones).

There is also a command-line interface that allows you to play the game. To run it, follow the installation instructions below and run the executable that it produced by building `Magic-Cards`. This will run a two-player game with preselected decks.

## Building

You need [GHC 7.8](http://www.haskell.org/ghc/download_ghc_7_8_2) or greater and [cabal-install 1.20](http://www.haskell.org/cabal/download.html) or greater to build Magic.

Clone the repository and create Cabal sandboxes for the projects in dependency order:

```
$ git clone git@github.com:MedeaMelana/Magic.git
$ cd REPO/Magic
$ cabal sandbox init
$ cabal install --dependencies-only
$ cabal build
$ cd REPO/Magic-Cards
$ cabal sandbox init
$ cabal sandbox add-source ../Magic
$ cabal install --dependencies-only
$ cabal build
```

If you want to run the web server:

```
$ cd REPO/Magic-Web-Server
$ cabal sandbox init
$ cabal sandbox add-source ../Magic
$ cabal sandbox add-source ../Magic-Cards
$ cabal install --dependencies-only
$ cabal build
$ dist/build/magic-cli/magic-cli
```

If you want to run the command-line interface:

```
$ cd REPO/Magic-CLI
$ cabal sandbox init
$ cabal sandbox add-source ../Magic
$ cabal sandbox add-source ../Magic-Cards
$ cabal install --dependencies-only
$ cabal build
```
