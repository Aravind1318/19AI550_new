# Ex.No: 3  Basic movements in Unity 
### DATE: 02/02/2026                                                                       
### REGISTER NUMBER : 212224240015
### AIM: 
 To learn the basic movements translation,scaling and rotation of game objects through code.
### Procedure:
1. Setup the Scene
2. Open Unity and create a 3D Scene.
3. Add three objects:Cube → Rename to Object1 (for movement),Sphere → Rename to Object2 (for rotation).Capsule → Rename to Object3 (for scaling).
4. Add the Script,Create a C# Script → Name it TransformOperations.cs.
5. Write the code for translation,scaling and rotation,save and close the script
6. Save the script
7. Select any empty GameObject (or create one: GameObject → Create Empty).
8. Attach the TransformOperations script to it.
9. In the Inspector, assign Object1 → Drag the Cube,Object2 → Drag the Sphere.Object3 → Drag the Capsule.
10. Run the Scene Press Play ▶️ in Unity
11. Stop the program.
### Program 
```
using UnityEngine;

public class TransformOperations : MonoBehaviour
{
    public Transform object1; // Object for translation
    public Transform object2; // Object for rotation
    public Transform object3; // Object for scaling

    public float moveSpeed = 2f;
    public float rotateSpeed = 50f;
    public float scaleSpeed = 0.5f;

    void Update()
    {
        // TRANSLATION (Move Object1 along X-axis)
        if (object1 != null)
        {
            object1.Translate(Vector3.right * moveSpeed * Time.deltaTime);
        }

        // ROTATION (Rotate Object2 around Y-axis)
        if (object2 != null)
        {
            object2.Rotate(Vector3.up * rotateSpeed * Time.deltaTime);
        }

        // SCALING (Scale Object3 up and down)
        if (object3 != null)
        {
            float scaleChange = Mathf.PingPong(Time.time * scaleSpeed, 1f) + 0.5f;
            object3.localScale = new Vector3(scaleChange, scaleChange, scaleChange);
        }
    }
}

```
### Output:

<img width="1919" height="1199" alt="image" src="https://github.com/user-attachments/assets/cbe0ff9c-3057-49df-baae-1e11e7134807" />

### Result:
Thus the basic movement is learned through scripting


