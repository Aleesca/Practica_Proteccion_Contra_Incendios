# Briefing Document: Design and Implementation of Automatic Sprinkler Systems (UNE-EN 12845)

## Executive Summary

This document synthesizes technical principles, historical evolution, and design methodologies for automatic sprinkler systems, primarily focused on the **UNE-EN 12845:2016** standard. Sprinkler systems serve two primary functions: protecting lives and property, and maintaining structural integrity by preventing building collapse during a fire. 

Modern fire protection has evolved from 17th-century manual efforts to highly sophisticated automatic systems. The current regulatory landscape identifies four main risk categories—Light Hazard (RL), Ordinary Hazard (RO), Extra Hazard Process (REP), and Extra Hazard Storage (REA)—each requiring specific discharge densities and areas of operation. Technical effectiveness relies on a synergy between hydraulic calculations (utilizing the K-factor and Hazen-Williams formula), thermal sensitivity (measured by the Response Time Index), and system reliability. While wet pipe systems remain the most common and reliable (~95% activation reliability), specialized applications like Ro-Ro decks and cold storage necessitate dry, deluge, or pre-action configurations to manage environmental and high-load challenges.

---

## Historical Evolution of Sprinkler Technology

The development of fire protection systems was spurred by major urban disasters, such as the Great Fire of London (1666).

*   **Initial Innovations:** The fire hose was developed in 1672 by Jan Van Der Heyden, followed by early fire engines.
*   **The Automatic Precursor:** In 1812, Benjamin Wyatt designed the first precursor to the modern sprinkler.
*   **The First Practical Sprinklers:** 
    *   **A. Stewart Harrison (1864):** Designed a brass sphere with perforations and a white rubber plug held by a fusible metal element, though it was never patented.
    *   **Henry S. Parmalee (1874):** Patented the first practical automatic sprinkler in the U.S., featuring a shower-type device held closed by a spring and low-melting-point rings.
    *   **Frederick Grinnell (1882):** Improved upon Parmalee’s design by introducing more sensitive elements, a 1/2" orifice, and a notched deflector, eventually developing the "glass disc" model in 1891.
*   **Modern Advancements:** The 1950s saw the development of the "standard spray" or "spray sprinkler" by Factory Mutual, which produced a hemispherical discharge pattern. By the late 1980s and early 1990s, high-performance options like **ESFR (Early Suppression Fast Response)** and **CMSA (Control Mode Specific Application)** were introduced to handle high-demand storage risks.

---

## Core System Components and Network Types

A standard sprinkler system consists of a water supply, a control station (puesto de control), a piping network, and the sprinklers themselves.

### 1. Control Station Valves
*   **Alarm and Retention Valves:** Govern the control station and manage system pressure.
*   **Cut-off and Sectioning Valves:** Usually gate or butterfly valves. They must be slow-acting to prevent water hammer and typically include limit switches for system monitoring.
*   **Test and Drainage Valves:** Installed at the most unfavorable point (to simulate a single sprinkler's flow) and at the lowest points (for system emptying).

### 2. Network Configurations
| Network Type | Description | Key Characteristics |
| :--- | :--- | :--- |
| **Tree (Árbol)** | Branches stem from a central manifold. | Manifold size decreases as it moves away from the supply; manual hydraulic calculation is possible. |
| **Grid (Malla/Rejilla)** | Adjacent branches form closed loops. | Improved hydraulics; water reaches discharge from multiple paths; requires software for calculation. |
| **Loop (Anillo)** | Manifolds form a closed ring. | Provides multiple paths to discharge; offers hydraulic improvements over tree systems. |

---

## Technical Classification of Sprinklers

Sprinklers are classified based on mounting, sensitivity, and performance characteristics.

### Mounting and Specialized Types
*   **Upright (Montante):** Discharges water upward.
*   **Pendant (Colgante):** Discharges water downward.
*   **Sidewall (De Pared):** Discharges from the wall toward the center of the room.
*   **Concealed/Flush/Semi-recessed:** Used for aesthetic purposes; the sprinkler is hidden behind a cover or partially embedded in the ceiling.
*   **In-rack:** Installed within storage shelving; requires protective cages and rain shields to prevent wetting from higher sprinklers.
*   **Dry Sprinklers:** Feature an extension to prevent water from entering the pipe until activation, ideal for cold storage.

### Thermal Sensitivity (RTI)
The Response Time Index (RTI) measures how quickly the thermal element acts.
*   **Quick Response:** RTI < 50.
*   **Special Response:** RTI between 50 and 80.
*   **Standard Response:** RTI > 80.

### Thermal Element Color Coding
Sprinklers are color-coded to indicate their nominal operating temperature.
*   **Orange:** 57°C (Bulb).
*   **Red:** 68°C (Bulb).
*   **Yellow:** 79°C (Bulb).
*   **Green:** 93°C–100°C (Bulb).
*   **Blue:** 121°C–141°C (Bulb).

---

## System Operation Modes

| System Type | Presurization | Ideal Application | Limitations |
| :--- | :--- | :--- | :--- |
| **Wet Pipe** | Water | Most common/economic; rapid response. | Not for frost-prone areas or >95°C. |
| **Dry Pipe** | Air/Inert Gas | Areas prone to freezing or >70°C. | Higher complexity; 60-120s delay in water delivery. |
| **Deluge** | Atmospheric | Hangars, petro-chem; total inundation. | Requires galvanized pipes due to oxygen/corrosion. |
| **Pre-action** | Air/Inert Gas | Museums, cold storage; avoids water damage. | Requires detection system signal + sprinkler activation. |

---

## Hydraulic Principles and Design Calculation

### Fundamental Formulas
*   **Caudal (Flow):** $Q = K \cdot \sqrt{P}$, where $Q$ is flow (l/min), $K$ is the K-factor, and $P$ is pressure (bar).
*   **Friction Loss:** Determined by the Hazen-Williams formula, considering the pipe material (Factor C), length, and diameter.
*   **Elevation Loss:** $P_e = 0.098 \cdot h$, where $h$ is the height difference in meters.

### Design Methodologies
1.  **Density-Area Method:** Used for standard sprinklers. Design is based on ensuring a specific density (l/min/m²) over a theoretical area of operation.
2.  **Number of Open Sprinklers:** Used for ESFR and CMSA sprinklers. Design considers a fixed number of sprinklers (e.g., 12) operating at a specific minimum pressure based on roof height and storage type.

### Hydraulic Dispersion
The theoretical flow ($Q_{teo}$) often differs from the real flow ($Q_{real}$) because sprinklers closer to the water supply operate at higher pressures than the most unfavorable sprinkler. A common practice is to add a **10% dispersion factor** ($Q_{real} = Q_{teo} \cdot 1.1$) to account for these variations.

---

## Hazard Classification (UNE-EN 12845)

Risk is determined by use, fire load, and combustibility of materials.

*   **Light Hazard (RL):** Schools, offices (excluding storage). Density: 2.25 mm/min.
*   **Ordinary Hazard (RO1–RO4):** Commercial premises, industrial sites. Density: 5.0 mm/min. Area of operation ranges from 72 m² to 360 m².
*   **Extra Hazard Process (REP):** High concentration of flammable materials. Densities: 7.5 to 12.5 mm/min.
*   **Extra Hazard Storage (REA):** High-piled storage requiring higher water volumes.

---

## Important Quotes with Context

> **"The sprinkler is a thermosensitive device that releases a stream of water with a determined discharge pattern and a specific water flow."**
*Context: This fundamental definition underscores the dual role of the sprinkler as both a detection and an extinction device.*

> **"In the case of dry pipe systems... the system's pumps must have a capacity sufficient for either the entire deck or at least two sections."**
*Context: Referring to the high-demand requirements for Ro-Ro decks, where rapid fire spread is a risk.*

> **"A pre-action system... seeks to prevent water discharge due to mechanical damage to the piping, especially in installations where protected objects are of great value, such as a museum."**
*Context: Explains the logic behind using interlocked systems to minimize accidental water damage.*

> **"Overall performance = system activation reliability × system performance effectiveness."**
*Context: A formulaic approach to evaluating fire safety systems, highlighting that a system is only as good as its maintenance and its design suitability.*

---

## Actionable Insights

*   **Maintenance is Critical:** Statistics show that 53% of system failures occur because the system was shut off, and 15% are due to lack of maintenance. Regular inspection of valves and pressure switches is non-negotiable.
*   **Early Insurer Consultation:** Different insurance companies have varying opinions on risk classification. Consult the insurer early in the design process to ensure the selected risk category (RL, RO, REP, REA) meets their requirements.
*   **Account for Modern Hazards:** Traditional standards like IMO Res A.123(V) for Ro-Ro decks may be insufficient for modern vehicles with high plastic content and alternative fuels (LNG, electric). Designers should consider automatic wet/dry systems with higher discharge densities.
*   **Select Appropriate K-Factors:** When calculating the required flow, always choose the next highest normalized K-factor (e.g., K115 if K84.85 is required) to ensure minimum pressure and density requirements are met.
*   **Environmental Considerations:** Always use galvanized piping in deluge or pre-action systems using compressed air to prevent corrosion caused by the oxygen present in the air. Use upright sprinklers in dry systems to prevent water accumulation and freezing in the pendant position.