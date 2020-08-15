# Introduction

## Foreword

Greetings!

This book is a miniature introduction into modding Custom Order Maid 3D 2 -- a game by 
KISS where you play as a maid parlor owner. While the gameplay is somewhat repetitive 
and heavily story-based, it has a massive modding potential owing to the game's maid
editor and Photo Mode.  

Custom Maid 3D 2 was the first game that got me serious into Unity modding back in 2015. I was captivated
by how simple it is to view game's code and edit it to fit my own needs. One of 
my very first plugins was [Maid Fiddler](https://github.com/denikson/CM3D2.MaidFiddler) which 
was a live value editor. To make such a tool, I started from the ground up and had to learn 
how to decompile and read the game's code, get grasp of writing IL patchers to inject my 
code into the game and jump hoops around Unity's own quirks. It was a daunting task, 
yet a great introduction into more general Unity modding. Later on I went ahead to apply the 
gained knowledge to such adventures as

* writing [Mono.Cecil.Inject](https://github.com/denikson/Mono.Cecil.Inject) which makes code injection
  easier with the tools used in CM3D2 modding;
* writing [the first comprehensive guide on CM3D2 plugin development](http://umaiumeunion.github.io/guides_unityinjector/01_preface)
  and [document the three-DLL patching architecture](http://umaiumeunion.github.io/guides_reipatcher/08_guideline_php_pcp_architecture) that is still used in many COM3D2 plugins to date;
* making [UnityDoorstop](https://github.com/NeighTools/UnityDoorstop) which allows to inject custom 
  code into any Unity game;
* helping as a developer for [BepInEx](https://github.com/BepInEx) -- a general-purpose Unity modding framework;
* maintaining [BepInEx Docs](https://bepinex.github.io/bepinex_docs/master/articles/index.html) which accumulates 
  various information on developing Unity plugins.

In this book I hope to share the experience I've gained over the course of 5 years modding Unity games to bring 
a basic introductory guide into COM3D2 modding. 

Back when I started modding, documentation was scarce. I hope that this book will be of benefit to anyone who wants to write 
plugins for COM3D2 or any other Unity game.

-- Geoffrey Horsington <[neigh@coder.horse](mailto:neigh@coder.horse)>

## What you will learn in this book

The book is intended as an introductory document into plugin development of COM3D2. 
While the contents are tailored for COM3D2, you can use the same concepts to mod almost any Unity game.

> Note: This book does not cover making models, textures or any other COM3D2 modding that is not related
> to programming aspects. For more information on this, I suggest checking out [*Amateur’s Modding Guide To COM*](https://docs.google.com/document/d/1ynhUG_JwypWVQejG_p7DfHfGhAnioQKnhf21K_jMNaQ).

This book covers the following topics:

1. The core basics of writing a plugin
2. Basics of reverse engineering the game with dnSpy
3. Using runtime patching to edit game's basic behavior
4. Understanding the basics of Common Intermediate Language
5. Advanced manipulation of game behavior by editing game's code

The topics are ordered by the difficulty level. After reading the book, you will by no means be the modding master, but
you certainly will have the knowledge to create the next great thing in COM modding!

## What you should know before reading this book

All the guides contained within here were made with little required background knowledge in Unity or Unity modding.  
*Only basic understanding of programming is required for this book.*
Nevertheless, the following material will make it much easier to understand the panoply of topics covered here:

* Knowledge of programming in C#: [.NET Academy](https://dotnetcademy.net/CSharp/Beginner) is a good public source
* Understanding of Reflection API in .NET: [.NET Academy](https://dotnetcademy.net/Learn/4/Pages/1)
* Understanding of Unity: [Create with Code](https://learn.unity.com/course/create-with-code) course will give extensive knowledge; even more than needed in this guide