# 🕹️Quinnipiac Arcade
Unity Example Project

A Unity project template for interfacing with Quinnipiac's Arcade Machine.

---
## ⌨️[Input](#input)  •  ⏸️[Pause Menu](#pause-menu)  •  📦[Deploying Your Game](#deploying-your-game)

# Input
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

---

# Pause Menu
The arcade machine **Start** button can be used to open a pause menu in your game. The example project has a Pause Manager prefab that can be used to freeze gameplay and display a menu for selecting options or exiting the game. 

To add support for the Pause Menu, simply add the **Pause Controller** prefab to your scene. The PauseManager script will listen for the "Space" input, which is bound to the "Start" button on the arcade machine. It will then allow any player to navigate the menu and select options from it.
> [!NOTE]
> You can exit your game at any time using `Application.Quit();` in a Unity script. When your game closes, the Launcher will be displayed.

---

# Deploying Your Game
There are a few steps needed to deploy your game to the arcade machine and have it properly interface with the Launcher.

## ✅ Name Your Executable
The name of your game's executable file should match the name of the games folder. 
> If the folder for the game is `My New Game` then the executable should be `My New Game.exe`.

## ✅ info.txt
Inside the root directory for your game, you must include an `info.txt` file. It should contain the following info in the JSON format:
```
{
    "GameName": "Game Name",
    "Description": "Description of your game.",
    "Team":[
        "Professor Blake",
	"Ripley"
    ]
}
```
- GameName: The name of your game as displayed on the Launcher screen.
- Description: The description that should be shown when your game is highlighted on the Launcher screen.
- Team: A comma separated list of your team members.

## ✅ Launcher Capsule Art
The capsule art that is shown on the launcher should be **600px X 288px** and needs to be in a `Media` folder in the game folders root directory. The file name doesn't matter, ex: `My New Game/Media/myImage.png`

---

> [!TIP]
> If you're ready to test your game on the arcade machine just ask Professor Blake to install it!
