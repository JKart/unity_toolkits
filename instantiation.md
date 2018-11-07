







```c#
using System.Collections;
using System.Collections.Generic;
using UnityEngine;

public class RockSpawner : MonoBehaviour
{
    [SerializeField]
    GameObject prefabRock;

    [SerializeField]
    Sprite rockSprite0;

    [SerializeField]
    Sprite rockSprite1;

    [SerializeField]
    Sprite rockSprite2;

    Timer spwanTimer;
    const float spwanDelay = 1;

    void Start()
    {
        spwanTimer = gameObject.AddComponent<Timer>();
        spwanTimer.Duration = spwanDelay;
        spwanTimer.Run();
    }

    // Update is called once per frame
    void Update()
    {
        if (spwanTimer.Finished)
        {
            spwanTimer.Run();
            if (GameObject.FindGameObjectsWithTag("c3rock").Length < 3)
            {
                SpwanRock();
            }
        }
    }

    void SpwanRock()
    {
        //generate screen coordinate
        Vector3 location = new Vector3(
            Screen.width / 2, Screen.height / 2, -Camera.main.transform.position.z);

        //convert screen coordinates to world coordinate
        Vector3 worldLocation = Camera.main.ScreenToWorldPoint(location);
        GameObject rock = Instantiate(prefabRock) as GameObject;
        rock.transform.position = worldLocation;

        //set random sprite for new rock
        SpriteRenderer spriteRenderer = rock.GetComponent<SpriteRenderer>();
        int spriteNumber = Random.Range(0, 3);
        if (spriteNumber == 0)
        {
            spriteRenderer.sprite = rockSprite0;
        }
        else if (spriteNumber == 1)
        {
            spriteRenderer.sprite = rockSprite1;
        }
        else
        {
            spriteRenderer.sprite = rockSprite2;
        }
    }
}

```



## Screencoordinate and worldcoordinate

```

```







## How to use instantiate



```C#
GameObject teddyBear = Instantiate(prefabTeddyBear) as GameObject;

```





## Mouse Input Magement

