# LuAnimator
LuAnimator is a tech mod that allows you to use custom character animations. Any images under a set size limit will work, and will be multiplayer-compatible. Animations are made through an application, which is also included in this repository.

## Table of Contents
- [Installation](#installation)
- [Features](#features)
- [Usage](#usage)
 - [Using the Application](#using-the-application)
 - [Using the Tech](#using-the-tech)
- [Using a different tech](#using-a-different-tech)
- [Planned](#planned)
- [Potential Issues](#potential-issues)
- [Contributing](#contributing)

## Installation
* [Download](https://github.com/Silverfeelin/LuAnimator/releases) the mod release for the current version of Starbound.
* Place the LuAnimator folder in your mods folder (eg. `D:\Steam\steamapps\common\Starbound\mods\`).
 * Remove the existing folder beforehand if it already exists. It is recommended to save a copy of the `luanimation.lua` file before you do so.
* Activate the `dash` tech on your character.
 * In singleplayer, use `/enabletech dash` and `/spawnitem techconsole` with your cursor pointed near your character. Place the tech console down and activate the tech from the tech console.
* Bind `LuAnimator Sit` and `LuAnimator Animate` in the controls menu.
 * The actual binds used are `PlayerTechAction2` and `PlayerTechAction3`. Other mods that use these binds may cause conflicts.
* [Download](https://github.com/Silverfeelin/LuAnimator/releases) the Windows LuAnimator application.
* Unpack the downloaded application, then run it.
* Create and set up animations. For further information on using the application and the output, see [Using the Application](#using-the-application).

## Features
* Crop game assets into separate frames.
* Create custom animations from frames.
 * Animations can be set for the following actions: standing still, walking, crouching (sleep), swimming, jumping and falling.
* Toggle custom animations on and off in-game using a tech.
* Sit on players and other entities, following them around automatically.

## Usage
* [Using the Application](#using-the-application)
* [Using the Tech](#using-the-tech)

### Using the Application
The application is built for [.NET Framework 4.5](https://www.microsoft.com/en-us/download/details.aspx?id=30653). Older versions of the .NET Framework may work, but this has not been confirmed.

![Overview](https://raw.githubusercontent.com/Silverfeelin/LuAnimator/master/readme/overview.png "Application Overview")

#### Cropping Assets
The frames for a lot of animated game assets are found in single image files. You can split these assets into frames easily in the application.
* Define the pixel width and height for each *frame*.
 * You can determine these dimensions by opening the image in an image editor such as [Paint.NET](http://www.getpaint.net/index.html).
* Select the image to crop. The file itself will not be modified.
* Select a location and base file name for the cropped frames.
 * A 3-digit number will be added to the end of the selected file name. The name `frame` will create files such as `frame001.png`.

![Cropped Frames](https://raw.githubusercontent.com/Silverfeelin/LuAnimator/master/readme/frames.png "Cropped Frames")  
*Asset cropped into separate frames*

#### Setting up Animations
* Select the animation state to set up animations for this state.
* Drag image files into the list box to add them to the selected animation state.
 * Every subsequent image added should have the same dimensions as the first frame added.
* Reorder frames by selecting them and using the arrow keys up and down, or automatically order them by pressing `Order`.
* Set the animation speed by adjusting the interval.
 * The given interval is in game ticks; each game tick is 1/60th of a second.
 * As a safety measure (specifically, to decrease the load on servers), the interval has to be at least 5 game ticks.
* Set whether the animation should loop or play once. Disabling looping is recommended for animations such as jumping and falling.
* Generate Code.
* Select a location to save the animation canvas to.
* Copy the generated code into the `/scripts/luanimation.lua` file of the mod. Make sure you replace the existing contents of the file entirely.

![Adding Frames](https://raw.githubusercontent.com/Silverfeelin/LuAnimator/master/readme/drag.png "Adding Frames")  
*Adding frames to the selected animation state*

![Output](https://raw.githubusercontent.com/Silverfeelin/LuAnimator/master/readme/output.png "Output")  
*Sample output*

### Setting up the Animation Canvas
When creating output, you will be asked to save an image. To enable animations, this image must be converted to drawables and be held by your character.

Recommended steps:
* Run the [Drawables Generator](https://github.com/Silverfeelin/Drawables-Generator).
* Select one of the frames, and position it.
* Note down the position values.
* Select the generated *invisible* canvas.
* Use the noted down position values.
* Generate an item (spawn command or export).
* Spawn the item using the command in-game, or import the item file.
* Hold the item in-game.

### Using the Tech
* Press the `H` key while holding your animation canvas to toggle your animations on or off.
* Press the `G` key to toggle sitting on entities on or off. When enabled, you will sit on the entity nearest to your cursor.
 * You can use your movement keys to adjust your position while sitting.

## Using a different tech
* Remove the tech script from the mod, located in (a subfolder of) the `tech` folder.
* Copy a different tech script from unpacked assets for the current version of the game.
* Place the copied tech script in the mod. Make sure the file name and directories match up with those of the game assets (eg. `\assets\tech\jump\multijump.lua` to `\LuAnimator\tech\jump\multijump.lua`).
* Open the new tech script in a text editor of your choice.
* Start a new line following the line `function init()`, and place the code below on this new line.
```lua
require "/scripts/luanimator.lua"
```
* Save the file.
* (Optional) Enable the new tech using `/enabletech <techname>` in singleplayer. Activate the tech through a tech console, obtainable by using the command `/spawnitem techconsole`.

## Planned
No additional features planned yet. Feel free to suggest them [on the discussion page]!

## Potential Issues
* Any other calls to the `tech.setParentDirectives(directives)` will overwrite the changes made by the LuAnimator tech. This can be worked around by removing the function calls that aren't found inside `/scripts/luanimator.lua`, but this may not be what you want.
* Using a low interval and high frame dimensions can easily cause performance issues for you, other players or the server you're playing on.
 * To avoid Chucklefish patching the LuAnimator out, please try to keep frames as small as they need to be. If players around you are experiencing performance issues because of the animations, please stop using the LuAnimator around them or switch to smaller animations or longer intervals.

## Contributing
If you have any suggestions or feedback that might help improve this mod, please do post them [on the discussion page]!
You can also create pull requests and contribute directly to the mod!
