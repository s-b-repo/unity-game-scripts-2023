# unity-game-scripts-2023

A grab-bag of loose Unity C# snippets — drop one into a Unity project
as a `MonoBehaviour` and attach it to the right GameObject. Not a
Unity project itself (no `Assets/`, `ProjectSettings/`, `.unity`
scenes), just source files.

## Snippet index

| File | What it is | Attach to |
|------|------------|-----------|
| `advanced player controler sliding running force right click.cs` | Rigidbody-based player controller with slide (LShift+Q), run, and right-click push force. | Player |
| `bubly flame thrower.cs` | On F: emit a bubble particle system, add forward impulse, and play a song. Toy weapon. | Player / weapon holder |
| `double jump.cs` | Two extra jumps until landed. Uses `Rigidbody.velocity` and legacy `CharacterController.isGrounded`. | Player |
| `even  weirder physics.cs` | Every FixedUpdate: random force, torque, and explosion force at self. Chaos toy. | Any Rigidbody |
| `float in water.cs` | When a Player-tagged Collider enters the trigger, the object floats to `floatHeight`. | Water/lift volume |
| `gun respwan advanced.cs` | Player controller with a `List<Gun>` inventory, UI text update, and gun-swap. | Player |
| `gun respwan death message script.cs` | Displays a death-message UI. | UI canvas |
| `jetpack script.cs` | Left-shift adds upward force while holding, with a fuel gauge. | Player |
| `open close door.cs` | Rotate a hinge on trigger enter/exit. | Door pivot |
| `random gun affect list.cs` | Rolls a random gun effect from a list on Fire. | Weapon |
| `random gun affects script.cs` | Applies a single random affect to the fired projectile. | Weapon |
| `weird physics affects .cs` | Similar to *even weirder physics* — random per-frame forces. | Any Rigidbody |
| `script that plays a sound when an object moves` | On `Rigidbody.velocity.magnitude > threshold`, plays an AudioClip. (No `.cs` extension — rename before importing.) | Any Rigidbody |
| ~~`a gun that crashes unity players.cs`~~ | **Not a game script — see warning below.** | — |

## ⚠️ Warning: `a gun that crashes unity players.cs`

This file is **not** a Unity game script. It's a UDP flood tool
wrapped in a `MonoBehaviour`: `while (true) { socket.SendTo(packet,
endpoint); }` against an arbitrary IP/port from the `Fire()` method.
Deploying it against any system you don't own or have written
authorization to test is a denial-of-service attack — a criminal act
in most jurisdictions and a violation of Unity's Long Term Services
Agreement.

**Recommendation:** delete this file from the repo, or archive the
whole repo on GitHub, or replace this file's contents with a comment
explaining the history. It's left in place here only because the
current refresh pass avoids removing files unilaterally.

## Compatibility notes

- Most snippets target the **legacy Input Manager** (`Input.GetKey`,
  `Input.GetKeyDown`). If your project uses Unity's new Input System
  package, they'll need small ports.
- `Rigidbody.velocity` is **deprecated in Unity 6**; rename to
  `linearVelocity`.
- Lowercase `rigidbody` (implicit `Component.rigidbody` accessor) was
  removed in Unity 5. A couple of files still use it and will not
  compile — the fix is `GetComponent<Rigidbody>()`.
- Several files start with a natural-language prompt as a `#` comment
  (from the original AI-generation process). C# treats `#` as a
  preprocessor directive prefix, so those first lines usually parse as
  invalid directives — strip them before compiling.
- Filename typos preserved as-is: "respwan" (should be respawn),
  "bubly" (bubbly), "affects" (effects), "even  weirder" (double
  space).

## License

MIT — see [LICENSE](LICENSE).
