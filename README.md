# Magic Method Documentation

> **Warning**
> We don't recommend you learning magic method if you don't have a basic understanding of Minecraft texture pack coding and how to edit entity files.

## What is Magic Method?
Magic Method is a method created by [Chainsketch](https://www.youtube.com/@Chainsketch) that allows you to access anything in the game. This allows you to make many mods, as magic method can interact with other players, item data, and UI.

## Pros/Cons of Magic Method
✅ Pros:
 - You can access data from almost anywhere.
 - It is relatively easy to setup once you know what you are doing.
 - It is compatible with any texture pack so you can add it.
 - It isn't experimental like public variables.
 
❌ Cons:
 - Sometimes it breaks on specific servers.
 - It is difficult to learn.
 - It will spontaneously break without much warning.

## To understand Magic Method....
To understand Magic Method you have to know about the different storage types. Most often you will see ```variable``` being used but other things like ```temp``` and ```context``` exist. For magic method you need to use ```temp```, as it directly writes to the game's storage.


![Bedrock.dev Example](https://user-images.githubusercontent.com/82107846/213821855-62a974d6-bee3-41bd-8a47-c4ae367b0139.png)

Go to your ```player.entity.json``` file in your workspace, if you don't already have one extract it from the base vanilla resource pack [here](https://aka.ms/resourcepacktemplate). It is in the folder entity, and will need to put in another folder with the name of entity.

Inside the file you will want to look for ```pre_animation```

![Example 2](https://user-images.githubusercontent.com/82107846/213822128-1c5b781f-e7bc-4416-a8bd-d0832ba9b7ee.png)

This is one of the most important lines because it sets up magic method and allows it for use. Now in order to give it a value, you can use many methods. One of these are render controller leaks.

## Render Controller Leaks
In the render controller folder, there are many different render controllers. You can go into the folder and find a file that is linked to the player entity. Inside different attributes like the textures or overlay colors you can actually set up variables. Here is an example:

![Example 3](https://user-images.githubusercontent.com/82107846/213823129-fd5e3dcd-0ca9-49c3-aee1-099c0c89f060.png)

> **Warning**
> Make sure you use proper syntax. Every line must end with a ```;```. If you are using this in the textures area, you must add ```return Texture.[whatevertexture];```.

Now once you assign this to value, you can use ```temp.my_first_mm_test``` as any other variable, and render things on your screen.



## Special Credits
Documentation inspired by [White](https://github.com/WhiteOnGitHub), created by [chyves](https://github.com/notchyves)!
