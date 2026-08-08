<img width="512" height="512" alt="HexInceptionIcon" src="https://github.com/user-attachments/assets/3848c4be-7b27-4c77-9cd9-d9626a9b1d49" />

# Hex Inception
## Information Sheet & User Guide

**Product:** Hex Inception (AUv2/VST3)
**Platform:** macOS  
**Primary use:** Supplying an eight-channel hexaphonic audio source to a hosted multichannel plug-in inside a DAW.

---

## 1. What Hex Inception Is

Hex Inception is a macOS plug-in designed for **eight-channel hexaphonic audio workflows**.

Its purpose is to solve a specific problem: a hardware device may expose all of its hexaphonic channels correctly to macOS, while the DAW does not provide a practical eight-channel input path to the plug-in that needs them.

Hex Inception acquires or receives the eight-channel source itself, passes that source to a multichannel plug-in hosted inside Hex Inception, and returns the hosted processor's output to the DAW.

A typical Live signal path is:

**Hex audio device → Hex Inception → hosted plug-in → DAW**

A typical Reamp / Resynth path is:

**DAW → Hex Inception 8ch → Hex Inception → hosted plug-in → DAW**

A common use case is feeding a BOSS/Roland-style hexaphonic USB source to a processor such as **MIDI Guitar 3 Hex**.

Hex Inception does not require device-specific BOSS awareness. In Live mode, it works from the capabilities reported by Core Audio.

---

## 2. What Problem It Solves

Many hexaphonic systems expose eight audio channels over USB:

- 2 × direct / DI channels
- 6 × individual string channels

The audio device may provide all eight channels, but a DAW may expose only stereo or another unsuitable plug-in input layout.

Hex Inception works around that restriction by providing its own eight-channel source path to the plug-in hosted inside it.

This allows an eight-input processor to operate without depending on the DAW being able to feed that processor eight hardware input channels directly.

---

## 3. Live and Reamp / Resynth

The source mode is selected with the:

**Live | Reamp / Resynth**

control.

### Live

Use **Live** when the source is a physical audio device.

Signal flow:

**Physical hex device → Hex Inception → hosted plug-in → DAW**

Typical uses include:

- playing a hex guitar in real time
- live MIDI Guitar 3 Hex tracking
- hexaphonic audio processing
- recording the hosted processor's result
- generating MIDI from a live performance

In Live mode, Hex Inception lets you select the physical source device and physical buffer.

### Reamp / Resynth

Use **Reamp / Resynth** when the eight-channel performance has already been recorded and you want to process it again.

Signal flow:

**DAW playback → Hex Inception 8ch → Hex Inception → hosted plug-in → DAW**

Typical uses include:

- re-tracking MIDI from a recorded hex performance
- trying different tracking settings
- changing the hosted processor after recording
- resynthesising a performance without replaying it
- comparing processor settings using the same source material

In Reamp / Resynth mode, the source is **Hex Inception 8ch**, so physical device selection is not used.

---

## 4. The Eight-Channel Format

Hex Inception is deliberately built around an **eight-channel source**.

A common device layout is:

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

Devices with fewer than **eight input channels** are not presented as normal Live-source choices.

This avoids filling the selector with stereo interfaces and other devices that cannot provide the complete Hex Inception signal path.

---

## 5. Sample Rates

Hex Inception's supported eight-channel workflow uses these sample rates:

- 44.1 kHz
- 48 kHz
- 88.2 kHz
- 96 kHz

**192 kHz is not supported.**

48 kHz is the normal default for the Hex Inception 8ch virtual device, but a different supported rate may be required by the physical device or DAW project.

The physical device, DAW and Hex Inception workflow must be operating at compatible rates.

---

## 6. Physical Buffer Sizes

The Live buffer selector contains these choices:

- 16 frames
- 32 frames
- 64 frames
- 128 frames
- 256 frames
- 512 frames

A fresh/default Hex Inception state selects:

**128 frames**

If the selected physical device cannot support one of the available choices, that choice may remain visible but unavailable.

Hex Inception distinguishes between the buffer you requested and the buffer actually accepted by the physical device. Diagnostic information should be treated as authoritative when checking the actual operating buffer.

### Choosing a buffer

Smaller buffers reduce device-side latency but place greater timing demands on the system.

A practical guide is:

| Buffer | General use |
|---|---|
| 16–32 | Minimum-latency operation where the hardware and session remain stable |
| 64 | Low-latency performance |
| 128 | Default starting point |
| 256 | Heavier sessions or additional safety margin |
| 512 | Latency-insensitive processing or troubleshooting |

Use the smallest buffer that remains completely reliable on the actual hardware and session.

---

## 7. Before You Start

For a Live workflow you need:

1. A Mac running a supported macOS version.
2. Hex Inception installed in the required plug-in format.
3. A physical Core Audio input device with at least eight input channels.
4. A compatible multichannel plug-in to host inside Hex Inception.

For Reamp / Resynth you additionally need:

5. The **Hex Inception 8ch** virtual audio device installed and available to macOS.

If the hosted processor produces MIDI, configure the required MIDI destination in the DAW or receiving application as appropriate.

---

## 8. Basic Setup — Live

### Step 1 — Connect the source device

Connect and power on the hex-capable audio device.

Confirm that macOS can see it before troubleshooting Hex Inception itself.

### Step 2 — Insert Hex Inception

Open the DAW project and insert **Hex Inception** on the track where you want to receive the hosted processor's output.

### Step 3 — Select Live

Select:

**Live**

in the **Live | Reamp / Resynth** control.

### Step 4 — Select the device

Choose the required physical source from the device selector.

Only suitable multichannel input devices are intended to appear here.

### Step 5 — Select the buffer

Choose the required physical buffer.

For a first test, **128 frames** is a sensible starting point.

### Step 6 — Select the hosted plug-in

Hex Inception must be stopped before changing the hosted processor.

Use the plug-in selector in the **Hosted Plug-in** section to choose the multichannel processor you want to use.

When a processor is loaded, the Hosted Plug-in section identifies it and shows information such as its manufacturer, format, input/output count and running state.

A saved project/session restores its hosted plug-in and hosted state when that plug-in is still available.

### Step 7 — Check the Routing section

Review the **Routing** section before starting audio.

The routing display represents the relationship between the eight source channels and the hosted plug-in's inputs.

Do not assume that a device manufacturer's channel labels necessarily match the order expected by the hosted processor.

### Step 8 — Start input

Use **Start Audio Input**.

When reception is running, the primary status changes to:

**Receiving**

When it is not running, the status is:

**Stopped**

### Step 9 — Verify all channels

Play each string or source independently.

Confirm that:

- the expected source meter responds
- the expected hosted input responds
- no string appears on an unintended input
- no required channel is missing
- the hosted processor produces the expected output

Do this before an important recording session, especially when using a new device or hosted processor.

---

## 9. Basic Setup — Reamp / Resynth

Reamp / Resynth processes an already-recorded eight-channel performance.

### Step 1 — Preserve the eight discrete channels

The original hex source must remain discrete.

Do not collapse the six string channels to stereo if you intend to reprocess them later.

### Step 2 — Send the recording to Hex Inception 8ch

In the DAW, route the eight recorded channels to the corresponding outputs of:

**Hex Inception 8ch**

Maintain the intended eight-channel order.

### Step 3 — Select Reamp / Resynth

In Hex Inception, select:

**Reamp / Resynth**

The physical Live-device selector is not used for this source mode.

### Step 4 — Select or recall the hosted processor

While stopped, use the **Hosted Plug-in** selector if you need to choose a different processor.

If the DAW project already contains a saved Hex Inception state and the processor is installed, Hex Inception should recall the saved processor and its state.

### Step 5 — Review Routing

Check the **Routing** section and confirm that the eight returned DAW channels correspond to the hosted processor's expected inputs.

### Step 6 — Start processing

Start the Hex Inception input path and play the DAW session.

The recorded eight-channel performance can now be presented to the hosted processor as a resynthesis/reprocessing source.

Record or monitor the resulting audio and/or MIDI in the DAW.

---

## 10. Hosted Plug-in

Hex Inception hosts one processor that receives the eight-channel source.

The **Hosted Plug-in** section is used both to choose the processor and to show the currently loaded processor.

When loaded, the interface provides a compact summary similar in purpose to:

- plug-in name
- manufacturer and format
- input and output count
- running state

For example, an eight-input processor may be shown as having:

**8 inputs · 2 outputs · Running**

### Changing the hosted processor

Stop Hex Inception before choosing another hosted plug-in.

Select the replacement using the **Hosted Plug-in** selector.

### Project recall

Hex Inception saves the hosted processor identity and hosted state with the project/session.

When reopening the project, the saved processor should be restored automatically when it remains installed and available.

### If the saved plug-in is unavailable

If Hex Inception reports that no plug-in is loaded or that the saved processor cannot be restored:

- stop audio input
- confirm the required AU/VST3 is installed
- use the Hosted Plug-in selector to select an available compatible processor
- verify the Routing section before restarting audio

A missing processor should not be silently replaced with an unrelated one.

---

## 11. Routing

The **Routing** section describes how the eight source channels are presented to the hosted processor.

It is part of the active signal path and should be read as a channel map.

The key idea is:

**eight source channels → hosted plug-in input channels**

The source is determined by the selected mode:

- **Live:** the selected physical input device
- **Reamp / Resynth:** Hex Inception 8ch

### Verify routing by signal, not by assumption

When using a new source device or processor:

1. Play or send one source channel at a time.
2. Watch the source/channel meters.
3. Observe which hosted input receives it.
4. Check the corresponding entry in Routing.
5. Repeat until all eight channels are accounted for.

This is particularly important with hexaphonic hardware because manufacturer channel labels and string order can differ.

### Current routing workflow

Use the channel assignments presented in the **Routing** section.

If a saved configuration cannot be resolved because its device or hosted processor is missing, correct the relevant source or hosted selection first, then review the routing shown by Hex Inception.

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

## 13. Receiving and Stopped

The main operational status is deliberately simple.

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

The channel meters are an important setup tool.

Use them to answer:

- Is the source reaching Hex Inception?
- Are all eight channels present?
- Does each string/source appear on the expected source channel?
- Is one channel unexpectedly silent?
- Is the channel order different from what the processor expects?

For a new device, the safest initial test is to excite one source at a time.

For a six-string hex source, play each string separately and note which of the eight channels responds.

---

## 15. MIDI

Some hosted hexaphonic processors generate MIDI.

Where supported, Hex Inception can pass generated MIDI into the wider DAW workflow.

When diagnosing MIDI, check the signal path in this order:

1. Is Hex Inception receiving the correct audio?
2. Is the hosted processor receiving the correct eight-channel mapping?
3. Is the hosted processor generating MIDI?
4. Is the DAW or destination listening to the appropriate MIDI source?

Do not begin by troubleshooting MIDI routing if the hosted plug-in is receiving the wrong audio channels.

---

## 16. Status Details and Diagnostics

The normal interface is intended to show the information needed during ordinary use without exposing every engineering detail.

Use **Status Details** and **Diagnostics** when you need to investigate a problem.

Depending on the current state, diagnostics can help confirm information such as:

- selected source mode
- selected physical device
- requested buffer
- actual accepted device buffer
- sample rate
- channel activity
- hosted processor state
- routing state

If something stops working, inspect the status information before changing several settings at once.

---

## 17. Troubleshooting

### The physical device does not appear

Check that:

- the device is connected and powered
- macOS can see it
- it exposes at least eight input channels
- Hex Inception is in **Live** mode

Hex Inception intentionally does not fill the Live selector with devices that cannot provide the required eight-channel source.

### Start Audio Input does not produce audio

Check:

- Hex Inception is in the correct source mode
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

Test the source one string at a time.

Possible causes include:

- the hardware itself is not supplying all expected channels
- the source channel order differs from what you expected
- one DAW return channel is missing in Reamp / Resynth
- the hosted plug-in is not exposing the required eight-input layout
- the Routing section does not match the intended signal order

### Strings appear on unexpected inputs

Do not rename or destructively reorder the original recording as the first response.

Identify the actual source order with the meters, then compare it with the Routing section and the hosted processor's expected inputs.

### Reamp / Resynth is silent

Confirm that:

- **Hex Inception 8ch** is installed
- Hex Inception is set to **Reamp / Resynth**
- the DAW is sending audio to Hex Inception 8ch
- all required output channels are being sent
- the eight-channel order is correct
- Hex Inception shows **Receiving** when the path is started
- a compatible hosted processor is loaded

### Crackles or instability

Try a larger physical buffer in Live mode.

For example:

**32 → 64 → 128 → 256**

Do not treat the smallest selectable buffer as automatically preferable.

### A 192 kHz session does not work

192 kHz is not supported.

Use one of:

**44.1 / 48 / 88.2 / 96 kHz**

---

## 18. Recommended First-Time Test

Before relying on Hex Inception in an important project:

1. Create a new DAW project.
2. Insert Hex Inception.
3. Select **Live**.
4. Select the physical eight-channel source.
5. Use **128 frames** initially.
6. Select the intended hosted processor while stopped.
7. Review Routing.
8. Press **Start Audio Input**.
9. Confirm the status shows **Receiving**.
10. Test every string/source independently.
11. Confirm all eight channels are accounted for.
12. Confirm the hosted processor produces the expected result.
13. Save the project.

This gives you a known-good reference configuration.

---

## 19. Project Recall

Hex Inception is designed to restore the important state of a saved DAW project.

That state includes the information needed to reconstruct the intended workflow, including the selected source configuration, explicit buffer choice, hosted processor and routing state.

The selected explicit buffer is preserved rather than being returned to 128 every time the project is opened.

The hosted plug-in and its state are also restored automatically when possible.

If required hardware or a hosted plug-in is missing, Hex Inception should report the unresolved condition rather than silently choosing an unrelated replacement.

Always check the visible status after reopening a project before recording.

---

## 20. Practical Workflow Advice

### Live performance

Prioritise:

1. correct source device
2. correct eight-channel signal
3. correct hosted processor
4. correct routing
5. stable buffer
6. lowest practical latency only after the above are reliable

### Recording

Where possible, preserve the original eight discrete hex channels.

This gives you the option to use **Reamp / Resynth** later rather than permanently committing to the tracking or synthesis result generated during the original performance.

### Reprocessing

Keep the recorded source channels intact.

Use Hex Inception's source/routing workflow to present them correctly to the hosted processor instead of destructively altering the original performance files.

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

> **Provide a reliable eight-channel hexaphonic source to a hosted processor when the surrounding DAW cannot conveniently provide that input itself.**

---

## 22. Quick Reference

### Live

**Physical hex device → Hex Inception → hosted processor → DAW**

1. Insert Hex Inception.
2. Select **Live**.
3. Select the physical device.
4. Select buffer.
5. Select/confirm the Hosted Plug-in while stopped.
6. Review Routing.
7. Press **Start Audio Input**.
8. Confirm **Receiving**.
9. Play/record.

### Reamp / Resynth

**DAW → Hex Inception 8ch → Hex Inception → hosted processor → DAW**

1. Preserve the eight discrete recorded channels.
2. Route them to **Hex Inception 8ch**.
3. Select **Reamp / Resynth**.
4. Select/confirm the Hosted Plug-in while stopped.
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

## 23. Information to Include With a Support Report

Include:

- macOS version
- DAW and version
- Hex Inception version
- Hex Inception plug-in format
- hosted plug-in name, format and version
- Live or Reamp / Resynth mode
- physical source device, if using Live
- sample rate
- requested buffer
- actual accepted buffer, if relevant
- which exact channels are affected
- whether Hex Inception shows **Receiving** or **Stopped**
- whether the problem occurs in a new empty project
- relevant Status Details or Diagnostics

For channel problems, describe the observed mapping explicitly.

For example:

> Source channel 5 reaches hosted input 7; source channel 7 is silent.

That is much more useful than reporting only that the strings are routed incorrectly.

---

## 24. Summary

Hex Inception provides a focused eight-channel audio path for hexaphonic processing on macOS.

Use **Live** to receive an eligible physical eight-channel device directly.

Use **Reamp / Resynth** to receive a previously recorded eight-channel performance through **Hex Inception 8ch**.

Select the hosted processor while stopped, verify the Routing section, start the input path, and confirm **Receiving**.

The basic principle is:

**Get all eight source channels to the intended hosted processor inputs reliably, without depending on the DAW to provide that eight-channel plug-in input itself.**
