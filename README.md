# LuAnimator
LuAnimator is a tech mod that allows you to use custom character animations. Any images under a set size limit will work, and will be multiplayer-compatible. Animations are made through an application, which is also included in this repository.

## Table of Contents
- [Features](#features)
- [Wiki](#wiki)
- [Planned](#planned)
- [Potential Issues](#potential-issues)
- [Contributing](#contributing)

## Features
* Crop game assets into separate frames.
* Create custom animations from frames.
 * Animations can be set for the following actions: standing still, walking, crouching (sleep), swimming, jumping and falling.
* Toggle custom animations on and off in-game using a tech.
* Sit on players and other entities, following them around automatically.

## Wiki
The Wiki covers about everything you need to know and do to use the LuAnimator.
https://github.com/Silverfeelin/LuAnimator/wiki

## Planned
No additional features planned yet. Feel free to suggest them [on the discussion page]!

## Potential Issues
* Any other calls to the `tech.setParentDirectives(directives)` will overwrite the changes made by the LuAnimator tech. This can be worked around by removing the function calls that aren't found inside `/scripts/luanimator.lua`, but this may not be what you want.
* Using a low interval and high frame dimensions can easily cause performance issues for you, other players or the server you're playing on.
 * To avoid Chucklefish patching the LuAnimator out, please try to keep frames as small as they need to be. If players around you are experiencing performance issues because of the animations, please stop using the LuAnimator around them or switch to smaller animations or longer intervals.

## Contributing
If you have any suggestions or feedback that might help improve this mod, please do post them [on the discussion page]!
You can also create pull requests and contribute directly to the mod!
