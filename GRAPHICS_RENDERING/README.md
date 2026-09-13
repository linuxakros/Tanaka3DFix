# Graphics Rendering

The game can use two different 3D rendering modes:

- **Direct3D HAL**
- **Open Media Toolkit Software**

On modern systems, the Direct3D HAL renderer can cause graphical issues or crashes.

For example, with Intel graphics driver **32.0.101.7088**, the game crashed in `igc32.dll` with exception `0xC0000005` when entering race mode with the Direct3D HAL renderer.

With an older Intel driver, Direct3D HAL did not crash, but graphical flickering was observed. Switching to **Open Media Toolkit Software** eliminated the flickering and avoided the `igc32.dll` crash.

## Recommended setting

The included `prefs.omt` file already has **Open Media Toolkit Software** selected.

It can be used as a ready-made configuration if the Direct3D HAL renderer causes problems.

## Changing the renderer

The renderer can also be changed directly from the game:

1. Start `Tanaka.exe`.
2. Open **Settings**.
3. Open **Graphics**.
4. Select **Set Video Mode and 3D Card...**
5. This page may take a long time to respond or appear to lag. Be patient and do not force-close the game.
6. Choose the desired 3D renderer.
7. Select the video mode and other graphics options.
8. Validate the changes by clicking **Exit**.

For better compatibility on modern systems, **Open Media Toolkit Software** can be used instead of the Direct3D HAL renderer.

## Error example

With a recent Intel graphics driver, the Direct3D HAL renderer caused:

```text
igc32.dll - Exception 0xC0000005
```

With an older driver, the observed problem was:

```text
Graphical flickering
```

Switching to **Open Media Toolkit Software** resolved both issues in the tested cases.
