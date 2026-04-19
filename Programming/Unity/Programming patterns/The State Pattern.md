You have a playable character with different states.
Standing. Running. Walking. Jumping.

**Use it if you expect your states to get complex.**
**Don't use if you only have a few states to track.**

FSM = finite states.
State Machine = Easily extensible number of states.

The Unity Animation State Machines are a type of FSM. (**Finite State Machine**)

![[Pasted image 20260417235632.png]]

It is a list of states.

An FSM can be in exactly one of **a finite number** of states.

FSM
- Has an initial state
- Transitions
- Conditions for each transition

Again, like the Animation State Machine in Unity.

A simplified example: You decide to make your game logic a switch statement.

This can work, but transitions can be difficult to make here. And some people find long switch statements with many transitions between them difficult to understand.
## FSM example

```csharp
public enum PlayerControllerState
{
    Idle,
    Walk,
    Jump
}

public class UnrefactoredPlayerController : MonoBehaviour
{
    private PlayerControllerState state;

    private void Update()
    {
        GetInput();

        switch (state)
        {
            case PlayerControllerState.Idle:
                Idle();
                break;
            case PlayerControllerState.Walk:
                Walk();
                break;
            case PlayerControllerState.Jump:
                Jump();
                break;
        }
    }

    private void GetInput()
    {
        // process walk and jump controls
    }

    private void Walk()
    {
        // walk logic
    }

    private void Idle()
    {
        // idle logic
    }

    private void Jump()
    {
        // jump logic
    }
}
```


On the other hand...
## State design pattern

![[Pasted image 20260418002158.png]]

The State Design pattern defines an interface for a state.
Then, it has a class that implements this interface for each state.

It seems like IBeginDragHandler, IDragHandler, IEndDragHandler.

Benefits
- You can add new states without impacting existing states.
## Example State

This is for the player's idle state.

It monitors the Character's velocity / jump state.
Then, invokes the State Machine's transition method. (TransitionTo)
It only invokes it when it is appropriate.

```csharp
using System.Collections;
using System.Collections.Generic;
using UnityEngine;

	namespace DesignPatterns.State
	{
	    public class IdleState : IState
	    {
		    // Constructor is used to pass in PlayerController object
		    // player contains a reference to the State Machine
		    // and stuff needed for the update logic.
	        private PlayerController player;

	        // color to change player (alternately: pass in color value with constructor)
	        private Color meshColor = Color.gray;
	        public Color MeshColor { get => meshColor; set => meshColor = value; }
	        // pass in any parameters you need in the constructors
	        public IdleState(PlayerController player)
	        {
	            this.player = player;
	        }

	        public void Enter()
	        {
	            // code that runs when we first enter the state
	            //Debug.Log("Entering Idle State");
	        }

	        // per-frame logic, include condition to transition to a new state
	        public void Update()
	        {
	            // if we're no longer grounded, transition to jumping
	            if (!player.IsGrounded)
	            {
	                player.PlayerStateMachine.TransitionTo(player.PlayerStateMachine.jumpState);
	            }
	

	            // if we move above a minimum threshold, transition to walking
	            if (Mathf.Abs(player.CharController.velocity.x) > 0.1f || Mathf.Abs(player.CharController.velocity.z) > 0.1f)
	            {
	                player.PlayerStateMachine.TransitionTo(player.PlayerStateMachine.walkState);
	            }
	        }
	

	        public void Exit()
	        {
	            // code that runs when we exit the state
	            //Debug.Log("Exiting Idle State");
	        }
	    }
	}
```

## Implementation

- Interface "IState" (as an example)
	- Entry logic (executed when first entering state)
	- Update logic (executed every frame) (LateUpdate, FixedUpdate too)
	- Exit logic (executed before leaving state and transitioning)
- Class for each IState-state. IdleState, WalkState, JumpState.
- StateMachine.cs class
	- Define CurrentState as read-only (another obj will set with Initialize)
	- Reference State objects
	- Make an event to notify other objects when state changes
	- Make new instances of states with constructor
	- 


```csharp
// IState is just an example name for the interface.
public interface IState
{

    public void Enter()
    {
        // code that runs when we first enter the state
    }

    public void Update()
    {
        // per-frame logic, include condition to transition to a new state
    }

    public void Exit()
    {
        // code that runs when we exit the state
    }
}
```

```C#
// a different class
// Should this inherit from Monobehaviour? i guess not?
public class IdleState : IState
{
	private PlayerController player;
	
	public IdleState(PlayerController player)
	{
		this.player = player;	
	}
	
	public void Enter()
	{
		// Code that runs when we enter the state
	}
	
	// Include condition to transition to a new state
	public void Update()
	{
		// if we're no longer grounded, transition to jumping
		// StateMachine is the next thing to make
		if (!player.IsGrounded)
		{
					player.PlayerStateMachine.TransitionTo(player.PlayerStateMachine.jumpState);
		
		// if we are faster than minimum thershold, transition to walking
		if (Mathf.Abs(player.CharController.Velocity.x) > 0.1f || Mathf.Abs(player.CharController.velocity.z) > 0.1f)
		{
				player.PlayerStateMachine.TransitionTo(player.PlayerStateMachine.walkState);
		}
		}
	}
	
	public void Exit()
	{
		// code that runs when we exit the state
	}
}
```

```csharp
[Serializable]
public class StateMachine
{
	public IState CurrentState { get; private set; }


	// reference to the state objects
	public WalkState walkState;
	public JumpState jumpState;
	public IdleState idleState;


	// event to notify other objects of the state change
	public event Action<IState> stateChanged;


	// pass in necessary parameters into constructor 
	public StateMachine(PlayerController player)
	{
		// create an instance for each state and pass in PlayerController
		this.walkState = new WalkState(player);
		this.jumpState = new JumpState(player);
		this.idleState = new IdleState(player);
	}


	// set the starting state
	public void Initialize(IState state)
	{
		CurrentState = state;
		state.Enter();


		// notify other objects that state has changed
		stateChanged?.Invoke(state);
	}


	// exit this state and enter another
	public void TransitionTo(IState nextState)
	{
		CurrentState.Exit();
		CurrentState = nextState;
		nextState.Enter();


		// notify other objects that state has changed
		stateChanged?.Invoke(nextState);
	}


	// allow the StateMachine to update this state
	public void Update()
	{
		if (CurrentState != null)
		{
			CurrentState.Update();
		}
	}
}
```