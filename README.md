# BalanceSetons
FAF is a community maintained online gaming community for the classic RTS Supreme Commander: Forged Alliance. Seton's Clutch is one of the more popular maps. BUT it's hard to get appropriate game balance. I'm going to use machine learning to see if I can balance Seton's better than the in game tool.

In the first stage, I'll build a model to see how well I can predict game outcome. Then I'll try and build a web API as a tool to balance future games.

# Why is this needed?
Typically, games on FAF are balanced based on the total ELO of their teams. This has a number of limitations when it comes to Seton's, which is why experienced players spend time balancing the game from their own knowledge. This is hard for new players to do well, and is a source of lobby-sim and arguments:

1. *Map knowledge is not modeled.* It matters a lot whether player's know the meta-game for the map, and whether they have a build order and strategy. A player with a 1200 rank but who has never played Seton's is not the same as someone with a 1200 who only plays Seton's is not the same as a player ranked 1200 who plays everything, but always wins on Seton's and always loses playing everything else.
2. *Lane balance is not taken in to account.* Even if the game is balanced over-all, it's not fun to play Seton's if the player on the opposite side in your lane is much stronger than you.
3. *Some positions are more important than others.* A strong player can carry a team from the air position easily, from the navy positions less easily, but probably not from the front. 
4. *Position knowledge is not modeled.* Some people prefer particular positions and are not good at other positions. Each position has its own build order, and they sometimes require a different temperment. Air needs fast reactions and a winning mindset, navy is slower, front needs to be conservative but also team-minded. Not everyone is good at the same things.

As a bonus, ELO based ranking doesn't deal well with common social situtaions such as: players who are buddies and want to play together, new players with unknown ranks, and players who will quit your game if you don't give them navy after you've been waiting for an hour for the lobby to fill.

# How can we deal?
It's hard to know how to weight all these factors. Fortunately, a support vector machine can do it for us. We can download replay history from the FAF API, model these features statistically, and then see how close a model we can produce. 
