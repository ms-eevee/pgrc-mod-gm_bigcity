# gm_bigcity PGRC Mod

*Note: this repo does not track any map files. If you would like to make any edits, you will have to import the map yourself*

Absolutely massive shoutout to (bigwig)[https://steamcommunity.com/id/bigwig] for the most influential map of my childhood, gm_bigcity is still a banger.

## Importing a Garry's Mod map
First step is to subscribe to whatever mod map you're looking to import. Once Steam downloads the map, it will be available in ```{SteamFolder}/SteamLibrary/steamapps/common/GarrysMod/garrysmod/cache/workshop``` in .gma format. You can find the id number corresponding to the .gma you are looking for by grabbing the ID from the addons workshop page URL.

To extract the gma file, Garry's Mod ships with a tool called gmad, located at ```{SteamFolder}/SteamLibrary/steamapps/common/GarrysMod/bin/``` (This will be gmad.exe if on windows, of gmad_linux if you're on linux). Run the following:
```
./gmad_linux extract -file garrysmod/cache/workshop/105982362.gma
```
to extract the .gma into a .bsp.

From there, you'll need to install [SourceIO](https://github.com/REDxEYE/SourceIO) into blender. Once installed, you get a new option in blender under File -> Import for SourceIO, select SourceMap (.bsp).

It takes a few seconds, but blender will open up the map. Trim out any unwanted geometery, as the geometry will be used to create the collision mesh later. Once you are finished, export the map through File -> Export -> .glb format. Save the file into the map-import folder within the mod directory. 

Now the annoying part (as I haven't found a built in way to do this in Godot yet), you have to change the materials in the model to shader materials. Select the imported mesh in the node tree; in the inspector under MeshInstance3D click on the mesh to open the mesh options. For each surface in the mesh, click the dropdown and select "Change to shader material" (the last option). Then, click the material to open it's properties, and change the shader to "gm_bigcity-overlay.gdshader". The material will update with the model's texture, and the retro shader applied.


