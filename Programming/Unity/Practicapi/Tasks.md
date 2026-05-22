In practice, we avoid using these.
These work in a separate thread from Unity's main thread.
So they're dangerous to use.

## Instructions

async
await
WhenAll

If a method requires more time...
We can use Tasks to wait for each line asynchronously.
(Similarly to CoRoutines)

A method that requires time.

```C#
private async Task<int> CalculatePlayerHighScore(Player player)
{
	await Task.Delay(100) // heavy calculations
	return player.HighScore
}
```

A method of methods that requires time

```C#
public (int highScore, int winStreak, int Rank) GetPlayersMatchResult(Player player)
{
	var highScore = CalculatePlayerHighScore(player);
	var winStreak = CalculatePlayerWinStreak(player);
	var rank = CalculatePlayerRank(player);
	
	return (highScore, winStreak, rank)
}
```

You can use Task to wait for each line asynchronously

```C#
// add async Task and encapsulate parameters with < >
public async Task<(int highScore, int winStreak, int Rank)> GetPlayersMatchResult(Player player)
{
	// add 'await's
	var highScore = await CalculatePlayerHighScore(player);
	var winStreak = await CalculatePlayerWinStreak(player);
	var rank = await CalculatePlayerRank(player);
	
	return (highScore, winStreak, rank)
}
```

With Tasks, we can upgrade this by executing all methods in parallel

```C#
// add async Task and encapsulate parameters with < >
public async Task<(int highScore, int winStreak, int Rank)> GetPlayersMatchResult(Player player)
{
	// remove 'await's
	// make them end with 'Task'
	var highScoreTask = CalculatePlayerHighScore(player);
	var winStreakTask = CalculatePlayerWinStreak(player);
	var rankTask = CalculatePlayerRank(player);
	
	await Task.WhenAll(highScoreTask, winStreakTask, rankTasks)
	
	var highScore = await highScoreTask;
	var winStreak = await winStreakTask;
	var rank = await rankTask;
	
	return (highScore, winStreak, rank)
}
```