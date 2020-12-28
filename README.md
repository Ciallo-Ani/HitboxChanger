# HitboxChanger
Sourcemod extension to provide the ability to edit the hitbox of a model from memory to a sourcemod plugin. It is necesary to use the custom hl2sdk-csgo as it has been extensively modeified to allow for this to work.

# Capabilities
This extension provides natives with the ability to modify the hitboxes of a model without recompilation.
- You can modify the hitboxes:
  - Bone
  - Group
  - Min Point
  - Max Point
  - Angle
  - Radius
  - And you can also get all of this info from a hitbox
- Change the number of hitboxes in the hitboxset.
  - You can *not* change this beyond the amount of hitboxes the model originally had, however you can make it less than or even negative values.
  - Use `GetNumHitboxes` first so you can get the max number you can set without crashing.
- Print debug info about a models hitboxes to server console
- Print debug info about a models bones to server console
- Print a list of valid bones/bone names for use as a hitbox bone
- Get a bones index by its name

# Natives
- `HitboxInfo`      Print all the hitboxes to server console
- `BoneInfo`        Print all the bones to server console
- `SetHitbox`       Set the properties at a hitbox index
- `GetHitbox`       Get the properties at a hitbox index
- `SetNumHitboxes`  Set the number of hitboxes for a model
- `GetNumHitboxes`  Get the number of hitboxes for a model
- `FindBone`        Find a bone's index in a model by name
- `FindValidBones`  Print a list of the bones in a model which can have a hitbox attached

# Hitbox Enum Struct
There is also a sourcepawn enum struct included in the native, to provide an easy method of hitbox reuse. Includes methods to copy the attributes to and from a model by using the structs data, as well as to print the data stored in the struct to server console.

# Building
- Place the hitbox_changer directory in your sourcemod 1.10 public directory.
- hitboxchanger-hl2sdk-csgo should be adjacent to your sourcemod directory, as should metamod 1.10.
- Run configure.py from sourcemod/public/hitbox_changer/build. Use `CC=clang CXX=clang++ python3 ../configure.py` on linux
- Run ambuild from build dir
- Profit???

# Notes
- The source code can be found in /sourcemod/public/hitbox_changer. 
- *You must build against the included modified hl2sdk-csgo for this to work.* 
- A hitboxes bone must have the `BONE_USED_BY_HITBOX` flag set, I am currently unable to set this, so it is error checked and setting to an invalid bone will fail.
- It should not take too much work to modify the extension for use in another source game, mainly removal of capsule code, but I currently have no means of testing for another game and no incentive, so feel free to release a modified version for other games. 
- It should not take too much work to modify the extension for use in another source game, mainly removal of capsule code, but I currently have no means of testing for another game and no incentive, so feel free to release a modified version for other games :). 
- I do not have a windows server to test this on but I can see no reason it will not work there.
