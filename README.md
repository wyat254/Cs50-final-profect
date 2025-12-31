# Cs50-final-profect

2D Tag Game in Godot
A simple 2D tag game built in Godot 4, featuring two players who can tag each other by overlapping their "TagArea" collision zones. The "it" player is visually indicated by a red color, and tagging swaps the status between players.

Features
Two-Player Gameplay: Player 1 and Player 2 with separate controls.
Tagging Mechanics: Overlap to tag the "it" player and swap roles.
Visual Feedback: Red color for the "it" player, white for others.
Movement and Actions: Walking, jumping (with double jump), and shooting.
Cooldown System: Prevents rapid re-tagging to avoid spam.
Debug Prints: Console output for collision detection and tagging events (can be removed for production).
Requirements
Godot 4.x
Basic understanding of Godot's scene tree and scripting.
Setup and Installation
Clone or Download: Download the project files and open in Godot.
Scene Structure: Ensure your main scene has two player nodes (e.g., "Player" for Player 1 and "Player2" for Player 2), each with the required children:
PlatformDetector (RayCast2D)
AnimationPlayer
ShootAnimation (Timer)
Sprite2D
Jump (AudioStreamPlayer2D)
Gun (custom node, assumed to have a shoot() method)
Camera (Camera2D)
TagArea (Area2D with collision shape)
Input Actions: Set up the following input actions in Project Settings > Input Map:
Player 1: jump, move_left, move_right, shoot
Player 2: jumpp2, moveleftp2, moverightp2, shootp2
Collision Layers: Ensure TagArea nodes are on the same collision layer/mask for detection.
Attach Scripts: Attach the provided scripts to the respective player nodes.
How to Play
Start: Player 1 starts as "it" (red). Player 2 is white.
Movement: Use controls to move and jump.
Tagging: Move into the other player's TagArea to tag them. The "it" status swaps, and colors update.
Cooldown: After tagging, the previous "it" player can't tag again for 1 second.
Win Condition: No explicit win—play until you decide!
Controls
Player 1:
Move Left/Right: move_left / move_right
Jump: jump
Shoot: shoot
Player 2:
Move Left/Right: moveleftp2 / moverightp2
Jump: jumpp2
Shoot: shootp2
Code Structure
Player 1 Script (Player.gd): Handles Player 1's logic, including tagging.
Player 2 Script (Player2.gd): Handles Player 2's logic, including tagging.
Key Functions:
_ready(): Initializes "it" status and connects signals.
_physics_process(): Handles movement, jumping, color updates, and cooldown.
_on_tag_area_entered(): Detects overlaps and performs tagging.
try_jump() and get_new_animation(): Support movement and visuals.
Variables:
is_it: Boolean for "it" status.
tag_cooldown: Prevents rapid tags.
Troubleshooting
No Collision Detected: Check TagArea collision layers/masks and ensure shapes are set.
Colors Not Changing: Verify is_it updates in console debug prints. If flags change but colors don't, check Sprite2D modulate.
One-Way Tagging: Ensure both players have the signal connected and cooldown is on the "it" player.
Debug Mode: Run with console open to see prints. Remove debug lines for final build.
Credits
Built with Godot Engine.
Inspired by classic tag games.
Special thanks to the user for iterating on the code!
Enjoy the game! If you have issues, check the Godot documentation or share console output for help. 🎮
