# Hex Inception
## Information Sheet & User Guide

**Version:** 1.0.0  
**Product:** Hex Inception (AUv2/VST3)  
**Platform:** macOS  
**Primary use:** Supplying a multichannel hexaphonic audio source to a hosted multichannel plug-in inside a DAW. (maximum: 8 channels)

---

## 1. Overview

Hex Inception is a macOS plug-in designed for **eight-channel hexaphonic audio workflows**.

It solves a specific routing problem: a hardware device may expose all of its hexaphonic channels correctly to macOS, while the DAW does not provide a practical eight-channel input path to the plug-in that needs them.

Hex Inception acquires or receives the eight-channel source itself, passes that source to a compatible multichannel plug-in hosted inside Hex Inception, and returns the hosted processor's output to the DAW.

Typical signal paths are:

**Live:**  
`Hex audio device → Hex Inception → hosted plug-in → DAW`

**Reamp/Resynth:**  
`DAW → Hex Inception 8ch → Hex Inception → hosted plug-in → DAW`

A common use case is feeding a BOSS/Roland-style hexaphonic USB source to a processor such as **MIDI Guitar 3 Hex**.

In Live mode, Hex Inception works with any compatible multichannel Core Audio device; it is not limited to specific BOSS/Roland hardware.

---

## 2. What Problem It Solves

Hexaphonic systems expose six or more audio channels over USB:

- 1 or more direct / DI channels
- 6 × individual string channels

BOSS devices expose 8 channels.

But even if an audio device provides multiple channels, the DAW in use may expose only stereo or another unsuitable plug-in input layout. This can be a showstopper for certain plugins.

Hex Inception bypasses that restriction by providing its own eight-channel source path to the plug-in hosted directly inside it.

This allows an eight-input processor to operate without dependence on the DAW being able to feed that processor all hardware input channels directly.

---

## 3. Requirements

### **Live** workflow

You need:

1. A Mac running a supported macOS version (macOS 11 Big Sur or higher).
2. Hex Inception installed in AUv2 or VST3 format.
3. A physical Core Audio input device with at least six input channels.
4. A compatible multichannel plug-in to host inside Hex Inception.

### **Reamp/Resynth** workflow

You also need:

5. The **Hex Inception 8ch** virtual audio device installed and available to macOS. This is included in the installation package.

Selecting Reamp/Resynth tells Hex Inception to listen to this virtual audio device, as opposed to the direct USB device input from Live mode. 

Note: If the hosted processor generates MIDI, configure an appropriate MIDI destination in Hex Inception and the receiving DAW or application.

---

## 4. **Live** and **Reamp/Resynth**

The source mode is selected with the **Live | Reamp/Resynth** control.

### Live

Use **Live** when the source is a physical audio device.

Signal flow:

**Physical hex device → Hex Inception → hosted plug-in → DAW**

Typical uses include:

- playing a hex guitar in real time
- live MIDI Guitar 3 Hex tracking
- hexaphonic audio processing
- recording the hosted processor's output (bussed to a new audio track)
- generating MIDI for a live performance

In Live mode, Hex Inception lets you select the physical source device and physical buffer.

### Reamp/Resynth

Use **Reamp/Resynth** when a multichannel performance has already been recorded and you want to process it again.

Signal flow:

**DAW playback → Hex Inception 8ch → Hex Inception → hosted plug-in → DAW**

Typical uses include:

- re-tracking MIDI from a recorded hex performance
- trying different tracking settings
- changing the hosted processor after recording
- resynthesising a performance without replaying it
- comparing processor settings using the same source material

In Reamp/Resynth mode, the source is **Hex Inception 8ch**, so physical device selection is not used.

---

## 5. The Eight-Channel Format

Hex Inception is deliberately built around an **eight-channel source**.

A common layout is:

| Channel | Typical source |
|---|---|
| 1 | DI / normal pickup L |
| 2 | DI / normal pickup R |
| 3 | Hex string channel |
| 4 | Hex string channel |
| 5 | Hex string channel |
| 6 | Hex string channel |
| 7 | Hex string channel |
| 8 | Hex string channel |

The exact string order is determined by the source device.

Hex Inception does not assume that every manufacturer's labels or string order are identical. Use the **Routing** section and the channel meters to verify what is reaching each hosted input.

### Live-device eligibility

The Live device selector is intended for devices that can provide the required multichannel source.

Devices with fewer than **six input channels** are not presented as normal Live-source choices.

---

## 6. Supported Sample Rates

Hex Inception supports:

- 44.1 kHz
- 48 kHz
- 88.2 kHz
- 96 kHz

**192 kHz is not supported.**

48 kHz is the normal default for the Hex Inception 8ch virtual device, but a different supported rate may be required by the physical device or DAW project.

The physical device, DAW and Hex Inception workflow must operate at compatible sample rates.

---

## 7. Physical Buffer Sizes

The Live buffer selector contains:

- 16 frames
- 32 frames
- 64 frames
- 128 frames
- 256 frames
- 512 frames

A fresh/default Hex Inception state selects:

**128 frames**

If the selected physical device cannot support one of the available choices, that choice may remain visible but unavailable.

Hex Inception distinguishes between the buffer you requested and the buffer actually accepted by the physical device.

### Choosing a buffer

| Buffer | General use |
|---|---|
| 16–32 | Minimum-latency operation|
| 64 | Low-latency performance |
| 128 | Default starting point |
| 256 | Heavier sessions or additional safety margin |
| 512 | Latency-insensitive processing or troubleshooting |

Use the smallest buffer that remains completely reliable on the actual hardware and session. 
>Note: Lower framerates are provided for user interest but 64 it is a recommended "sensible" setting.

---

## 8. Basic Setup — Live

### 1. Connect the source device

Connect and power on the hex-capable audio device. Confirm that macOS can see the device in the Audio-MIDI Setup environment.

### 2. Insert Hex Inception

Open the DAW project and insert **Hex Inception** on the track where you want to receive the hosted processor's output.

### 3. Select Live

Select:

**Live**

in the **Live | Reamp/Resynth** control.

### 4. Select the device

Choose the required physical source from the device selector. 

Devices with five or less inputs do not appear here.

### 5. Select the buffer

Choose the required physical buffer.

For a first test, **128 frames** is a sensible starting point. 

### 6. Select the hosted plug-in

Hex Inception must be stopped before changing the hosted plug-in.

Use the plug-in selector in the **Hosted Plug-in** section to choose a compatible multichannel plugin.

When a processor is loaded, the Hosted Plug-in section identifies it and shows information such as its manufacturer, format, input/output count and running state.

A saved project/session restores its hosted plug-in and hosted state when that plug-in is still available.

Note: a plugin, once shown to load correctly, is flagged with compatibility status in the plug-in list. 

### 7. Check Routing

Review the **Routing** section before starting audio.

Do not assume that a manufacturer's channel labels necessarily match the order expected by the hosted processor.

### 8. Start input

Use **Start Audio Input**.

When reception is running, the primary status changes to:

**Receiving**

When it is not running, the status is:

**Stopped**

### 9. Verify all channels

Play each string or source independently.

Confirm that:

- the expected source meter responds
- the expected hosted input responds
- no string appears on an unintended input
- no required channel is missing
- the hosted processor produces the expected output

Do this before an important recording session, especially when using a new device or hosted processor.

---

## 9. Basic Setup — Reamp/Resynth

Reamp/Resynth processes an already-recorded multichannel performance.

### 1. Preserve the eight discrete channels

The original hex source must remain discrete.

Do not collapse the six string channels (and DI guitar signal/s) to stereo if you intend to reprocess them later.

### 2. Send the recording to Hex Inception 8ch

In the DAW, route the eight recorded channels to the corresponding outputs of:

**Hex Inception 8ch**

Maintain the intended eight-channel order.

### 3. Select Reamp/Resynth

In Hex Inception, select:

**Reamp/Resynth**

The physical Live-device selector is not used in this mode.

### 4. Select or recall the hosted processor

While stopped, use the **Hosted Plug-in** selector to choose a different processor.

If the DAW project already contains a saved Hex Inception state and the processor is installed, Hex Inception should recall the saved processor and its state.

### 5. Review Routing

Check the **Routing** section and confirm that the eight returned DAW channels correspond to the hosted processor's expected inputs.

### 6. Start processing

Start the Hex Inception input path and play the DAW session.

The recorded eight-channel performance can now be presented to the hosted processor as a reprocessing source.

Record or monitor the resulting audio and/or MIDI in the DAW.

---

## 10. Hosted Plug-in

Hex Inception hosts one processor that receives the eight-channel source.

The **Hosted Plug-in** section is used both to choose the processor and to show the currently loaded processor.

When loaded, the interface provides a compact summary such as:

- plug-in name
- manufacturer and format
- input and output count
- running state

For example:

**PatchWork · Blue Cat Audio · VST3**
**8 inputs · 4 outputs · Running**

(Note: when using PatchWork, be sure to select its 8-in/4-out audio config under its I/O button). 

### Changing the hosted processor

Stop Hex Inception before choosing another hosted plug-in.

### Project recall

Hex Inception saves the hosted processor identity and hosted state with the project/session.

When reopening the project, the saved processor should be restored automatically when it remains installed and available.

### If the saved plug-in is unavailable

If Hex Inception reports that no plug-in is loaded or that the saved processor cannot be restored:

- stop audio input
- confirm the required AU/VST3 is installed
- select an available compatible processor
- verify Routing before restarting audio

A missing processor should not be silently replaced with an unrelated one.

---

## 11. Routing

The **Routing** section describes how the eight source channels are presented to the hosted processor.

The source is determined by the selected mode:

- **Live:** the selected physical input device
- **Reamp/Resynth:** Hex Inception 8ch

### Verify routing by signal

When using a new source device or processor:

1. Play or send one source channel at a time.
2. Watch the source/channel meters.
3. Observe which hosted input receives it.
4. Check the corresponding entry in Routing.
5. Repeat until all eight channels are accounted for.

---

## 12. Changing the Live Input Device

To change the physical source:

1. Stop audio input.
2. Select **Live**.
3. Choose the replacement device.
4. Choose the required buffer.
5. Review Routing.
6. Start audio input again.
7. Verify all eight channels.

Device and buffer changes should be made while Hex Inception is stopped.

After changing hardware, do not assume that the previous manufacturer's channel order applies to the replacement device.

---

## 13. Operating Status

### Receiving

**Receiving** means Hex Inception is actively receiving the selected eight-channel source.

### Stopped

**Stopped** means the external/source input path is not currently running.

Some configuration changes require Hex Inception to be stopped. Follow the guidance shown in the interface if a selector is unavailable while Receiving.

### No Plug-in Loaded

If no hosted processor is selected, Hex Inception reports that state rather than pretending processing is active.

Audio reception, channel information and routing can remain useful for configuration and diagnosis, but there is no hosted processing result until a compatible processor is loaded.

---

## 14. Channel Meters

Use the channel meters to answer:

- Is the source reaching Hex Inception?
- Are all eight channels present?
- Does each string/source appear on the expected source channel?
- Is one channel unexpectedly silent?
- Is the channel order different from what the processor expects?

For a new device, excite one source at a time.

For a six-string hex source, play each string separately and note which of the channels responds.

---

## 15. MIDI Output

Some hosted hexaphonic processors generate MIDI.

Hex Inception can route generated MIDI using its per-instance MIDI output options.

Depending on the configured mode, MIDI output can be:

- **Off**
- sent through Hex Inception's **built-in virtual MIDI source**
- sent to a selected **external MIDI destination**

Only one Hex Inception instance can own the built-in virtual MIDI source at a time. External MIDI destinations can be shared by multiple Hex Inception instances where the destination itself permits it.

When diagnosing MIDI, check the signal path in this order:

1. Is Hex Inception receiving the correct audio?
2. Is the hosted processor receiving the correct eight-channel mapping?
3. Is the hosted processor generating MIDI?
4. Is Hex Inception's MIDI output configured correctly?
5. Is the receiving DAW or application listening to the selected MIDI destination?

Before troubleshooting MIDI routing, make sure that the hosted plug-in is receiving audio on the correct channels.

---

## 16. Status Details and Diagnostics

Refer to **Status Details** (at the top of the UI) and **Diagnostics** (accessible under Support) if you ever need to investigate a problem.

Depending on the current state, diagnostics can help confirm:

- selected source mode
- selected physical device
- requested buffer
- actual accepted device buffer
- sample rate
- channel activity
- hosted processor state
- routing state
- MIDI output state

If something stops working, inspect the status information before changing several settings at once.

---

## 17. Troubleshooting

### The physical device does not appear

Check that:

- the device is connected and powered
- macOS can see it
- it exposes at least six input channels
- Hex Inception is in **Live** mode

Hex Inception intentionally does not fill the Live selector with devices that cannot provide the required multichannel source.

### Start Audio Input does not produce audio

Check:

- the correct source mode is selected
- the correct Live device is selected, if using Live
- the required buffer is available
- the device and project are using compatible sample rates
- the main status changes to **Receiving**
- the input meters show activity

### No hosted processor is active

Stop Hex Inception and use the **Hosted Plug-in** selector to choose a compatible processor.

If the project previously used a plug-in that is no longer installed, reinstall it or choose another compatible processor explicitly.

### A plug-in is loaded but does not receive the expected signal

Check:

- its input count/layout
- the Routing section
- the channel meters
- the physical device's actual channel order
- whether you are using the correct source mode

A plug-in can load successfully while still being unsuitable for the required eight-channel input layout.

### Only some strings are present

Possible causes include:

- the hardware is not supplying all expected channels
- the source channel order differs from what you expected
- one DAW return channel is missing in Reamp/Resynth
- the hosted plug-in is not exposing the required eight-input layout
- the Routing section does not match the intended signal order

### Strings appear on unexpected inputs

Identify the actual source order with the meters, then compare it with the Routing section and the hosted processor's expected inputs.

Avoid destructively changing the original recording until you understand the actual channel order.

### Reamp/Resynth is silent

Confirm that:

- **Hex Inception 8ch** is installed
- Hex Inception is set to **Reamp/Resynth**
- the DAW is sending audio to Hex Inception 8ch
- all required output channels are being sent
- the eight-channel order is correct
- Hex Inception shows **Receiving**
- a compatible hosted processor is loaded

### Crackles or instability

Try a larger physical buffer in Live mode. **32 → 64 → 128 → 256**

Do not treat the smallest selectable buffer as automatically preferable!

### A 192 kHz session does not work

192 kHz is not supported.

Use one of:

**44.1 / 48 / 88.2 / 96 kHz**

---

## 18. Recommended First-Time Test

1. Create a new DAW project.
2. Insert Hex Inception.
3. Select **Live**.
4. Select the physical multichannel source.
5. Use **128 frames** initially.
6. Select the intended hosted processor while stopped.
7. Review Routing.
8. Press **Start Audio Input**.
9. Confirm the status shows **Receiving**.
10. Test every string/source independently.
11. Confirm all audio channels are accounted for.
12. Confirm the hosted processor plug-in produces the expected result.
13. Save the project.

This gives you a known-good reference configuration.

---

## 19. Project Recall

Hex Inception is designed to restore the important state of a saved DAW project.

That state includes the selected source configuration, explicit buffer choice, hosted processor and routing state.

The selected explicit buffer is preserved rather than being returned to 128 every time the project is opened.

The hosted plug-in and its state are also restored automatically when possible.

If required hardware or a hosted plug-in is missing, Hex Inception should report the unresolved condition rather than silently choosing an unrelated replacement.

Always check the visible status after reopening a project before recording.

---

## 20. Practical Workflow Advice

### Live performance

Prioritise:

1. correct source device
2. correct multichannel signal
3. correct hosted processor
4. correct routing
5. stable buffer
6. lowest practical latency only after the above are reliable

### Recording

Where possible, preserve the original discrete hex channels.

This gives you the option to use **Reamp/Resynth** later rather than permanently committing to the tracking or synthesis result generated during the original performance.

### Reprocessing

Keep the recorded source channels intact.

Use Hex Inception's source/routing workflow to present them correctly to the hosted processor rather than destructively altering the original performance files.

---

## 21. What Hex Inception Is Not

Hex Inception is not intended to be:

- a general-purpose audio-interface control panel
- a replacement for the DAW mixer
- a universal arbitrary-channel patchbay
- a conventional stereo effect
- a 192 kHz processing system
- a BOSS-device-specific manager

Its purpose is narrower:

> **Provide a reliable multichannel hexaphonic source to a hosted processor when the surrounding DAW cannot conveniently provide that input itself.**

---

## 22. Quick Reference

### Live

**Physical hex device → Hex Inception → hosted processor → DAW**

1. Insert Hex Inception.
2. Select **Live**.
3. Select the physical device.
4. Select buffer.
5. Select or confirm the Hosted Plug-in while stopped.
6. Review Routing.
7. Press **Start Audio Input**.
8. Confirm **Receiving**.
9. Play or record.

### Reamp / Resynth

**DAW → Hex Inception 8ch → Hex Inception → hosted processor → DAW**

1. Preserve the eight discrete recorded channels.
2. Route them to **Hex Inception 8ch**.
3. Select **Reamp / Resynth**.
4. Select or confirm the Hosted Plug-in while stopped.
5. Review Routing.
6. Start the input path.
7. Confirm **Receiving**.
8. Process or record the result.

### Supported sample rates

**44.1 / 48 / 88.2 / 96 kHz**

### Live buffer choices

**16 / 32 / 64 / 128 / 256 / 512 frames**

Fresh/default selection:

**128 frames**

---

## 23. Contacting Support

Click the **Support** button to get help. Please include the following info in your email:

- macOS version
- DAW and version
- Hex Inception version
- Hex Inception plug-in format
- hosted plug-in name, format and version
- Live or Reamp/Resynth mode
- physical source device, if using Live mode
- sample rate
- requested buffer
- actual accepted buffer, if relevant
- MIDI output mode and destination, if relevant
- which exact channels are affected
- whether Hex Inception shows **Receiving** or **Stopped**
- whether the problem occurs in a new empty project
- relevant Status Details or Diagnostics

---

## 24. Summary

Hex Inception provides a focused eight-channel audio path for hexaphonic processing on macOS.

Use **Live** to receive an eligible physical eight-channel device directly.

Use **Reamp / Resynth** to receive a previously recorded eight-channel performance through **Hex Inception 8ch**.

Select the hosted processor while stopped, verify the Routing section, start the input path, and confirm **Receiving**.

The basic principle is:

**Get all source channels to the intended hosted processor inputs reliably, without depending on the DAW to provide that multichannel plug-in input itself.**
