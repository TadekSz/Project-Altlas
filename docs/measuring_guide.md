# 📏 Atlas Measuring Guide: Physical to Digital

The true power of Project Atlas lies in objective verification. Unlike proprietary swatch books that rely on human eyesight and ambient room lighting, Atlas uses spectral data to mathematically prove a color match.

This guide outlines how to measure a physical substrate (like paper, fabric, or plastic) and compare it against the Atlas Core Database.

---

## 1. The Hardware: Open Spectral Sensors
To bypass expensive, proprietary colorimeters, the Atlas standard is built to work seamlessly with open-hardware micro-spectrometers. 

We recommend utilizing an 11-channel spectral sensor, specifically the **AMS AS7341**, paired with a standard microcontroller (ESP32, Arduino, or Raspberry Pi Pico).

### Sensor Requirements:
*   **Channels:** Minimum 8 channels across the visible spectrum (380nm - 730nm).
*   **Illuminant:** A calibrated onboard White LED (acting as D50/D65 simulation) to provide consistent light regardless of the room you are in.
*   **Enclosure:** The sensor must be placed inside a 3D-printed or opaque shroud to completely block ambient light during a scan.

---

## 2. Calibration (The White Point)
Before scanning a color, the sensor must establish a baseline of "pure white." 

1.  Place the sensor flat against a verified calibration target (e.g., a standard Barium Sulfate white tile, or high-grade optical white PTFE).
2.  Trigger the calibration sequence via your micro-controller. 
3.  The system will record the maximum reflectance values. All subsequent color scans will be calculated relative to this baseline.

---

## 3. Taking a Measurement
1.  **Preparation:** Ensure the physical sample (printout, fabric) is flat and free of dust or heavy textures that cast shadows.
2.  **Isolation:** Place the sensor directly flat against the target area. Do not tilt the device, as ambient light leakage will immediately corrupt the spectral reading.
3.  **Scan:** Trigger the internal LED and capture the reflectance data.

---

## 4. Validation: Calculating Delta E ($\Delta E_{2000}$)
Once you have the physical reading, your software must compare it to the Atlas JSON database. 

1.  **Extract Physical Data:** Convert the raw sensor counts into $L^*a^*b^*$ coordinates based on your calibration profile.
2.  **Fetch Digital Data:** Pull the target color's core identity from the Atlas database. (e.g., `Nebula Blue` -> `L: 45.20, a: 5.15, b: -48.10`).
3.  **Calculate Variance:** Run the two sets of coordinates through the **CIEDE2000 ($\Delta E_{2000}$)** color difference equation.

### Understanding the Results:
*   **$\Delta E < 1.0$:** A mathematically perfect match. The human eye cannot detect a difference.
*   **$\Delta E$ 1.0 - 2.0:** Excellent match. Completely acceptable for high-end commercial printing and branding.
*   **$\Delta E$ 2.0 - 3.5:** Good match. A visible difference exists under close inspection, but acceptable for most standard workflows.
*   **$\Delta E > 4.0$:** Failed match. The substrate, ink mixture, or printing process needs to be adjusted.
