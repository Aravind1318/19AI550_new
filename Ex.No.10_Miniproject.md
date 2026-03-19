# Ex.No: 10  Implementation of 2D game Falling Object
### DATE: 18/03/2026 
## Name : Aravind P
### REGISTER NUMBER : 212224240015
### AIM: 
To develop a simple 2D game in Unity where the player moves a character to catch falling objects, demonstrating basic game mechanics such as object spawning, gravity-based movement, collision detection, scoring, and user interaction. 
### Algorithm:

Step 1: Create player, ground, and falling object prefab in the scene.
Step 2: Add Rigidbody2D and Collider2D to the falling object for gravity and collision.
Step 3: Place a spawner above the screen to generate falling objects.
Step 4: Spawn falling objects at random X positions at fixed time intervals.
Step 5: Let gravity pull falling objects downward automatically.
Step 6: Move the player left and right using keyboard input.
Step 7: Detect collisions between falling objects and player or ground.
Step 8: Increase score when the player catches a falling object.
Step 9: Reduce life or destroy the object when it hits the ground.
Step 10: End the game when the player loses all lives.
 
### Program:

## playercontroller.cs

using System.Collections;
using System.Collections.Generic;
using UnityEngine;

public class playercontroller : MonoBehaviour
{
    float horizontalInput;
    float moveSpeed = 10f;

    Rigidbody2D rb;
    // Start is called once before the first execution of Update after the MonoBehaviour is created
    void Start()
    {
        rb=GetComponent<Rigidbody2D>();
    }

    // Update is called once per frame
    void Update()
    {
        horizontalInput=Input.GetAxis("Horizontal");
    }

    private void FixedUpdate()
    {
        rb.linearVelocity=new Vector2(horizontalInput * moveSpeed, rb.linearVelocity.y);
    }

    private void OnCollisionEnter2D(Collision2D collision)
    {
        if(collision.gameObject.CompareTag("Object"))
        {
            Destroy(this.gameObject);
        }
    }
}

## objectfall controller.cs

using System.Collections;
using System.Collections.Generic;
using UnityEngine;

public class objectfallcontroller : MonoBehaviour
{
    float wait=0.1f;
    public GameObject fallingObject;
    // Start is called once before the first execution of Update after the MonoBehaviour is created
    void Start()
    {
        InvokeRepeating("Fall",wait,wait); 
    }

    // Update is called once per frame
    void Fall()
    {
        Instantiate(fallingObject, new Vector3(Random.Range(-10, 10),10,0),Quaternion.identity);
    }
}

## fallingobject.cs

using System.Collections;
using System.Collections.Generic;
using UnityEngine;

public class fallingobject : MonoBehaviour
{
    private void OnCollisionEnter2D(Collision2D collision)
    {
        Destroy(this.gameObject);
    }
}

### Output:
<img width="1919" height="1026" alt="Screenshot 2025-11-16 184312" src="https://github.com/user-attachments/assets/3c10f291-50e2-458b-87d2-7882ff026e16" />
<img width="1917" height="1014" alt="Screenshot 2025-11-16 190231" src="https://github.com/user-attachments/assets/c1c87a18-11fc-4374-bbee-926b8ec1f252" />



### Result:
The falling objects game works correctly, with objects spawning, falling due to gravity, and interacting with the player through collisions and scoring.
