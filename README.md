<img width="256" height="256" alt="HexInceptionIcon" src="https://github.com/user-attachments/assets/7fce60ad-24c9-4e7c-8dd1-799b2a1f17e3" />

# Hex Inception 1.0.0

The first public release of **Hex Inception**, a macOS plug-in for hexaphonic guitar DAW/host workflows, both in performance and recording.

Hex Inception solves a common DAW/host limitation in integrated hex guitar/computer setups: when connected via USB your audio hardware may expose all channels correctly — typically two DI channels plus six individual strings — while your DAW cannot provide a practical multichannel input path to the plug-in that needs them. Hex Inception acquires the multichannel source directly and routes it to a compatible plug-in via its hosting capability.

### Highlights

- **AUv2 and VST3** plug-in formats
- Direct **8-channel Core Audio input** for Live workflows
- Hosts compatible multichannel processors, such as **MIDI Guitar 3 Hex** (Jam Origin) and **PatchWork** (Blue Cat Audio)
- Flexible audio mapping between source channels and hosted plug-in inputs
- **Reamp / Resynth** workflow for processing recorded hex performances
- **Hex Inception 8ch** virtual Core Audio device for eight-channel DAW return (suitable for audio aggregation)
- MIDI output routing for compatible hosted processors
- Supports **44.1, 48, 88.2 and 96 kHz**
- Physical buffer choices from **16–512 frames**  

### Typical signal flow

**Live** mode:  
`Hex audio device → Hex Inception → hosted plug-in → DAW`

**Reamp / Resynth** mode:  
`DAW → Hex Inception 8ch → Hex Inception → hosted plug-in → DAW` 

### Installation

**macOS:** `Hex_Inception_1.0.0_macOS.pkg`

The installer contains the **AUv2, VST3 and Hex Inception 8ch HAL driver**. It is Developer ID signed, Apple notarized and stapled for normal macOS installation. 

The HAL driver is intended to be aggregated with each user's primary audio device to enable reamping/resynthing individually recorded strings.

**SHA-256:**  
`68b608b6220bddd192e60da51a4df984b6d89fba616d01bb2dcdfb685054d037`

> Hex Inception requires a compatible multichannel audio source and a compatible hosted multichannel plug-in for its primary hexaphonic workflow.
> Full setup instructions, Live and Reamp / Resynth workflows, routing guidance and troubleshooting are available in the Hex Inception User Guide⁠.
