# Star Ocean 4: Exact damage calculator

Go to the page here: https://wrayos.github.io/so4-exact-dmg-calc/

This is an incredibly simple calculator to assist players of Star Ocean 4 in getting the battle trophies for dealing exact amounts of damage.

There have existed a few applications over the years to help in this calculation, but they seem to have been lost to time.
The calculation itself is quite simple, and by putting this on Github I hope it can survive for any future players coming back to trophy grind this.

I have taken the formula written by Trueachievements user jaganshihieiyyh at this page - https://www.trueachievements.com/gamerblogcomment.aspx?gamerblogid=3462
Who in turn credits a user 'summoner191' as the original author.
To verify my outputs I referenced this video of the original 'so4exact.exe' application in action, and made sure all the numbers were the same - https://www.youtube.com/watch?v=uUvElsy3bAo

# Formula

This small app calculates which ATK your character requires to hit the desired damage number.  To achieve this you will need to gather some data:

- **low_attack (LA)**: Equip your character with the weakest weapon you have, while ensuring their ATK remains above 0.  Their ATK becomes this `low_attack` value.
- **low_damage (LD)**: With the weapon used for `low_attack` equipped, fight an enemy.  Attack the enemy and take note of how much damage is done (ignoring crits).  The damage becomes this `low_damage` value.
- **high_attack (HA)**: Equip your character with the strongest weapon you have.  Their ATK becomes this `high_attack` value.
- **high_damage (HD)**: With the weapon used for `high_attack` equipped, fight an enemy.  Make sure it is the same enemy as used for `low_damage`.  Attack the enemy and take note of how much damage is done (ignoring crits).  The damage becomes this `high_damage` value.
- **target_damage (TD)**: This is the exact damage you are trying to achieve.
- **target_attack (TA)**: The value we want.  This is what ATK you should try and get on your character to hit the desired target damage.

The formula documented by user jaganshihieiyyh on trueachievements.com was:

```
(TA - LA) * (HD - LD) = (TD - LD) * (HA - LA)
```
Where we want to solve for `target_attack (TA)`.  To do this we can rewrite the equation as
```
TA = (TD - LD) * (HA - LA) / (HD - LD) + LA
```
or 

```math
TA = {(TD - LD) * (HA - LA) \over HD - LD} + LA
```
And since that might annoy anyone who cares about mathematics..
```math
x = {(t - l)(y - z) \over h - l} + z; l \ne h 
```

# Goals

I'm a backend developer who has somehow avoided ever learning anything about front end development.  
This little calculator therefore is pretty terrible - but functions, is tiny, and is fast.  
I may use it as an excuse to learn a little more about front end work in the future.

## Todo

- [ ] Add validiation to inputs
- [ ] Styling
- [ ] Investigate using an actual framework instead of simple HTML as a learning exercise
