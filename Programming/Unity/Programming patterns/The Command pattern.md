![[Pasted image 20260418150029.png]]

Allows actions to be represented as objects.
## Why?

- If you want to keep a player's input history
- Undo/Redo functionality
- Queue up actions before executing them

## Why not?

- Much more overhead.
## Examples

- RTS - Queue up unit and building actions
- Turn based - Select a unit, queue up moves
- Puzzle - undo, redo
- Fighting - reading inputs in a specific command list results in combos / special moves

## How to implement

![[Pasted image 20260418145828.png]]

![[Pasted image 20260418153325.png]]
### ICommand Interface

```C#
public interface ICommand
{
	void Execute()
	void Undo()
}
```
### Command invoker

```C#
public class CommandInvoker
{
	// stack of command objects to undo
	private static Stack<ICommand> _undoStack = new Stack<ICommand>();
	// stack of command objects to redo
	private static Stack<ICommand> _redoStack = new Stack<ICommand>();
	// execute command object directly, save to undo stack
	public static void ExecuteCommand(ICommand command)
	{
		command.Execute();
		_undoStack.Push(command);
		
		// clear redo stack if we make a new move
		_redoStack.Clear();
	}
	
	public static void UndoCommand()
	{
		if (_undoStack.Count > 0)
		{
			ICommand activeCommand = _undoStack.Pop();
			_redoStack.Push(activeCommand);
			activeCommand.Undo();
		}
	}
	
	public static void RedoCommand()
	{
		if (_redoStack.Count > 0)
		{
			ICommand activeCommand = _redoStack.Pop();
			_undoStack.Push(activeCommand);
			activeCommand.Execute();
		}
	}
}
```
### Command object

```C#
public class MoveCommand : ICommand
{
	PlayerMover playerMover;
	Vector3 movement;
	public MoveCommand(PlayerMover player, Vector3 moveVector)
	{
		this.playerMover = player;
		this.movement = moveVector;
	}
	public void Execute()
	{
		playerMover.Move(movement);
	}
	public void Undo()
	{
		playerMover.Move(-movement);
	}
}
```
