Only use Tuples in small, independent methods.
Where defining a Struct feels like an overkill.

(They're less readable, and passing around an object where you can't find its usages.)

Tuple: `return (blah, blah, blah);`

Defining a whole struct for one method:

```C#
public MatchResult GetPlayersMatchResult(Player player)
{
	var highScore = CalculatePlayerHighScore(player);
	var winStreak = CalculatePlayerWinStreak(player);
	var rank = CalculatePlayerRank(player);
	
	return new MatchResult(heighestScore, winStreak, rank);
}

public struct MatchResult
{
	public int HighScore;
	public int WinStreak;
	public int Rank;
	
	public MatchResult(int highScore, int winStreak, int rank)
	{
		HighScore = highScore;
		WinStreak = winStreak;
		Rank = rank;
	}
}
```

Using a tuple instead:
```C#
public MatchResult GetPlayersMatchResult(Player player)
{
	var highScore = CalculatePlayerHighScore(player);
	var winStreak = CalculatePlayerWinStreak(player);
	var rank = CalculatePlayerRank(player);
	
	// return new MatchResult(heighestScore, winStreak, rank);
	return (heighestScore, winStreak, rank);
}

// Struct no longer declared down here
```