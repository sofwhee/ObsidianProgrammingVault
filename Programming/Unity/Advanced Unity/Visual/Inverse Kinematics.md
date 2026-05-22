https://github.com/Unity-Technologies/2d-animation-samples/blob/master/Documentation/2DIK.md

## Workflow summary

1. Add the IK Manager 2d component to the GameObject at the top of the hierarchy. Usually the root bone of the character skeleton.
2. Add to the IK Solvers list by selecting a type of IK Solver. Added as additional GameObjects to the heirarchy.
3. With an IK Solver selected, select its Effector bone/transform. Create or set a Target for the IK Solver.
4. Position bones by moving the target. It will apply transforms to move the chain of bones with IK for you.

## IK Solvers

Calculates the position and rotation the Effector and all its connected bones should take to achieve their Target position.

Each type of IK Solver has its own algorithm to make them better suited to different kinds of conditions.

Effector
- Define the bone or transform the IK Solver solves for.
Target
- The transform used to indicate the desired position for the Effector.
Constrain Rotation
- Constrains rotation of the Effector to the rotation of the Target.
Restore Default Pose
- Restores bones to the positions before 2D IK is a applied. Disable to apply 2D IK in relation to the Effector's current position and rotation
Weight
- Adjusts the degree the IK Solver's solution affects the original Transform positions. At 0, the IK solution is ignored. At 1, the IK solution is fully applied. Further influenced by IK Manager's master Weight.

CCD and FABRIK extra properties
Chain Length
- Starting from Effector, it's the number of bones/transforms in the chain that the IK solution is applied to.
Iterations
- The number of times the algorithm runs.
Tolerance
- Threshold where the Target is considered to have reached its destination position, and when the IK stops iterating.

## IK Manager 2d

If the arm bone is the child of the torso bone, the torso's IK solver should be set above the arm's Solver in the list. 
Rearrange Solvers by dragging the leftmost edge of a row up or down.

## Limb

Two bone solver.
Fixed to three bones - starting from Effector bone, including up to two additional bones in its chain.

## Chain (CCD) Cyclic Coordinate Descent

Gradually becomes more accurate the more times the algorithm is run.

## Chain (FABRIK) Forward and Backward Reaching Inverse Kinematics

Solution becomes more accurate the more times the algorithm is run. Generally takes less iterations to reach the Target's destination, but slower per iteration if rotations are applied. Solver is able to adapt quickly if the bones are manipulated in real time.

## Set a Target

1. Select the last bone in the chain
2. Create an empty transform
3. Move transform position to the tip of the last bone in the chain
4. Select the IK solver
5. Drag the transfrom from the heirarchy into the Effector field
6. Click create target button. A target is made at the transform's position.
7. If create target is greyed out, ensure chain length is set to one or greated.
8. Target is created as IK solver child, appears as circle gizmo.
9. Move target to manipulate chain of bones