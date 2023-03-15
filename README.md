# BlendShapeCombiner-English

This is a Unity editor extension that adds a new shape key that combines multiple blend shapes and saves it as a new mesh.

You can specify coefficients, so you can create a "make the eyes smaller" shape key from a "make the eyes bigger" shape key, for example, or normalize weights set outside the range of 0 to 100.

The development background is the issue of only being able to specify one shape key for blinking in VRChat Avatars 3.0, but it can be used for other purposes as well.

![image](https://repository-images.githubusercontent.com/285993854/facec380-fc27-11ea-9588-d9cd6b608ba7)

## Requirements

Unity 2018.4 or later

## Import procedure

### How to import unitypackage

Download the latest version of `BlendShapeCombiner-vX.X.X.unitypackage` from the [Releases page](https://github.com/chigirits/BlendShapeCombiner/releases) and import it into Unity.

### How to use package manager

1. Open `Packages/manifest.json` in a text editor for the project you want to import to.
2. Add the following element to the `dependencies` object.
   
   ```
   "com.github.chigirits.blendshapecombiner": "https://github.com/chigirits/BlendShapeCombiner.git",
   ```

## Usage

1. Place the model in the scene
2. Select "Menu/Chigiri/Create BlendShapeCombiner" and the BlendShapeCombiner will be placed at the top level of the Hierarchy.
3. Specify the SkinnedMeshRenderer to be manipulated in the `Target` of the BlendShapeCombiner. If applying to the avatar's facial expressions, generally specify the Body object.
At this time, the mesh attached to the target is automatically set to `Source Mesh`.
   
   ![usage-01](https://user-images.githubusercontent.com/61717977/93739727-edafd580-fc23-11ea-983d-fd2c7836ebad.png)
4. Enter the name of the shape key to be created in `Name` and select the source shape key from `Source [X]` to composite it.
   
   - The degree of effect can be adjusted by setting the scaling factor (the value in the text box to the right of the pull-down menu) to a value other than `1`. (See Scaling Factor below for details.)
   - To increase or decrease the number of source shape keys, press the trash can icon to the left of each `Source [X]` or the `+` button at the bottom left.
   - To increase or decrease the number of shape keys to be created, press the `+` `-` buttons at the bottom right of the `New Keys` list tab (to delete, select the target row in advance).
   
   ![usage-02](https://user-images.githubusercontent.com/61717977/93739733-f2748980-fc23-11ea-9ff2-d3abe91057e0.png)
5. Press the "Process And Save As..." button to save the newly generated mesh.
   
   ![usage-03](https://user-images.githubusercontent.com/61717977/93739737-f4d6e380-fc23-11ea-9118-d287db6226ec.png)

   When the save is complete, the new mesh will be attached to the SkinnedMeshRenderer in `Target`.
   Try changing the values of the new shape keys added to the replaced mesh to confirm that the expected effect is applied.
   
   ![usage-04](https://user-images.githubusercontent.com/61717977/93739742-f7393d80-fc23-11ea-8686-1493f870986c.png)

## About Scaling Factor

By specifying a scaling factor other than `1`, you can greatly exaggerate or reverse the effect of a shape key.

For example, by specifying `-1` for the `scale` of a shape key that reduces the size of the eyes, you can create a shape key that enlarges the eyes.

![usage-05](https://user-images.githubusercontent.com/61717977/92988185-1b9a6900-f504-11ea-84c4-aa234108caa5.png)

![usage-06](https://user-images.githubusercontent.com/61717977/92988187-1e955980-f504-11ea-8262-2dfc5dea82d2.png)

Furthermore, suppose there are only two shape keys available for a model, "A: Close eyes" and "B: Close eyes and open mouth." In that case, by overlaying the -1 scaled shape key of A onto B, you can create an expression where only the mouth is open.

## License

[MIT License](./LICENSE)

- This software is available for both commercial and non-commercial use free of charge but is not guaranteed. The author is not responsible for any issues that may arise from its use.
- When reusing the code, you must include the copyright notice and the license terms from the link above. Please read the terms (in English) for more information.

## Version History

- v1.2.0
  - UI improvements
    - Implemented custom UI
    - Maintains Source Mesh independently from Target to reduce the burden of retrying
    - Set the initial directory of the save dialog to the same as the Source Mesh
    - Added Revert Target button
    - Added tooltip display
- v1.1.0
  - Added scaling factor property
  - Supports batch addition of multiple shape keys
- v1.0.0
  - First release
