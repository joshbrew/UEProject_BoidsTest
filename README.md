# UEProject
dum dum da dum dum dum dummmm


Just import or drag/drop the uassets into your editor. They just use default assets as the blueprints are what you want. 

TestAI Checklist
- DetourCrowdAI pathing, nice default behavior tree with smart avoidance built in. Looks really good and performs well.
- Acceleration based movement, physicsy repulsion with variables you can control
- AI has group vision with line of sight and distance checking for you and for group members. If another AI is within range, and another AI is too far away but within that AI's range, it will spot you. These are toggleable options too.

TODO:
- TEst Patrolling, the automatic pathing should be just fine.
- Dynamic and fixed grouping, flocking behaviors (i.e. creating cool flow patterns while idle or when grouped)
- Tune Physics, create mass physics behaviors.
- Last: Navigation learning algo, need to make a graph tree to represent level layouts then basically just reweight it based on your choices, then we override the AI path when this occurs to split them up probabilistically based on weights. Simple stupid but will freak players the fuck out if you catch on.


Level design ideas:
- Momentum based escape puzzles
- Physicsy items
- Use the enemy physics for puzzle solving
- Flow Control puzzles - freaky crowd physics
