# Tanaka3DFix

Fixes and workarounds for *Tanaka 3D* on Windows. Works on **Windows 11 64-bit**.

## Available fixes

### OMT.dll

Fix for the original **Open Media Toolkit (`OMT.dll`)** used by *Tanaka 3D*.

The original OMT drawing code can crash during text input with **OS error (87)**.

See [`OMT.DLL/`](OMT.DLL/) for the technical details and the available patch.

### Graphics Rendering

On modern systems, the **Direct3D HAL** renderer can cause graphical issues or crashes.

For example, with Intel graphics driver **32.0.101.7088**, the game crashed in `igc32.dll` with exception `0xC0000005` when entering race mode with the Direct3D HAL renderer.

Switching to **Open Media Toolkit Software** eliminated the flickering and avoided the `igc32.dll` crash.

See [`GRAPHICS_RENDERING/`](GRAPHICS_RENDERING/) for details.

### Demo → Evaluation Copy

The Windows Demo can be changed to the **Evaluation Copy** by replacing its `resources.omt` with the `resources.omt` from the Mac version.

In other words:

1. Obtain the Windows Demo.
2. Obtain the Mac version.
3. Copy the Mac `resources.omt`.
4. Replace the Windows Demo `resources.omt` with it.

This changes the Windows version from **Demo** to **Evaluation Copy**.

## Known downloads

### Windows Demo

[Internet Archive - TANAKA.zip](https://archive.org/download/TANAKA_201402/TANAKA.zip)

### Evaluation Copy

[MediaFire - Tanaka (rare).zip](https://www.mediafire.com/file/ngnznzdutdz/Tanaka+%28rare%29.zip)

[MyAbandonware - Tanaka 3D](https://www.myabandonware.com/game/tanaka-3d-10og)
