# UEProject
Super inefficient blueprint based boids with a ton of inefficient methods, mainly to test lots of blueprint features and get comfortable.

Originally built in UE4, (mostly) updated files in zip though some features are still missing or need to be supplemented since they were incomplete to begin with.


Just import or drag/drop the uassets into your editor in a Twin Stick Shooter template, replace any and all that need to be overwritten. They just use default assets mostly as the blueprints are what you want. 

TestAI Checklist
- DetourCrowdAI pathing, nice default behavior tree with smart avoidance built in. Looks really good and performs well.
- Acceleration based movement, physicsy repulsion with variables you can control
- AI has group vision with line of sight and distance checking for you and for group members. If another AI is within range, and another AI is too far away but within that AI's range, it will spot you. These are toggleable options too.
- [Boids](https://en.wikipedia.org/wiki/Boids)
- Boids are so cool, everything is adjustable and tied to the physics engine. Play with all of the visible default parameters to see the behavior changes. We have a full swarm AI controls. 

- At any point in game or in editor you can tweak the:

-- separation, 

-- alignment, 

-- cohesion, 

-- tethering, 

-- tether bounding box, 

-- tether origin (orbit point), 

-- swirl

-- grouping sizes (for performance i.e. the nested for-loops in place create potentially up to t x n x 2(g + b) calls per sec, so if 100 boids with size 30 local groups, firing at 10 times per second to do grouping and boids will create about 60,000 times however many sub calculations per second. Resulting in millions of calculations. I will optimize it as much as I can but keep group sizes small while you can still spawn a few hundred no problem.

-- grouping updates (randomized),  

-- grouping radius (you can combine this with grouping sizes and grouping timings to optimize further),

-- impulse timing, 

-- group leader chance (doesn't do anything by default), 

-- predator chance (default 0). 

-- optional require line of sight to other boids 

-- detourAI functions, requires actors near navigable surfaces to create paths - does NOT work on flying boids unless near surfaces that are connected to you.

-- Basic 3D navigation and environment avoidance. Plenty of tweaks possible. 

-- Collision physics tweakable with simple variables (e.g. mass, inertia)

-- Ground Boids mode looks pretty good and swarmy, you can toggle between flight and ground modes

-- Ground Boids have navigation and different search modes: attacking (red), hunting i.e checking last known position (yellow), homing (purple), stunned (green), idle (cyan).

- Boids Macro is called each tick and constrained by timers and group size limits to not eat too many resources.

This way we can have really good base AI and tweak their parameters to suit different areas (e.g. maybe they have swirl in one room and in another room they fly, and transition between the two procedurally)

Other stuff:
- Particle FX tests, drop the whole folder in with your assets in the Blueprints folder
- Key cards, Goals (just resets the level), Ammo drops, Proximity Doors (lockable, can be made to open for boids instead of the pawn)
- Custom projectile for the twin stick pawn to shoot the boids with.
- Custom twin stick pawn with mouse & keyboard, as well as twin stick controller controls.

TODO:
- Add some acceleration and deceleration to the player pawn so movement isn't exact (easy)
- Mouse shooting + player rotation control (easy)
- More stealth options, more doors & buttons, other gameplay material,.
- Get freaky wit da boids

- May need to relegate to an AI spawner so dozens of AI controllers aren't spawned, although it wasn't an issue before so maybe not.
- Improve the grouping as needed. Limit group size for performance gainz, play with the regrouping timer and stuff to find a good balance for performance.
- Test Patrolling, the automatic pathing should be just fine.
- Tune Physics, create mass physics behaviors.
- Last: Navigation learning algo, need to make a graph tree to represent level layouts then basically just reweight it based on player choices when under pursuit (so better stealth = less smart AI), then we override the AI path when this occurs to split them up probabilistically based on weights. Simple stupid but will freak players the fuck out if they catch on.


Level design ideas:
- Momentum based escape puzzles
- Physicsy items
- Use the enemy physics for puzzle solving
- Flow Control puzzles - freaky crowd physics - simply set the LastKnownPosition on a boid and they will patrol over there automatically. 

test map:
![testmap](https://github.com/moothyknight/UEProject/blob/master/TestMap.PNG?raw=true)


Card Key Level Blueprint implementation:
![lbp](https://github.com/moothyknight/UEProject/blob/master/lbp.PNG?raw=true)
