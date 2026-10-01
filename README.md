# N0M4D's 3D Controller Overlay

A transparent, animated 3D controller overlay for OBS Studio on Windows.

Show button presses, stick movement, trigger pressure, and supported battery information while you play. Arrange two independent camera views using the included visual editor.

## Features

- Coloured ABXY highlights and physical button movement.
- Animated sticks, bumpers, triggers, and D-pad.
- Directional glow rings on the thumbsticks.
- Trigger rings that fill with pressure.
- Direction-specific D-pad highlights.
- Battery indicators and charging animations when reported by the device.
- Connection-sensitive Xbox logo illumination.
- Smooth dimming when the selected controller disconnects.
- Separate rear and front camera views with unrestricted rotation.
- Controller selection and Xbox, PS4, or PS5 input labels.
- Optional input readout.
- Local settings storage and transparent OBS output.

## Requirements

- Windows 10 or 11, 64-bit.
- OBS Studio.
- A WebGL-capable browser for the editor.
- Windows PowerShell.
- A supported controller.

The portable package includes its runtimes and graphics libraries. You do not need to install Node.js, .NET, Blender, or VS Code. Internet access is not required during normal use.

## Installation

1. Download the portable Windows ZIP from this repository’s **[Releases](https://github.com/N0M4Dcode/N0M4D-s-3D-Controller-Overlay/releases)** section.
2. Extract the **entire ZIP** into a writable folder, such as `Documents\Nomads3DCOverlay`.
3. Run `Nomads3DCOverlay.exe`.
4. Click **Open controller studio**.

Keep the bundled files and folders together. Do not run the application directly from inside the ZIP.

## Set up your controller

1. Connect your controller to the PC.
2. Select it from the **Controller** dropdown.
3. Choose automatic, Xbox, PS4, or PS5 button labels.
4. Adjust the two camera views:
   - **Left-drag:** rotate.
   - **Right-drag:** reposition.
   - **Mouse wheel:** zoom.
5. Use the position and gap sliders to arrange the views.
6. Choose whether to show the input readout.
7. Click **Save & copy OBS link**.

PlayStation label profiles currently use the supplied Xbox-shaped model. Separate PS4 and PS5 models are not included yet. this will change as time goes on. as its an active project of mine.

## Add the overlay to OBS

1. In OBS, click **+** under **Sources**.
2. Choose **Browser**.
3. Paste the copied overlay URL.
4. Set:
   - **Width:** `620`
   - **Height:** `740`
5. Confirm, then position and resize the source in your scene.

The overlay background is transparent. No chroma-key filter is needed.

The studio’s copied URL contains a snapshot of your settings. After changing the layout, save again and replace that URL in OBS.

Alternatively, use:

```text
http://127.0.0.1:3210/?overlay
```

This address loads the latest saved settings whenever the Browser Source refreshes. The launcher’s **Copy OBS URL** button copies this address.

## Keep it running

Leave Nomads running while using the overlay.

Closing the launcher window keeps it running in the Windows system tray. To stop it completely, right-click its tray icon and choose **Quit**.

Input is read by a local Windows helper, so it does not depend on the editor browser having focus.

## Battery and connection indicators

| State | Indicator |
|---|---|
| Full battery | Three green segments |
| Medium battery | Two amber segments |
| Low or empty battery | Pulsing red segment |
| Wired connection reported | Blue pulse |
| Charging explicitly reported | Repeating fill animation |
| Battery information unavailable | Dim neutral ring |
| Controller disconnected | Logo and input rings off; model fades to 25% brightness |

Battery support depends on the controller, driver, and connection method. XInput reports coarse battery levels rather than an exact percentage.

Connecting a USB charging cable does not guarantee that charging information is exposed to Windows. A controller may continue sending input through its wireless dongle while charging.

## Controller support

- Standard XInput controllers.
- Native PS4 and PS5 input through SDL3.
- Xbox and PlayStation input labels.

PS5 hardware has not yet been tested. The standard XInput reader does not expose the Xbox guide button.

HOTAS devices, steering wheels, haptics, and touchpad movement are not implemented.

If a controller mapper exposes both a physical and virtual device, select the device you want in the editor. Reconnecting an SDL device may require selecting it again.

## Updating

1. Quit the running version from its tray icon.
2. Extract the new release into a separate folder.
3. To retain settings, copy `data/settings.json` from the old folder into the new folder’s `data` directory.
4. Launch the new version.

Do not run multiple versions at once.

## Troubleshooting

### The overlay does not load

Make sure Nomads is running and the entire ZIP was extracted. Confirm that your OBS URL starts with:

```text
http://127.0.0.1:3210/
```

### Port 3210 is already in use

Quit any previous Nomads instance or development server before launching the package.

### No controller input

Check the controller’s connection and operating mode, then select it in the editor. Review `launcher.log` in the application folder if the reader does not start.

### Settings do not save

Move the extracted application to a writable folder, such as Documents.

### Charging is not shown

The device may not report charging through its current connection. Wired mode and confirmed charging are treated separately.

### An old layout appears in OBS

A previously copied URL may contain the old layout. Copy a new link from the editor, or use the simple `?overlay` URL and refresh the Browser Source.

## Preview release status

Version 0.1.1 is an unsigned portable preview.

Startup, local assets, settings storage, and disconnect-fade checks have passed. Broader clean-PC, controller compatibility, and full OBS streaming tests are still needed.

## Credits

The controller model is based on **Xbox controller** by **wilsonR**:

https://sketchfab.com/3d-models/xbox-controller-a8d4bbaecf004885bfd68fe79b0c2077

Licensed under [CC BY 4.0](https://creativecommons.org/licenses/by/4.0/).

The model was modified in Blender for this project, including control separation, materials, and the battery ring. The original creator does not endorse this project.

Third-party components include Three.js, SDL3, Node.js, and Microsoft .NET. Their licence notices are included in the portable package’s `licenses` folder.

The model’s licence does not automatically apply to the application source code.

if you would like to support me. buy me a coffee or drop a follow on my YT

[BuyMeACoffee](https://buymeacoffee.com/n0m4d)
[Youtube](https://www.youtube.com/channel/UC51wCpcVe3cglUBtS6rZTPQ)
