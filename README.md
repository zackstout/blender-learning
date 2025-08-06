# Blender

- Wow most of this playlist was just a year ago.
- We live in amazing times.

---

## 1: Part 1

- Press "G" to end "grab" mode, can move the thing
- right click cancel, left click confirm
- can you x, y and z to lock axis movement
- middle mouse button with snap to axis
- "S" to scale mode
- "R" to rotate mode

- middle mouse button to orbit, rotate the view itself
- hold shift and middle mouse to pan around
- (laptop with a trackpad will be a tough road ahead)
- Use the gizmo in the upper right to pan and rotate the view.
- But in User Preferences > Input > emulate 3 button mouse, you can fix it. Use alt key.

- Shift+D to duplicate object
- Number pad period key will focus on a selected object.
- But you can use the tilde key to bring up menu, and you can see that as one option.
- Use "X" or delete to delete object.

- Shift+A to add object
- Use f3 to search for "quick smoke"
- Then in simulator panel, change to "fire and smoke"

---

## 2: Basic Modelling

- right click: Shade Smooth to smooth out the poly
  - Can also use Shade Flat mode for debugging
- You get a little thing in lower left just after adding an item, that lets you update its properties.
- You want to go as low-poly as you can

- Wrench icon: Add modifier: Generate: Subdivision Surface.
- Use ctrl+1 to add it to any object.
- You may need to go User Preferences > Viewport > GPU Subdivision checkbox
- Oh cool it's labelled as Catmull-Clark in the UI -- haha neat
- Distinction between Levels/Viewport and Render -- what you're seeing in the live UI vs what you will see in the rendered version

- Things that look too perfect simply look fake.
- Alter the mesh. Leave Object mode. Enter Edit mode.
- Now you see all the vertices.
- (Damn it's true, "vertex" is a dope word.)
- Use same "G" hotkey as before to move a vertex. Sick.
- Hotkey to enter Edit mode is to simply press TAB.

- In the upper right you can enable Proportional editing.
- This adds a "circle of influence" around your selected point.
- Scroll or pageup+pagedown or change Settings > Keymap, in order to change radius of the sphere of influence.

- Use alt+click on edge to fully select the continued edge.
- So you can scale in the entire great circle around the (horizontal) center of the donut. Neat.

- When you save you get a ".blend" file.

---

## 3: Modelling the Icing

- Shift+D and then cancel, to put it in the same place.
- F2 will let you name an object
- Upper right to toggle X Ray to let you drag to get all the points, through and behind the front part of the mesh. Neat.
- Press X or Y on the gizmo to toggle Orthographic mode, get a straight-on view
- Flickering comes from z-fighting -- two faces fighting for which to render.
- Add modifier > Generate > Solidify. Then change the Offset from -1 to 1.

- Now make the icing's edge curved with like a wave.
- Using proportional mode again.
- Turn on Snapping in the upper right. You want to snap to the Face. Actually in this case we need Face Project. This lets it snap to the underlying donut's faces.
- Use the subdivision modifier again to Apply a more refined Geometry, as before. 4x.

- Fix backface projection:
- You can hide part of mesh to be ignored by Proportional circle tool.
- Ctrl Plus will expand out, select next vertices along a chain.
- H for hide.
- Alt+H to un-hide.
- Remember: middle mouse button will snap to closest axis. Use it after you use G to select a vertex.

- When you add a Subsurface ontop of a Solidify, you want the Solidify applied first, so you put it at the top.

- Head into Edge Data and Crease Intensity or something, mess with those values.

- Shift+ select to multiselect, yep.
- Select two vertices, tap "E" to enter Extrusion state.
- Creates a new breakaway face.
- Pulls down drips of icing around the donut.

---

## 4: Sculpting

- Technical check: enter edit mode, look at vertices
- Instead of, for each one, select, "G", click, ...
- Use the Shrink wrap modifier, under Forms (not Generate)
- You need this to happen first. It accepts a different shape as a parameter (you click on it).

- To gain access to the modifier-generated mesh, click "Apply" to "make the modifier real".
- Now you get the vertices for the icing.
- Want to create little bulges at the bottom of the drips.

- Sculpt mode! (In addition to Object and Edit modes)
- Many many tools appear in the left sidebar.
- Can use F and Shift+F to affect the radius and strength of the brush.

- "Inflate" brush.
- Curved edge is too jagged.
- We need to Apply the subdivision, because it's currently being applied after the sculpting.
- Now sculpting looks much better.

- "Grab" brush. It's like pushing clay with your finger.

- "Mask" brush (click M to toggle). Let's you dictate an "IGNORE ME" area,
- so when you apply a new effect, that part is ignored.

- By the way, when you enter Sculpt tool, you want to set Brush to Front Faces Paint.

- "/" is Isolation mode, to ONLY see a selected object.

- Use ctrl+I to invert the mask.

- Apply a uniform inflation: Mesh Filter brush. Hard to understand, poorly documented.
- "Hey at least it's better than Z-brush."

- Use Mask > Smooth mask to smooth it out.
- If you're in Sculpt mode, hold Shift to invoke the smooth tool.

---

## 5. Shading

- Add a Material with button from right-hand sidebar.
- Change color and roughness.

- Parent one object to another to make a group. Ctrl+P.
- You want "Keep transform".
- Select child first, then Ctrl+P, then its parent.
- That will make the child always follow the parent.

- Add an Image Texture for the material (with circle next to Background Color).
- Free textures from his site, Poliigon
- Unzip the download and use the one with "COL" in the name. Neat.

- Most material work happens in the Shading tab at top.
- Changes layout to show a Shader Graph (Node Setup).
- Material Mode will let you quickly preview materials by applying a higher-lighting setup.

- Shift A to add a node, try a HueSaturationValue node. Wow. Neat. Very flexible.
- We can apply an image texture to the roughness, instead of a flat value.
- Pull in the downloaded file with "ROUGHNESS" in the name.
- Tell Blender to look from sRGB to Non-Color data. Nice.

- Also can add bumps. This is under Normal.
- Now grab the "NRM" file. Again use Non-Color.
- But we need to convert the Normal image file with a NormalImageMap.

- This is a PBR shader. (Physically based rendering)
- And yes, as suspected, there is an addon that does all that node wiring for you.

- Now, painting the donut.
- Image texture, but instead of Open, we click New.
- Then you get a second view with the square texture and you can paint on either one. Awesome.

- We have to manually save this new image somewhere.

---

## 6. Geometry Nodes -- Sprinkles

- Geometry Nodes tab at top of screen
- Right click join areas on the spreadsheet to get rid of it
- With Icing selected, click "New"
- Interface very similar to Shader Material Nodes, but completely different system.

- You can expose an Offset value from a geometry node and then it shows up in the Modifier Stack. Really cool.
- Really powerful system.

- Shift A: Add > Point > Distribute Points on Faces
- Shift A: Add > Join Geometry to join the Points with the original Mesh, sure. Makes perfect sense.

- These points won't show up in the render yet.
- So Shift A > Mesh > UV sphere. This will be the sprinkle. Go as low-poly as possible.

- Can click Pin in the Geometry Nodes tab to make it always show, regardless of what object is selected.

- Now you can just drag the Sphere into the Geometry nodes tray. Wow. "Object Info."
- Instance on Points, takes in that object, and also the Distribute points, goes out to Join geometry.

- Change distribution from Random to Poisson Disk. Can set a Distance Min.
- Fixes issue with intersecting sprinkles and clipping.

- Weight painting, yet another Mode. Also used in Rigging.
- We can paint a value between 0 and 1 onto our mesh and use it later however we want.

- They get saved in our Data tab under Vertex Groups.
- Once again, drag and drop into Geometry nodes tray. Plug it into Density Factor.
- Node is called Named Attribute.

- Can you Ctrl with the Weight painting to paint negative values.

- Remember: ~ key to bring up menu, and then View Selected to zoom to selected object.

- Sharing between objects: again, you can expose values that you want to be different across objects, like Density Max. Drag it into empty slot on the Group Node (entry point). So sick. Then it shows up in the modifiers panel on the right.

- Now we want to scale our donut down to realistic size for reasons to do with rendering.
- Select 3 objects, then scale down.
- Hold Ctrl while scaling to make it happen in increments.
- You can also just type a value to scale to.

- Then as before you need to Apply the scale.
- Ctrl+A to apply, and then select Scale.

- But now we need to change the Density values.

- Nice trick to avoid huge values.
- Do a Math calculation inside the Geometry node: Utilities > Math > Math. Awesome.

- Yeah wow. This is pretty mind-blowing. Visual representation of how shaders work..

---

## 7. Geometry Nodes -- Long Sprinkles

---

## 8. Rendering

---

## 9. Layout

---

## 10. Lighting

---

## 11. Compositing

---

## 12. Animation

---

## 13. Rendering

---

## 14. Finale!

---

## And More

### Modeling

- Polygon Runway: 5 Blender models in 7 minutes
- Polygon Runway: Learn Blender Hard Surface Modeling in 5 Minutes
- Josh Gambrell: Why THESE Modeling Rules are so Important
- CG Boost: 6 Blender Hard-Surface Modeling Trick I Wish I Knew Earlier

### Texturing

- BlenderGuru Blender Texturing for Beginner's
- Ryan King Art: Procedural Worn Painted Metal Material
- CG Boost: Fake Large-Scale Forests in Blender
- Jamie Dunbar: 3 Easy steps to make Realistic Materials

### Animation

- Ryan King Art: Animation for Beginners!
- CbaileyFilm: Animation for Beginners! Learn to Animation like a PRO in Blender (CHOOSE ONE)
- CbaileyFilm: Animation for Beginners! Default Cube to Short Film in 29 Minutes
- Polyfjord: My new Rigging work flow
- Polyfjord: Animate a character in 15 Minutes

### Extra

#### Environment Design

- CG Boost: 10 Tips for Creating Epic Landscapes in Blender
- Max Hay: How to Add DEPTH you your Renders

#### Color

- Blender Guru: Understanding Color

#### Realism

- Blender: The Secrets of Photorealism

#### Geometry Nodes

- Erindale: Hexagon World with Geometry Nodes Fields
- Erindale: Endless Flight Loop with Geometry Nodes
- Ducky 3D: 34 video Geometry Nodes Playlist

#### Visual Effects

---

# Animation for Beginners! Learn to Animation like a PRO in Blender

- When you select an object, you immediately get a timeline in the bottom tray.
- One way to create a Keyframe is click button next to object property like X in the righthand panel.
- Or you can hit "I" to bring up Insert Keyframe, and select Location
- Or hit "I" while hovering over those properties.
- Now go to Time 80 in Timeline, and move the cube.
- Make sure you save the keyframe changes, with hitting "I".
- But there is an Autokeying button (on timeline controls) -- but this can be dangerous as well
- Your keys are like objects in the scene (G, etc), but they live in the Timeline.
- We just set 3 frames, and it smoothly interpolates the parabola for us.

- In bottom tray, click upper left icon and switch to Graph editor.
- User Prefs > Animation > Only show selected F curve keyframes
- You can then manipulate the tween graph's points. Neat.

- Select all keyframes, then right click > Interpolation Mode (easing)

- 17:00, mentions "rigs", perfect.
- Rig is like a control system for a puppet. A Skeleton.
- Create > Empty > Circle (or whatever). It's just a bare position in space.
- Parent the cube to the empty. The Empty is the controller.
- So when you scale the Empty, it will scale the cube, in the way you want, from the bottom rather than the center.

---

## Exporting Animation to Three.js

- https://www.youtube.com/watch?v=GByT8ActvDk&ab_channel=WaelYasmina
- Test things out by drag and drop gltf file into threejs.org/editor, Wow
- `const clip = THREE.AnimationClip.findByName(clips, "HeadAction");`

## Oh wow he does GLSL Snacks too

- https://www.youtube.com/watch?v=6mVB93NnfqQ&ab_channel=WaelYasmina

## Rigging in Blender

- https://www.youtube.com/watch?v=1khSuB6sER0&ab_channel=ProductionCrate
- Edit mode: Add Bone
- Select In Front in Armature settings to be able to see bones inside mesh
- You can right click to subdivide to make one bone into multiple, such as a spine.
- Click endpoint of a bone and click E to extrude another bone.
- Tool tab contains "X mirror Axis" so you don't have to do 2x the work
- Bones are essentially just Parented-to-each-other objects. Neat.
- With rig selected, Ctrl+P > With Automatic Weights
- So each bone can only control certain body parts. Sure.
- Mesh Edit > Merge by Distance can help make that automatic process work
- You can use Decimate modifier to remove vertices. Neat.
- Inverse Kinematics: Change in hand or feet can propagate back to entire arm/leg

## Rigging for impatient people

- https://www.youtube.com/watch?v=DDeB4tDVCGY&ab_channel=JoeyCarlino
- Shift+A to add Armature
- Can like right click: Symmetrize to copy all left-side bones to right
- Whoa, Ctrl+R to loop cut a rectanglular prism into a bunch of slices
- Some Weight Painting tips
- Oh sweet! With Rigid Rigging, which only works if model is made of of Separate objects/segments, you don't need Weights at all!
- You just parent directly to bones
- Select one object. Shift click the armature, then enter Pose mode.
- Then select the bone you want to parent it to, ctrl+P, choose Bone.
- Now the object should follow the bone when you move it.
- There is an add-on to speed this up: https://github.com/g3ntile/parentToNearestBone
- More Inverse Kinematics stuff, seems complicated haha

- Select object. Shift click armature. Enter pose mode. Select bone. Ctrl+P > Bone.
- OR:
  - Select the mesh object.
  - Go to the Object Constraints tab.
  - Add a Child Of constraint.
  - Set the Armature as the target.
  - Choose the correct Bone.
  - Click “Set Inverse” if needed to prevent a jump.
- Ok nvm that didn't quite work. I think because we had rotated and moved the armatures?
- Ctrl+Tab is pose mode shortcut.

---

## Oh Boy I'm Doing It

- Ok... on a trackpad:
- just using trackpad rotates the view.
- Shift+trackpad pans the view.
- Cmd+trackpad scales the view. Right on.

- Ahhhhh OK we had to set the Driver in the Bone > Transform.... NOT IN THE OBJECT > TRANSFORM
- AHA AND LOOK! OUR CUSTOM IDX PROPERTIES DID ACTUALLY GET ADDED! THEY GOT ADDED HERE AT BONE LEVEL, NOT AT THE OBJECT LEVEL.

- Fn+ Shift+ F5 to enter 3d mode and
- Fn + Shift + F11 to enter text mode.
- Wish there was easier toggle...
- We could also open up a new viewing pane....somehow....

- NOTE: We can use cmd+p instead of ctrl+p to get parenting menu
- NOTE: We use OPTION in place of ALT, e.g. OPTION+H to unhide elements
