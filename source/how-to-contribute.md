# Any Help Is Welcome

**Art Of Sequence** (or **AOS**) is a volunteer driven project, powered only by love of art, authors and the will to help them.
Still, it's a very big project, made of several sub-projects that are different tools working together. It's designed to be open. The purpose is to provide a base on which companies and authors could build their own tools. It requires a very wide variety of skills, knowledge and a lot of time to develop.

**Any help is welcome.** Below we describe how you can help on the technical side. If you're an author but don't have technical skills, you can still help by providing feedback and suggestions (see http://artofsequence.org ).

**For developers**, [instructions to setup the developpement environnement are available there](development-setup.md). A [coding convention is also available](coding-standard.md) : we'll accept only code following this convention. It's a constant work-in-progress so feel free to ask details or propose enhancements to it.

If you want to participate on the technical side of the project, here is a list of war fronts to fight on.

## Issues

You should first look at the issues lists for each sub-project:
 - [AOSL](https://github.com/artofsequence/aosl/issues)
 - [AOS Designer](https://github.com/artofsequence/aos-designer/issues)
 - [AOS Web Player](https://github.com/artofsequence/aos-webplayer/issues) - take a look at [the demo](http://demo.artofsequence.org)
 

If the issues are bugs or not-working-as-it-should features, feel free to fix them and create pull-requests. (If you're not familiar with Git, our source-control tool, here is a good starting point : http://git-scm.com/book )

**However if the issues imply design decisions, please first discuss the issue** in the comments or in the related discussion on [the forum if necessary](http://forum.artofsequence.org).


## Build System Improvements

AOS provide tools and players implementations that are meant to work at least on Windows, MacOSX and Linux (at least Ubuntu & Fedora).
To achieve this goal for C++ code, **we use [CMake](http://www.cmake.org/)** as meta-build system to generate the project files necessary for each platform and tools sets.

However, we don't have CMake specialists in the team at the moment (core team size = 1...) and the current CMake files might be very naive implementations.

Any help to enhance CMake files documentation and implementation (flexibility, correctness) are very welcome!

## Cross-Platform Support

**The tools provided by A.O.S. are meant to work on Windows, MacOS and Linux (at least Ubuntu and Fedora).**

At the moment, while keeping this objective in mind, we develop and check the application mainly on Windows. 
Deep checks of correct behavior of the tools on those platforms are welcome.

Also, the players implementations are meant to be working on more different platforms, specific to the player application nature. Deep checks of provided players implementations behavior on those platforms are welcome too!

## AOSL

**AOSL is the format that makes the tools and players work together.** It's xml-based and totally defined and documented in [an xsd file](http://artofsequence.org/aosl/) at the moment.

As it's a format specification, originally written by one person only, it needs a lot of reviews and enhancement for the future versions:

### Design

You can discuss AOSL's design [on the dedicated forum](http://forum.artofsequence.org/category/aosl) or [enter issues](https://github.com/artofsequence/aosl) for design bugs.

Enhancement, fixes and new features propositions are obviously welcome and encouraged. Just provide changesets to check in with a full explanation of your proposition for review.

### Documentation

At the moment, AOSL is really poorly documented. If you start to grasp the point of AOSL, you're encouraged to help on it's documentation, either in the xsd definition documentation tags or by providing tutorials and articles for example.


## AOS Designer

**AOS Designer is the main visual edition tool of the project.** We need to add helpful and powerful features to let the author be free to story-board and mount their sequences as they wish and with almost not limits.

**Skills wanted** :
 * Programming : C++, Boost, Qt
 * UI and usability designs
 * Graphism : icons and other graphic stuffs

### User Experience

The project being in it's infancy, the current objective is to make it *just work*.

Having said that, it's still a visual montage tool that needs to be really simple and clear to use. We try to implement the UI in a useful way as much as possible while we implement the basic features of this tool. 

We need to have some resources focused purely on usability. 

You can suggest improvements on the forum or even implement some and propose them to be pulled in the codebase, with a provided rational for the feature.

One thing that might help a lot would be to add usage statistics to the code, to make the tool send use data about how the users behave. That would complete observation of real-world usage that I'm doing with some people around me.


### Documentation

AOS Designer really need tutorials and extensive documentation.

A wiki might be a good solution for such documentation (TODO?).

Another type of documentation is everything that is inside the tool itself. For example, tooltips and contextual information pages might help the users to figure what they should or can do at any moment.

Tutorials could be implemented in two ways : 

 * Tutorial sequences : sequences explaining how to use the tool and providing their own sources/project files, to help the user understand how to do something. I think it should be the preferred form because it would help "eating our own dog food" and it's a perfect case of explanation by desmonstration.
 * Textual tutorials : classic tutorial texts.

### Unit Tests

Even in AOSLCPP, there is no unit tests at the moment.
Any help on this front would be awesome.


## Exporters

Exporters are tools that convert a sequence definition (an AOSL file) and it's resources (images, sounds, etc.) into another specific form.

The main exporter that will be provided with the tool will be an HTML/CSS/Javascript exporter, generating a folder with an html page, some Javscript and CSS files and a resources directory. This exporter is meant to be the simplest and provide a simple way to put the artist's sequences online, available on any platform with a decent browser.

However, this will not be enough. One of the purposes of AOS is to allow defining a Sequence, maybe making some variants, and exporting to several different targets.

There are two kind of targets : 

 * Players : see the next section. Some exporters will just allow players to read specific optimized formats.
 * Final form : the web exporter exports the sequence in it's final form, the javascript interepreter will do the work of the player. We could also implement an executable from the Sequence description, for any platform.


## Players

**Players are interprets of sequences**. There are two kind of players :

 * Players reading AOSL files (and resources) : those are the most flexible players. However they might suffer from performance problems on some platforms like embedded hardware (smartphones for example).
 * Players reading specific format : mostly for performance reasons, a binary format for some players might be necessary.

For binary formats, there is no official AOSL binary at the moment because it's meant to be extended: players can implement additional features to the language. When such a player-specific extension is used in a Sequence that is played in a player that don't know this extension, it's just ignored, like with HTML tags. 

Ideas of players that might be interesting to provide :

 - Flash player (implemented in AS3)
 - Android player
 - iOS player

Some of these players are planned as commercial products by Joel Lamotte.

### Web Player

The web player is essentially a Javascript AOSL interpreter that allows to play a Sequence in a web page. It's meant to be the default exporter of AOS Designer and will be the demonstration tool of the project.

You can see an work-in-progress example there: http://demo.artofsequence.org
