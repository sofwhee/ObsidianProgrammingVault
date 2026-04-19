Reuses game objects instead of creating and destroying them.

Reduces CPU load and garbage collection overhead.

Use when gameplay is stuttering due to instantiating large numbers of objects.
Otherwise, don't use prematurely. It adds more complexity.

Create objects in advance and store them in a pool.
When needed, take them from the pool and use them.
When done, return to the pool.



## How it works in Unity

![[Pasted image 20260418101603.png]]

Initialize objects in a deactivated pool.
Pre-instantiate all required objects before gameplay. (Do it when users wouldn't notice the stutter, like a loading screen)
Once used, deactivate again.
Return to the pool.

Request from pool, activate, deactivate, return to pool.

## How to use

