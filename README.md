🌐 Project Atlas: The Open Spectral Color Standard

Welcome to the core repository for Project Atlas.For decades, the design and manufacturing world has relied on proprietary, closed-source color matching systems. These systems are expensive, prone to physical degradation, and inherently disconnected from modern, screen-first workflows.

Atlas is different. It is a 100% free, open-source color standard built on objective optical physics (Spectral Data and CIELAB) rather than proprietary ink mixtures.

🚀 The Vision

Atlas bridges the gap between physical manufacturing and digital rendering by providing a single, verifiable JSON payload for every color. Whether you are building a CSS stylesheet with oklch(), rendering a broadcast-safe video in Rec.2020, or printing CMYK on an uncoated press, Atlas provides the exact mathematical translation.

🗂️ How the Data Works

Every color in the Atlas database is stored as a single JSON file. The data is structured into four core pillars:
1. Core Identity: The objective $L^*a^*b^*$ coordinates and OKLCH values.
2. Spectral Data: The 36-point reflectance curve (the physical DNA of the color).
3. Digital Translation: Pre-calculated, mathematically verified values for sRGB, Display P3, Rec. 2020, and modern CSS tokens.
4. Print Translation: Open-source CMYK ink coverage values based on standard ICC profiles (FOGRA39, GRACoL, etc.).

🛠️ How to Use Atlas (Developers)

You can consume Atlas data directly in your applications via raw GitHub links. No API keys, no subscriptions.
(Example code snippet showing a simple Javascript fetch of a color)

🤝 Contributing: The Pull Request Ecosystem

Atlas relies on community validation. We cannot test every color on every monitor and printing press in the world, but together, we can.

-Submit a Color: Have spectral data for a beautiful, versatile color? Format it using our v2.0 schema and submit a PR.

-Refine a Translation: If you find that a specific CMYK translation prints too warm on FOGRA47, adjust the math in the JSON file and submit a Pull Request with your physical proofing notes.

License: MIT

Maintainer: Atlas Open Foundation
