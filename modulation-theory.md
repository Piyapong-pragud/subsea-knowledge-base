# Modulation Theory for Coherent Optical Transmission
Modulation is the process of encoding digital information onto an optical carrier  
by adjusting physical parameters of the lightwave.  
Modern submarine and long-haul terrestrial systems use *coherent modulation*,  
which provides high spectral efficiency and long-distance performance.

---

## 📘 1. What Is Modulation?
In optical communication, modulation defines how bits (0/1) are represented as  
changes in the optical field.  
Coherent systems modulate **phase**, **amplitude**, and use dual polarization (DP).

Key controlled parameters:
- **Amplitude (A)**
- **Phase (ϕ)**
- **Polarization (X/Y)**
- **Frequency (f)** in some systems

Each combination of (A + ϕ) creates a **symbol** on the constellation diagram.

---

## 📘 2. Constellation Diagram
A constellation is a map of all symbol positions.

Examples:

| Modulation | Symbols | Bits/Symbol | Notes |
|-----------|---------|--------------|--------|
| **BPSK** | 2 | 1 bit | Maximum reach, lowest capacity |
| **QPSK** | 4 | 2 bits | Subsea workhorse, long distance |
| **8QAM** | 8 | 3 bits | Medium reach |
| **16QAM** | 16 | 4 bits | High spectral efficiency |
| **64QAM** | 64 | 6 bits | Short-reach metro systems |

Higher-order modulation = more bits/symbol  
but requires higher OSNR and shorter distance.

---

## 📘 3. Phase Modulation Fundamentals (QPSK)
**QPSK (Quadrature Phase Shift Keying)** encodes data using 4 phase states:

- 45°
- 135°
- 225°
- 315°

Mapping:

00 → 45° 01 → 135° 11 → 225° 10 → 315°

Advantages:
- Excellent reach (thousands of km)
- High tolerance to ASE noise and nonlinearities
- Most commonly used on submarine systems (APG, AAG, SMW, TGN, etc.)

---

## 📘 4. Amplitude + Phase Modulation (16QAM and above)
Higher-order modulations use both:
- **Phase shifts**, and  
- **Amplitude changes**

Example: 16QAM has 4 amplitude levels × 4 phase states.

Pros:
- More bits per symbol → higher capacity

Cons:
- Much higher OSNR requirement
- Shorter transmission distance
- Sensitive to phase noise and nonlinear effects

---

## 📘 5. Dual-Polarization Modulation (DP-QPSK / DP-16QAM)
Modern coherent transponders transmit symbols on **two orthogonal polarizations** simultaneously:

- X-pol  
- Y-pol  

This doubles capacity:

- QPSK (2 bits/symbol) → **DP-QPSK (4 bits/symbol)**
- 16QAM (4 bits/symbol) → **DP-16QAM (8 bits/symbol)**

Used by:
- Submarine systems (DP-QPSK)
- High-capacity terrestrial long-haul (DP-16QAM)

---

## 📘 6. OSNR Requirements
Minimum OSNR (0.1 nm resolution bandwidth):

| Modulation | OSNR Required |
|------------|----------------|
| BPSK | 7–9 dB |
| **QPSK** | **11–14 dB** |
| 8QAM | 15–17 dB |
| 16QAM | 18–20 dB |
| 64QAM | 22–24 dB |

Submarine repeater chains typically support:

### ✅ BPSK / QPSK  
### ❌ 16QAM / 64QAM (OSNR not sufficient)

---

## 📘 7. Baud Rate and Symbol Rate
Symbol rate = number of symbols per second (Gbaud)

Example:
- 100G DP-QPSK → ~32 Gbaud
- 200G DP-16QAM → ~32–34 Gbaud
- New 400G systems → 60–70 Gbaud with advanced shaping

Baud rate affects:
- Required spectrum  
- Filtering  
- Nonlinear performance  

---

## 📘 8. IQ Modulator (The Key Hardware Component)
A modern coherent transmitter uses an **IQ (In-phase/Quadrature) Modulator**  
to encode:

- Amplitude  
- Phase  
- Both polarizations  

Structure:
- I-branch → amplitude control  
- Q-branch → phase control  
- Mach–Zehnder interferometers (MZI)  
- LiNbO₃ electro-optic modulators  

The IQ Modulator is the core of coherent transmission.

---

## 📘 9. DSP (Digital Signal Processing)
The receiver uses a powerful DSP to correct transmission impairments:

- Chromatic dispersion compensation  
- PMD equalization  
- Carrier/phase recovery  
- Adaptive equalization  
- Nonlinear compensation (simplified)  
- FEC decoding  

DSP is what makes coherent systems capable of trans-oceanic distances.

---

## 📘 10. Why Submarine Systems Use QPSK
Reasons QPSK dominates submarine communications:

- Excellent OSNR tolerance  
- Robust against ASE from hundreds of EDFAs  
- Works with 60–100 km spans  
- Less sensitive to nonlinearities  
- Long-reach capability with SD-FEC  
- Stable constellation under temperature variations  
- Proven across all major systems (APG, AAG, PLCN, JUPITER)

New SDM systems still rely on QPSK for long-haul segments.

---

## 📘 11. Summary
Coherent modulation transforms optical communications by combining:

- **IQ modulation**
- **Dual polarization**
- **Advanced digital signal processing**

Modulation options form a trade-off:

| More bits/symbol | → | Higher capacity, shorter distance |
| Fewer bits/symbol | → | Lower capacity, very long reach |

Submarine cables operate at the longest distances →  
**QPSK is the optimal balance of reach, robustness, and OSNR margin.**

---

File: modulation-theory.md Category: Optical Transmission Systems
