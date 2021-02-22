> Note: This was written for Windows computers. If you have a different OS, then ask Google :D

# Exit with Exit Code 0 on Minecraft

Hello there! I enjoy playing Minecraft, I even hosted my own modded server. While playing on this server, I have found that it occasionally crashes with exit code 0. While researching the solution to this, I have found a few solutions. Some worked for me, others did not. Most people are not going to read this, but I hope it helps!

## Figuring Out the Cause

Whenever you have an issue with technology, there is a checklist that you should go through before doing anything else:

1. Restart your computer
2. Update...
Your computer / OS
Java
Minecraft launcher
Minecraft .jar file (delete and redownload)
Graphics card (if applicable)
Forge / Fabric mods (if applicable)
3. Check the logs (open up the launcher, click settings, select "Open output log when game start", then run Minecraft)

Do these on step at a time, and test to see if it worked so you know the fix if it ever happens again. When this issue happened to me, I was running Forge 1.15.2 with around 25 mods, including OptiFine. Sadly, none of this worked, but I found the following in the logs:

```
JRE version: Java(TM) SE Runtime Environment (8.0_25-b18) (build 1.8.0_25-b18)
Java VM: Java HotSpot(TM) Client VM (25.25-b02 mixed mode windows-x86 )
Problematic frame:
C  [ig4dev32.dll+0x3e88]

Failed to write core dump. Minidumps are not enabled by default on client versions of Windows

If you would like to submit a bug report, please visit:
  http://bugreport.sun.com/bugreport/crash.jsp
The crash happened outside of Java Virtual Machine in native code.
See problematic frame for where to report bug.
```

## Windows Vista and Compatibility

This is the most recent fix (as of 1.16.3). First find the actual Minecraft launcher application in the files app or on the desktop. Right click it, and select "Properties". Then, select the compatibility tab. Once there, select "Run this mode in compatibility mode for:" and "Windows Vista". Here is a [walk-through video on doing this](https://youtu.be/MC83eGWjNRA).

You can always change this back if it didn't work, as the Windows Vista version of the Launcher is not nearly as clean.

## Testing Mods Individualy (Forge / Fabric / Custom Jars)

This may take a lot of time, but it is effective. Basically you manually test Minecraft by mixing around the mods that you have enabled. Maybe remove unstable ones, or test a single one alone. Or, maybe, try running the same version, but without any of the modifications. See if it still happens on Vanilla.

This actually worked for me. I found that OptiFine was causing the issue, so I removed it. Soon I will add an updated version.

## Post 1.7 with Graphics Card

I have found in StackEdit a post asking this question, and it was from someone who just transferred from 1.7 to 1.8. Supposedly the rendering engine was changed, causing Minecraft to crash. The general response was that this change was permanent and that they should update / re-install their graphics card. I'll teach you how to do this, but it is a last resort because it can mess up your device.

I recommend following [this tutorial](https://appuals.com/minecraft-failed-core-dump/) for this, but **be warned! This may mess up your computer, and it is not reversible.**

## Some Links and Things

- [Mojang Bug](https://bugs.mojang.com/browse/MC-200062)
- [Another Fix for Forge](https://forums.minecraftforge.net/topic/93087-minecraft-1163-starts-up-but-crashes-with-exit-code-0/)
- [Another Thing](https://www.errorvault.com/en/troubleshooting/runtime-errors/mojang/minecraft/error-0_minecraft-error-0)

## Closing

I hope you found this guide interesting!
Later,

~BD103