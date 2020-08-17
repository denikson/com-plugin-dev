# A brief history lesson on custom code execution

> Note: This section is not mandatory but might prove interesting
> in terms of Unity modding history.

When Unity modding was at its infancy, custom code execution was achieved
by permanently patching some DLL in the game's `Managed` folder. Some 
small piece of code was injected into the game which in turn allowed to load 
other user-made DLLs with the code. One example of such loaders was
[Illusion Plugin Architecture](https://github.com/Eusth/IPA) (IPA), which at the time
was heavily used to mod Illusion games. IPA had a simple monolithic
architecture in which all core components were in a single core DLL. 
Actual game code manipulation was done by patching `Assembly-CSharp.dll` — 
DLL containing game's core logic — making every single C# inheritable 
and every method [`virtual`](https://docs.microsoft.com/en-us/dotnet/csharp/language-reference/keywords/virtual).

At the time of CM3D2 release, a new tool named *ReiPatcher* was released. 
While still patching game's assemblies permanently, ReiPatcher didn't
virtualize the whole `Assembly-CSharp.dll` and instead allowed users to 
write custom patchers using [Mono.Cecil](https://github.com/jbevain/cecil) 
library which provides low-level access to .NET assembly internals. 
In addition, ReiPatcher shipped with *UnityInjector* which was a general 
purpose plugin loader for Unity games. Unlike with IPA, ReiPatcher and 
UnityInjector were highly configurable and modular in design. In addition, 
UnityInjector required plugins to save metadata (plugin name, version, etc) 
using [C# attributes](https://docs.microsoft.com/en-us/dotnet/csharp/programming-guide/concepts/attributes/).
While ReiPatcher was quickly outlived, many of its architectural choices are
still seen in many modern loaders.

A minor segway: at the time of ReiPatcher and Mono.Cecil-based patching, tool to make 
patching easier were developed. Most notably

* [MonoMod](https://github.com/MonoMod/MonoMod) — allows to write assembly
   patchers without touching any of Cecil. It is still very useful in some
   cases. In fact it's still useful in modern loaders, refer to
   [Chapter 4](../chapters/4_monomod/intro.md) for the guide.
* [dnSpy](https://github.com/0xd4d/dnSpy) — tool to view and inspect .NET
    assemblies. Allows to edit assemblies using C# directly, which lowered 
    the entry bar for modding significantly (even though it is still
    hardpatching). We will dive into dnSpy in [Chapter 2.1](../chapters/2_patching_basics/1_dnspy.md).

An important turning point for CM3D2 modding was introduction of Sybaris.  
Sybaris was a single DLL file that required only a drop-in installation into 
CM3D2 folder. In turn, Sybaris allowed to run Mono.Cecil patches **in memory**
without ever permanently modifying any game DLLs. Not only did it solve 
potential problems related to user errors, it also made uninstallation and 
game updating much easier. In addition to adding some other CM3D2-specific 
functionality, the base architecture of Sybaris was identical to ReiPatcher. 
Sybaris also used UnityInjector for actual plugin loading.

Sybaris 2 was released at the time of COM3D2 with only minor updates. Around 
the same time, Koikatsu (a game developer by Illusion) was released and 
[BepInEx](https://github.com/BepInEx/BepInEx) was developed as a successor 
to IPA. BepInEx took the best parts of IPA's installation simplicity,
ReiPatcher's attribute-based metadata and modularity. A little later, 
modders from COM3D2 and Koikatsu community came together, giving birth to
[UnityDoorstop](https://github.com/NeighTools/UnityDoorstop) (formerly also 
known as UnityPrePatcher). UnityDoorstop allowed to inject any C# code into
any Unity game right before Unity runs any of its code. This allowed to 
implement all of Sybaris 2 features directly into BepInEx and iterate on them, 
creating truly unified Unity modding framework. 

And here we are today. BepInEx
[has vast documentation](https://bepinex.github.io/bepinex_docs/master/articles/index.html), 
contains clean logging and configuration tools and
[allows to load Sybaris patchers and UnityInjector plugins](https://bepinex.github.io/bepinex_docs/master/articles/advanced/compatibility.html)
while doing it all in memory.
BepInEx also includes a panoply of helper libraries such as

* [Harmony](https://harmony.pardeike.net/) which allows to patch game code at runtime
* [MonoMod.RuntimeDetour](https://github.com/MonoMod/MonoMod/blob/master/README-RuntimeDetour.md) which has a bunch of additional patchers and helper tools