## Warning:

![[Pasted image 20260503084741.png]]

It adds complexity, so don't do premature optimization!

## Example

```C#
public interface IAttacker
{
	// abstract, meaning it is intended to be given an implementation
	// by the interface-ee.
	abstract int AttackDamager { get; }
	// The "Contract".
	// Anything that implements this interface MUST define this function.
	void Attack(Hero otherHero);
}
```

```C#
public class Vampire : Hero, IAttacker, IHealer
{
	public override string Name => "Vampire";
	public int AttackDamage => _attackerBehaviour.AttackDamage;
	//...
	private readonly AttackerBehaviour _attackerBehaviour;
	//...
//...
```

Wait... what the heck?

```C#
public int AttackDamage => _attackerBehaviour.AttackDamage;
//...
private readonly AttackerBehaviour _attackerBehaviour;
```

What's this mean?
Hmm...

```C#
//... continuing in class...
public Vampire()
{
	_attackerBehaviour = new AttackerBehaviour(this, 3);
	_healerBehaviour = new HealerBehaviour(this, 1);
}
```

Oh! `AttackerBehaviour` is a class?
And it takes parameters when making a new instance of it?
Why? How?
Also why is all this in a method named `Vampire`, the same name as the class itself?

```C#
public class AttackerBehaviour : IAttacker
{
	private Hero _hero;
	public int AttackDamager { get; }
	
	public AttackerBehaviour(Hero hero, int attackDamage)
	{
		_hero = hero;
		AttackDamage = attackDamage;
	}
	
	public void Attack(Hero otherHero)
	{
		otherHero.Health -= AttackDamage;
		Debug.Log(_hero.Name + " attacked " + otherHero.Name);
	}
}
```

Oh okay!
So when you set a method that's the same name as the class it's in...
Anything that calls `new` on the class is triggering that method and anything in it.
So you could set variables on instantiation.

So when you declare a `new AttackerBehaviour`, you must pass a couple parameters...
and in doing so you've essentially created a new method with built in variables
In this case, `Attack()`, where Hero and AttackDamage are set in the method's variable environment.
also permanently load some parameters onto the Vampire `AttackerBehaviour _attackerBehaviour` variable.

So the complete class looks like...

```C#
public class Vampire : Hero, IAttacker, IHealer
{
	public override string Name => "Vampire";
	public int AttackDamage => _attackerBehaviour.AttackDamage;
	public int HealAmount => _healerBehaviour.HealAmount;
	private readonly AttackerBehaviour _attackerBehaviour;
	private readonly HealerBehaviour _healerBehaviour;
	
	public Vampire()
	{
		// Set variables in AttackerBehaviour on creation
		// new AttackerBehaviour(Hero, AttackDamager)
		_attackerBehaviour = new AttackerBehaviour(this, 3);
		_healerBehaviour = new HealerBehaviour(this, 1);
	}
	
	public void Attack(Hero otherHero)
	{
		_attackerBehaviour.Attack(otherHero);
		// Interface
		// Attack(otherHero) -> 
		// otherHero's .Health -= AttackDamage.
	}
	
	public void Heal()
	{
		_healerBehaviour.Heal();
	}
```


```C#
public interface IHealer
{
	// abstract, meaning it is intended to be given an implementation
	// by the interface-ee.
	abstract int HealAmount { get; }
	// The "Contract".
	// Anything that implements this interface MUST define this function.
	void Heal();
}
```

```C#
public HealerBehaviour : IHealer
{
	private Hero _hero;
	public int HealAmount { get; }
	
	public HealerBehaviour(Hero hero, int healAmount)
	{
		_hero = hero;
		HealAmount = healAmount;
	}
	
	public void Heal()
	{
		_hero.Health += HealAmount;
		Debug.Log(_hero.Name + "Healed by " + HealAmount);
	}
}
```