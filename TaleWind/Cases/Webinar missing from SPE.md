1. pulled up csv file that we processedf or the migration
2. maybe it was the import timing out?
3. we couldn't fiure out why
4. upload the videos
5. meta_key null (wb media id) meta value should have something in them

6. Recreate the problem
	1. I need to be able to access the webinar in the same way as them. How do I do this?
		1. Log in with my own credentials?

The tabs at the top, and the favicons in the tabs, all seem to be related to workerbee. It might not be important, but i just want to make sure to cover all the bases here.

simplest version of this code

Player has a list of upgrades they collected
List<GameObject> upgradesCollected

Boss goes through each one at random
save list to a var
ShuffleList
foreach...

then removes it from the player (this can be a method on the player that downgrades it based on upgrade)
playerScript.removeUpgrade(upgrade)

spawns an image copy of it next to the player
GameObject SpawnUpgradeImage(upgrade, side)

image copy travels to the boss
TravelToBoss(upgrade)

image copy flashes white and self destructs
UpgradeSelfDestruct(upgrade)

upgrade applies to boss
ApplyUpgrade(upgrade)