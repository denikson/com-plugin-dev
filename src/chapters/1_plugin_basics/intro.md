# Preface

The most basic parts of modding COM's code is executing custom code inside the
game. 
The ability to run any logic directly in game opens a glut of possibilities to
manipulate or add behavior to the game.

Over time there have been various means of injecting custom user code into the 
game. The currently suggested way to do so is by writing plugins using 
[BepInEx](https://github.com/BepInEx/BepInEx) — a generic cross-platform 
Unity modding framework.

> For the interested, I suggest taking a look at
> [Unity code modding history](/appendix/history.md) for information about 
> other modding tools.

In this chapter, you will

* install [BepInEx](https://github.com/BepInEx/BepInEx) and [Visual Studio](https://visualstudio.microsoft.com/);
* create and set up a BepInEx plugin project for COM3D2;
* Write a simple plugin which writes logs, uses configuration files and changes
    game's behavior by calling some of the game's own code; and
* learn about good practices related to packaging plugins for release.

