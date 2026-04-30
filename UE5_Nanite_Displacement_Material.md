Enable **Nanite Displacement** to create realistic raised geometry on flat materials.  
I am currently working in **Unreal Engine 5.7.4**
## Step 1:As shown in the picture, I have already applied the sand and stone material to the ground surface.  
<img width="2559" height="1539" alt="image" src="https://github.com/user-attachments/assets/0be94523-a1db-4eb9-bd73-71e8382c5d22" /> 
Currently, the ground material appears flat. We will use **Nanite Displacement** to make it more three-dimensional and realistic. 

## Step 2:Right-click the project and select **Show in Explorer**  
<img width="311" height="249" alt="image" src="https://github.com/user-attachments/assets/0da9fcf9-abeb-4f6a-ac6a-df676977266d" />

## Step 3:Open the **Config folder**.  
<img width="678" height="339" alt="image" src="https://github.com/user-attachments/assets/1517c832-0d57-4dd7-94ff-af126f60fd0a" />

## Step 4:Open the **DefaultEngine.ini** file.  
<img width="1062" height="351" alt="image" src="https://github.com/user-attachments/assets/4901d8ff-6b84-4257-af89-9200c5918e9c" />
<img width="2547" height="1476" alt="image" src="https://github.com/user-attachments/assets/f4056465-efa5-4853-bd52-2a54c22608c6" />

## Step 5:Add the following two console variables to the `DefaultEngine.ini` file:
```ini
r.Nanite.AllowTessellation=1
r.Nanite.Tessellation=1
```
<img width="1260" height="651" alt="image" src="https://github.com/user-attachments/assets/5203bd7f-daa9-40a8-bd79-257236d01b90" />  

<img width="1263" height="717" alt="image" src="https://github.com/user-attachments/assets/de2ec3e2-3cae-4b1a-8d6d-78502368ba0c" />

## Step 6:Save the edited DefaultEngine.ini file.  
- If you are using Notepad, click the Save button in the top-left menu.  
- Alternatively, you can use the shortcut Ctrl + S to save quickly.

### Why we modify `DefaultEngine.ini` instead of enabling it inside Unreal Editor:

The **Nanite Tessellation/Displacement** feature is still considered an experimental, developer-only setting in many versions of Unreal Engine.
It is **not exposed in the regular editor UI**, so there is no checkbox or toggle to turn it on directly in the Material Editor or Project Settings.

To unlock this hidden functionality, we need to manually add the following console variables to the `DefaultEngine.ini` configuration file:
```ini
r.Nanite.AllowTessellation=1
r.Nanite.Tessellation=1
```
## Step 7: Restart Unreal Engine for the modified settings to take effect.  

## Step 8: Assign the Material to the Landscape
With the **Landscape Actor** selected, go to the **Details panel** and find the **Landscape Material** slot.
<img width="1173" height="1338" alt="image" src="https://github.com/user-attachments/assets/a7ca3564-1ec7-4ea6-8739-04dfa8d2f1c4" />

## Step 9: Open the Material and Locate the Parent Option
Double-click the landscape material to open it in the Material Editor, then find the **Parent** option in the editor.
<img width="1550" height="1122" alt="image" src="https://github.com/user-attachments/assets/4e3f4f3d-6793-4211-ba0a-9efc2531a628" />
After opening it, you can see that the **Displacement** node is still grayed out and unavailable.
<img width="1551" height="1122" alt="image" src="https://github.com/user-attachments/assets/b913ffe8-725a-4f61-8a36-770016beed80" />

## Step 10:Enable Tessellation
Select the **Material Attributes** option.
<img width="1551" height="1122" alt="image" src="https://github.com/user-attachments/assets/e7f3781a-f6bf-4f13-aaed-1026d660552a" />  

Then scroll down in the left **Details panel** to find the **Nanite** category. Expand it and locate the **Enable Tessellation** option.
<img width="1284" height="1470" alt="image" src="https://github.com/user-attachments/assets/3e109040-d41f-478d-8787-bd45d8f8a8fa" />  

Then just click it.
<img width="473" height="174" alt="image" src="https://github.com/user-attachments/assets/7066bbc9-7feb-4e0e-8a66-8124df222a2a" />  

After enabling this option, we can see that **Displacement** becomes functional normally.
<img width="960" height="987" alt="image" src="https://github.com/user-attachments/assets/46b5743d-375f-43cc-bb05-ad1be1751caa" />

### Explanation
**Enable Tessellation** means to turn on dynamic surface subdivision for Nanite. It generates extra real geometry polygons on the mesh in real time.

Without this option, the mesh face count stays fixed, so the displacement node stays grayed out and cannot work. The surface only shows fake flat bump visuals.

After enabling **Enable Tessellation**, the material gains permission to use displacement. Height maps can now change the actual geometric shape of the landscape, creating real three‑dimensional undulations instead of flat texture illusions.

This material setting matches the engine configuration we added in `DefaultEngine.ini`, working together to fully activate the Nanite displacement function.

**Enable Tessellation（启用曲面细分）** 的作用是开启 Nanite 的动态表面细分功能，引擎会实时在模型上生成更多真实的几何面片。

如果不开启这项设置，模型的面数会保持固定，置换节点就会一直灰色无法使用，地形只能依靠贴图做出虚假的平面凹凸视觉效果。

开启 **Enable Tessellation** 之后，材质才会获得置换功能的使用权限，高度贴图能够真正改变地形的几何形状，呈现出真实的三维起伏，不再是平面的视觉假象。

该材质设置需要配合我们之前在 `DefaultEngine.ini` 中添加的引擎配置，两者结合才能完整开启 Nanite 置换功能。  

## Step 11:Apply
Click the **Apply** button in the upper left corner to apply all the modified material settings.
<img width="615" height="237" alt="image" src="https://github.com/user-attachments/assets/bc188e76-ea9f-4094-adcd-96579aa4ea31" />  

## Step 12:Enable the Nanite function
Go back to the **Landscape** actor, find the **Nanite** section in the **Details panel**, then enable the Nanite function.
<img width="729" height="1254" alt="image" src="https://github.com/user-attachments/assets/019b95a4-522e-487b-a29a-3b76f498cfe9" />

## Step 13:Build Data
Click **Build Data** to rebuild the landscape data.
<img width="870" height="477" alt="image" src="https://github.com/user-attachments/assets/1c71d32c-8789-4fd1-addc-f80c31f77242" />
<img width="2559" height="1539" alt="image" src="https://github.com/user-attachments/assets/02291ff6-c11b-4dc2-b8d0-067a50b81a40" />
The picture below shows the final result after completing Build Data.  
<img width="2538" height="1515" alt="image" src="https://github.com/user-attachments/assets/b7704be1-3c64-4d4e-80a4-374f5111dcfd" />  

## Step 14:Decrease the Displacement Amount
Decrease the **Displacement Amount** value to adjust the strength of the terrain displacement effect.  
Double-click to open the **Landscape Material**
<img width="732" height="390" alt="image" src="https://github.com/user-attachments/assets/e53b1243-581f-4e2e-a84d-3f5c051a3b82" />  

Find **Material Property Override**
<img width="1749" height="1179" alt="image" src="https://github.com/user-attachments/assets/2a19ebbb-2904-41c1-adb3-676f036642c7" />  

Then activate **Displacement Scaling** option
![Uploading image.png…]()





















