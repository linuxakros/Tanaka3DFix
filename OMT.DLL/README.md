# OMT.dll Fix

Fix for the original **Open Media Toolkit (`OMT.dll`)** used by *Tanaka 3D*.

## Purpose

The original OMT drawing code can crash during text input with **OS error (87)**.
The crash comes from two separate error checks around two consecutive drawing operations. This fix bypasses both fatal error branches while keeping the normal operations intact.

## Installation

There are three ways to apply this fix.

### Method 1 - Hex editor

Modify the two locations in the original `OMT.dll`:

| File offset | Original | Fixed |
|---|---|---|
| `0x38850D` | `0F 85 16 01 00 00` | `E9 17 01 00 00 90` |
| `0x388638` | `0F 85 15 01 00 00` | `E9 16 01 00 00 90` |

Make a backup of the original DLL before editing.

### Method 2 - Apply the patch with Patcheur

Use [Patcheur](https://github.com/linuxakros/Patcheur/releases) to apply `OMT.dll.patch.bz2`.

Example:

```text
Patcher64.exe -p OMT.dll OMT.dll.patch.bz2
```

Make a backup of the original DLL before applying the patch.

### Method 3 - Download the patched DLL

A pre-patched `OMT.dll` is available in the Tanaka3DFix release.

Replace the original `OMT.dll` with the patched version.

Make a backup of the original DLL before replacing it.

## Fixes

### First error check

**File offset:** `0x38850D`

```text
Original: 0F 85 16 01 00 00
Fixed:    E9 17 01 00 00 90
```

This bypasses the first error-handling block.

### Second error check

**File offset:** `0x388638`

```text
Original: 0F 85 15 01 00 00
Fixed:    E9 16 01 00 00 90
```

This bypasses the second error-handling block.

These are two distinct error checks. The first fix must not jump directly to the end of the second block, because the second drawing operation and normal processing are located between the two checks.

## Original error message

The original `TanakaDebugInfo.txt` log reports:

```text
OMT Exception: OS error (87). File: \\MOTHERSHIP\DEPOT VERT\yves\Work\SharedSources\OMT Classes\OS_Support\MSWindows\Graphics\Drawings\OMediaWinDrawPort.cpp. Line: 282.
```

This message is included to help users find this fix when searching for the same error.

## SHA-256

Original:

```text
6712063B54827791E89462E106F8BA29A403AD5ED925CB3467C91FD58CAD78D9
```

Fixed:

```text
EAE2264F37165A0A92B9E91369004B642E61251A219C2594C106446C54B44D50
```

## Compatibility

The fixed DLL has been tested and works on **Windows 11 64-bit**.

## Scope

This fix addresses the **OS error (87) drawing crash** in OMT.dll. It does not modify the game's graphics renderer.
