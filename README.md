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

---

---

---

---

---

---
