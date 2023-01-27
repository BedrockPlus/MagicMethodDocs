# Magic Method Documentation

> **Warning**
> We don't recommend you learning magic method if you don't have a basic understanding of Minecraft texture pack coding and how to edit entity files.

## 🔮 What is Magic Method?
Magic Method is a method created by Chainsketch that allows you to exchange data in entity files in the game. This is also known as temp leaking. This allows you to make many mods, as magic method allows you to transfer data between other players, mobs, and particles.

> **Note**
> We want to credit Chainsketch in everyway possible, so please check out his [YouTube](https://www.youtube.com/@Chainsketch), [Discord](https://dsc.gg/chainsketch), and [Twitter](https://twitter.com/Chainsketch_)!

## Pros/Cons of Magic Method
✅ Pros:
 - You can access data from almost anywhere.
 - It is relatively easy to setup once you know what you are doing.
 - It is compatible with any texture pack so you can add it.
 - It isn't experimental like public variables.
 
❌ Cons:
 - Most servers have anticheats built in to stop you from accesing others data.
 - It is difficult to learn.
 - It will spontaneously break without much warning.

## 🤔 To understand Magic Method....
To understand Magic Method you have to know about the different storage types. Most often you will see ```variable``` being used but other things like ```temp``` and ```context``` exist. For magic method you need to use ```temp```, as it directly writes to the game's storage.

| Name | Description |
| --- | --- |
| `variable.variable_name` | Read/write storage on an actor |
| `temp.variable_name` | Read/write temporary storage |
| `context.variable_name` | Read-only storage provided by the game in certain scenarios |


Go to your ```whatever.entity.json``` file in your workspace, if you don't already have one extract it from the base vanilla resource pack [here](https://aka.ms/resourcepacktemplate). It is in the folder entity, and will need to put in another folder with the name of entity.

Inside the file you will want to look for ```pre_animation```

````JSON
"pre_animation": [
    "temp.my_first_mm_test = temp.my_first_mm_test ?? -1",
]
````

This is very important when using Temp leaking / Magic Method when the temp has no value in game storage it will set it as -1 this (if you dont do this you wont be able to test for temps in most places sense molang will just treat it as an error)

## 💧 Render Controller Leaks
In the render controller folder, there are many different render controllers. You can go into the folder and find a file that is linked to the player entity. Inside different attributes like the textures or overlay colors you can actually set up variables. Here is an example:

````JSON
"controller.render.player.third_person": {
    "geometry": "Geometry.default",
    "materials": [
        {
            "*": "Material.default"
        }
    ],
    "textures": [
        "temp.my_first_mm_test = query.distance_from_camera; return Texture.default;"
    ],
````

> **Warning**
> Make sure you use proper syntax. Every line must end with a ```;```. If you are using this in the textures area, you must add ```return Texture.[whatevertexture];```.

Now once you assign this to value, you can use ```temp.my_first_mm_test``` as any other variable, and render things on your screen.

## 🌍 Example Pack
If you don't understand packs or can't understand this guide we have an example pack. This pack tells you the distance from the closest player with an iron sword. Please don't use this on Hive's Murder Mystery as this would technically be a hack.

[Download Here](https://github.com/BedrockPlus/MagicMethodDocs/blob/main/MagicMethodPack.zip?raw=true)
<iframe width="560" height="315" src="https://www.youtube.com/embed/QWpM0n392gg" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>

## ✨ Particle Leaking
This is similar to render controller leaking but this is more recommended and you can more accurately choose who you want to get data from. More coming soon....

### Block Detection
If you want to be able to detect blocks around an entity with magic method you can use particles.
````json
"minecraft:particle_expire_if_in_blocks" [
    // minecraft block names, e.g. 'minecraft:water', 'minecraft:air'
    // these are typically the same name as in the /setblock command
    // except for the minecraft: prefix
    "blockname1",
    "blockname2", 
    ...
],
````
Now that you have set this code up, you need to tell the particle what to do if it expires. So, you will need to write this.
```json
"minecraft:emitter_lifetime_events": {
      "expiration_event": "stop"
}
````
This is the code that writes the value to the temp. So if it detects the block, it runs something that changes the temp value.
```json
"stop":{
  "expression": "temp.yourtemp = 1;"
}
````

### 🌍 Example Pack Coming Soon!

## 📜 Special Credits
Documentation made by [White](https://github.com/WhiteOnGitHub) and [chyves](https://github.com/notchyves)!
Edited by [xStormy](https://github.com/xstormyy)


### You can use the example pack, but do not steal contents and claim it as yours. Also feel free to use this documentation however you like, but just do not claim it.
