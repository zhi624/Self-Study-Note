Enable **Nanite Displacement** to create realistic raised geometry on flat materials.  
I am currently working in **Unreal Engine 5.7.4。**
As shown in the picture, I have already applied the sand and stone material to the ground surface.  
<img width="2559" height="1539" alt="image" src="https://github.com/user-attachments/assets/0be94523-a1db-4eb9-bd73-71e8382c5d22" /> 
Currently, the ground material appears flat. We will use **Nanite Displacement** to make it more three-dimensional and realistic. 

Next, right-click the project and select **Show in Explorer**  
<img width="311" height="249" alt="image" src="https://github.com/user-attachments/assets/0da9fcf9-abeb-4f6a-ac6a-df676977266d" />

Then, open the **Config folder**.  
<img width="678" height="339" alt="image" src="https://github.com/user-attachments/assets/1517c832-0d57-4dd7-94ff-af126f60fd0a" />

Then, open the **DefaultEngine.ini** file.  
<img width="1062" height="351" alt="image" src="https://github.com/user-attachments/assets/4901d8ff-6b84-4257-af89-9200c5918e9c" />
<img width="2547" height="1476" alt="image" src="https://github.com/user-attachments/assets/f4056465-efa5-4853-bd52-2a54c22608c6" />

Add the following two console variables to the `DefaultEngine.ini` file:
```ini
r.Nanite.AllowTessellation=1
r.Nanite.Tessellation=1
```
<img width="1260" height="651" alt="image" src="https://github.com/user-attachments/assets/5203bd7f-daa9-40a8-bd79-257236d01b90" />  

<img width="1263" height="717" alt="image" src="https://github.com/user-attachments/assets/de2ec3e2-3cae-4b1a-8d6d-78502368ba0c" />

Save the edited DefaultEngine.ini file.  
- If you are using Notepad, click the Save button in the top-left menu.  
- Alternatively, you can use the shortcut Ctrl + S to save quickly.

### Why we modify `DefaultEngine.ini` instead of enabling it inside Unreal Editor:

The **Nanite Tessellation/Displacement** feature is still considered an experimental, developer-only setting in many versions of Unreal Engine.
It is **not exposed in the regular editor UI**, so there is no checkbox or toggle to turn it on directly in the Material Editor or Project Settings.

To unlock this hidden functionality, we need to manually add the following console variables to the `DefaultEngine.ini` configuration file:
```ini
r.Nanite.AllowTessellation=1
r.Nanite.Tessellation=1



