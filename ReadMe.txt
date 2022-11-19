1. How to build the project

- Please set "CollisionDetection" project as a starter project and build with x64 configuration / Debug or Release mode.
  Or you can execute with "CollisionDetection.exe" file in x64\Debug(or Release) folder.

- GitHub Link:
https://github.com/kanious/Project02_Collision



2. User Input Option

 < For Camera >
 You can look around the scene with this camera.
 * WASD : Moving Camera (look/right direction).
 * Space/Left Shift : Up/Down Camera (up direction).
 * Alt : Enable/disable mouse. Rotating camera with mouse move when mouse is disabled.

 < For Object >
 This is a bit complicated, but the horizontal movement(xz) and rotation on the Y axis are the same formation as in usual WASD + QE.
 * TFGH : Moving Object (xz direction).
 * U/J : Up/Down Object (y direction).
 * R/Y : Rotate Object to the Y axis.
 * Left/Right Arrow : Rotate Object to the Z axis.
 * Up/Down Arrow : Rotate Object to the X axis.

 < Etc >
 * F1 : Enable/disable Large Mesh Bounding boxes (leaf nodes of octree).
        * Only the bounding boxes of leaf nodes where triangles exist are enabled.
 * F2 : Enable/disable Object Bounding box.
 * F3 : Reset Object to the initial position (0, 0, 20) and initial rotation (0, 0, 0).
 * ESC : Close the program.



3. Simple Description

- Building an octree takes some time.
  In debug mode : about 2 min.
  In release mode : about 6 sec.

- When the object and the large mesh collide, the bounding boxes of the area they collided will be enabled.

- If you already enabled the bounding boxes, you can notice the collision by color changing.
  ( Object bounding box color : Blue )
  ( Large mesh bounding box color : Green )
  ( Collided bounding box color : Red )

- Collision checking is performed as follows:
  1. Saves the force to control the object when the move/rotate key is pressed.
  2. Check in advance if the position to move/rotate collides with Octree.
     - Finding the areas(AABB) that collide with object in octree.
     - Check if the object(OBB) intersects with any triangle in the areas found above.
  3. If they collide, the saved force will not apply.

- I checked the collision using the triangles of the large mesh and the oriented bounding box of the object.

- Since the triangles from the surface of the mesh are not very smooth, the movement along the surface is also not smooth.
  If the object is stuck, please use F3 command to reset it.



