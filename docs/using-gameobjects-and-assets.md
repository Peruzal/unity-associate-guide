# Using GameObjects and Assets

## GameObjects

- Everything within a scene view is called a GameObject.
- Every GameObject have a Transform property
- Components can be added to the GameObjects to modify their properties
- Scripts can also be added to GameObjects as components
- Components can be added, copied or removed using using Inspector cog icon
- Scripts can be added by dragging them to an empty space in the Inspector view or clicking the Add Component button adn choosing New Script
- GameObjects can be parented and the parent child relationship is represented by arrows in the Hierarchy Window.
- GameObjects can selected either in the Hierarchy window or the Scene view

![GameObjects][1]

1. GameObjects as seen from the Hierarchy window
2. GameObjects in the Scene Window
3. Components of the Cube GameObject


## Working with Prefabs

- Prefabs are pre-configured game objects. You can turn any GameObject from the Scene into a prefab by dragging it into the Project Window.

- Prefabs are saved as files as part of the project.

- Prefabs are used for all sorts of GameObjects, e.g creating projectiles, explosions, enemies, collectables, and many more.

- You can modify the prefab and apply the changes to all the instances of the prefab or revert the changes entirely.

## Tags

- Tags are used to identify game objects, e.g we could have many enemies in the game and we can identify them all by tagging them as enemies.

- You can assign an existing tag or create one if it doesn't already exists.

- Tags can used from code. This is very useful especially within the script of a prefab, e.g when an enemy is created, it might need to find the player in the game.

![Tags][2]


## Using Tags in Scripts

```csharp hl_lines="15 16"
// Finding the player from within a script attached to the enemy
using System.Collections;
using System.Collections.Generic;
using UnityEngine;
using UnityEngine.AI;

public class Enemy : MonoBehaviour
{
    GameObject player;
    NavMeshAgent agent;
    // Start is called before the first frame update
    void Start()
    {
        agent = GetComponent<NavMeshAgent>();
        // Find the player in the game
        player = GameObject.FindGameObjectWithTag("Player");
    }

    // Update is called once per frame
    void Update()
    {
        // set the enemy destinate to player
        agent.SetDestination(player.transform.position);
    }
}
```

## Layers

Layers allow us to define some common functionality across unrelated game objects, e.g we can hide objects in the same layer from the camera, which objects should ignore a Raycast and which object we would like to see in the Scene view.

![Layers][3]

If the layer is there, we can add a new layer.

### Adding a New Layer

- Click the Layer drop down
- Choose Add Layer

or alternatively we can add layers by using the menus byt choosing **Edit** ->** Project Settings** -> **Tags and Layers**



## Importing Assets

## Working with Sprites

[1]: images/gameobjects-scene-view.png
[2]: images/tags.png
[3]: images/layers.png