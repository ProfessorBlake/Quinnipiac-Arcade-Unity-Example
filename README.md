# 🕹️Quinnipiac Arcade
Unity Example Project

A Unity project template for interfacing with Quinnipiac's Arcade Machine.

---
# ⌨️ Input
This example project has the InputManager mapped out for easy support of the QU Arcade Machine's unique input. Each Joystick and 3 Button set is mapped to a player ID between 1 and 4.

To listen for input, the example project creates an "input prefix" for each player. This is mapped to the input listed in the Input Manager. Example:
```
[SerializeField] private int playerID = 1;

private string inputPrefix;

private void Start()
{
	inputPrefix = "P" + playerID;
}

private void Update()
{
  Vector2 playerInput = new Vector3(
		Input.GetAxisRaw(inputPrefix + "Horizontal"),
		Input.GetAxisRaw(inputPrefix + "Vertical")
		);

}
```


> [!TIP]
> If you're ready to test your game on the arcade machine just ask Professor Blake to install it!
