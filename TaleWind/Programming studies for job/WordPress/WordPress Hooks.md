They're basically just events.

#### Define a hook in core, themes, or plugins.
`do_action()`
or
`apply_filters()`

#### Make a callback function.
```
function DoBlah()
{
	do blah blah blah
}
```

#### Register a callback function to a specific hook:

##### `add_action()`
Executes code. Side effects. **Does not return a value.**

`add_action( string $hook_name, callable $callback, int $priority = 10, int $accepted_args = 1 )`

`$hook_name` - name of action hook (`wp_head`, `init`, `save_post`) to which function will be attached.
`$callback` - name of function or method when hook triggered. ( `DoBlah` )
`$priority` - optional integer determining execution order. (asc) Defaults 10.
`$accepted_args` - optional integer specifying number of args passed to callback.

##### `add_filter()`
Modify data before used or displayed. **Returns a value.**

`add_filter( 'hook_name', 'callback_function' )`

Same thing, but allows plugins and themes to modify internal data at runtime.

#### Execution
When WordPress reaches the hook point during runtime it executes all registered callbacks in order of priority.
``