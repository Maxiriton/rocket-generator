# rocket-generator script

![Rocket Generator](https://i.imgur.com/IZiGvZT.jpg)

A simple tool to generate vintage rockets with Blender

## General description

Rocket Generator is based on very simple principles. A rocket is composed of several parts defined by the user.
Each part has to modeled manually, the script will only takes care of randomly assembling the parts.

Here is an example  of some parts composing a rocket :

![Rocket Generator](https://i.imgur.com/nA7Qsbf.jpg)

Once each part is modeled, the script will assemble them using a naming convention and adding some randomness when needed.

- the script registers all variations of each parts that are currently in your current scene
- it starts generating rockets, begining with selecting a random root_base_var and then recursively calling the generate function for each target it finds.

## Adding a new part

When you create a new part, you can use as many objects as you want to compose it. The only condition being that all objects must be children of an empty named root_$PÄRTNAME_var.
For example, if you to create a new rocket body, all the objects composing the body must be children of an empty called **root_body_var**.

The idea is to have several variations of the body part, so the script will choose one randomly when it generates a new rockets. When you will be adding more variations, create new empties called **root_body_var_2**, **root_body_var_3** and so on...

Here is an example of a body part in the viewport. Note how all the all the objects are children of **root_body_var** empty.

![Body variation example](https://i.imgur.com/qKKGVEE.jpg)

## Adding a target to a part

The script let the user controls how each part must be assembled to form the rocket. To do so, when creating a part, the user must place empties wich will define to position, location and scale of a children part.
These empties follow an other naming convention : target_$PARTNAME.

For example, you have created a base part, from which you want to attach a body, and several feet parts. To do so, simply place a **target_body** and several **target_foot** empties on your model.

![Example of the base part](https://i.imgur.com/WfffK8P.jpg)

## Script parameters

The script has a very basic user interface.

![Imgur](https://i.imgur.com/fx2CGvw.jpg)

- **Number of rockets** : how many rockets will be generated
- **Use similar Foot parts** : when enabled, this will make sure, all foot variations are the same per rocket model, making a more consistent model
- **Use similar Body parts** : same as previsouly but for body variation
- **Allow weird shape** : Currently this an hardcoded function that allows the choose if the rocket must have a regular shape or can have a more creative shape.
