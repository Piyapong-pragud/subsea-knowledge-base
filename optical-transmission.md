# Optical Transmission Systems – Subsea Layer Overview
🔵 **Optical Transmission (คลื่นแสง)** คือหัวใจหลักของ Submarine Cable  
ครอบคลุม: Transponder • WDM • EDFA • OSNR • DSP • ROADM • Nonlinear • Monitoring  
เอกสารนี้เป็นภาพรวมระดับ “Engineer → Specialist”

---

## 1) Optical Layer Architecture (ภาพใหญ่ที่สุด)

Optical Layer ของระบบใต้น้ำประกอบด้วยส่วนสำคัญดังนี้:

- **SLTE / Transponder**
- **WDM Mux/Demux**
- **ROADM / WSS (บางระบบ เช่น APG)**
- **Repeater Chain (EDFA ใต้น้ำ)**
- **Performance Monitoring**
- **DSP (Coherent Engine)**
- **Power Control / Gain Control**

โครงสร้างแบบย่อ:

[SLTE/Transponder] → [WDM] → [ROADM/WSS] → [EDFA Chain] → WET PLANT → [EDFA] → [SLTE]

---

## 2) Transponder / Coherent Engine

### หน้าที่
- สร้างคลื่นแสงความเร็วสูง (Tx)
- รับคลื่นแสงแล้ว decode (Rx)
- เลือกรูปแบบ modulation เช่น QPSK / 8QAM / 16QAM
- ใช้ DSP แก้ noise, dispersion, nonlinear

### ส่วนประกอบหลัก
- FEC Encoder  
- IQ Modulator  
- Tunable Laser  
- DSP Receiver  

### Vendors
Ciena • Nokia • Infinera • SubCom • NEC • HMN

---

## 3) DWDM Channel Plan (แผนผังช่องสัญญาณ)

### Spacing ต่อระบบ
- **APG:** 37.5 GHz  
- **CSN:** 50 GHz  
- ระบบใหม่: **Flex-grid 12.5 GHz slot**

### Launch Power
- ช่วงมาตรฐาน: **−2 ถึง +1 dBm/ช่อง**  
- ขึ้นกับ nonlinear limit ของสาย

### การจัดการสเปกตรัม
- ปรับสมดุลให้ทุกช่องระดับกำลังใกล้เคียงกัน
- ใช้ **GFF หรือ WSS** เพื่อรักษา Flat Spectrum

---

## 4) ROADM / WSS (Routing คลื่นแสง)

### ROADM ทำอะไร?
- เพิ่ม/ลดช่อง (Add/Drop)
- ปรับ power ต่อช่อง
- จัดเส้นทาง wavelength แบบ dynamic

### WSS (Wavelength Selective Switch)
- Insertion Loss 5–7 dB
- ใช้ใน BU รุ่นใหม่ หรือ CLS ที่ทันสมัย

---

## 5) EDFA Amplifier (ใต้น้ำ)

### EDFA (Erbium-Doped Fiber Amplifier)
ใช้เพิ่มกำลังแสงทุก 60–80 km

**Key Specs:**
- Gain ~ 14–20 dB
- Noise Figure ~ 4–5 dB
- Pump laser: 980 nm / 1480 nm

### Repeater Chain
สายความยาว 2000–10,000 km  
จะมี repeater 30–200 ตัวตามระยะ

---

## 6) OSNR – Optical Signal-to-Noise Ratio

ตัวชี้วัดคุณภาพสำคัญที่สุดของ Optical Layer

### ค่าเป้าหมายต่อ modulation
- **QPSK:** ≥ 14 dB  
- **8QAM:** ≥ 16 dB  
- **16QAM:** ≥ 18 dB  
- **64QAM:** ≥ 21 dB  

### วิธีวัด
- SLTE internal monitor  
- Optical Spectrum Analyzer (OSA)  
- Performance Monitoring (PM)  

---

## 7) BER / FEC

### FEC (Forward Error Correction)
- Coherent ใช้ **SD-FEC**  
- 10G ใช้ **RS(255,239)**

### Threshold
- Pre-FEC ต้องดีขึ้นกว่า **1×10⁻²**  
- Post-FEC ควรใกล้ 0

---

## 8) Nonlinear Effects (สำคัญในสายน้ำลึก)

### 1) SPM – Self Phase Modulation
power สูง → pulse บิด

### 2) XPM – Cross Phase Modulation
ช่องข้างเคียงรบกวนกัน

### 3) FWM – Four Wave Mixing
ความถี่ใหม่เกิดขึ้น → ทำให้บางช่อง OSNR ตก

### 4) Raman Scattering
เกิด slope: λ สั้นตก, λ ยาวขึ้น

---

## 9) Constellation Analysis

สัญญาณหลังผ่าน DSP จะถูกแสดงเป็นรูปแบบจุด

สรุปอาการที่พบ:

| อาการใน Constellation | สาเหตุที่เป็นไปได้ |
|------------------------|---------------------|
| จุดเบลอ | OSNR ต่ำ |
| จุดกระจายแกนตั้ง | Phase Noise |
| จุดยืดแนวนอน | Amplitude Noise |
| วงรีเอียง | LO Laser drift |
| กระจายไม่เสถียร | Nonlinear (SPM/XPM/FWM) |

---

## 10) Optical Performance Monitoring (OPM)

ค่าที่วัดได้:
- Power ต่อช่อง  
- Spectrum Shape  
- OSNR  
- Q-factor  
- CD (Chromatic Dispersion)  
- PMD (Polarization Mode Dispersion)  
- BER / FEC status  

---

## 11) SLTE Alarm ที่สำคัญ

- Loss of Signal (LOS)  
- Loss of Frame (LOF)  
- OSNR Deviation  
- Q-factor Low  
- PMD High  
- FEC Uncorrectable  
- Frequency Offset Drift  
- Pilot Tone Missing  

---

## 12) Channel Provisioning Flow (ขั้นตอนเปิดช่องใหม่)

1. ตรวจ OSNR budget  
2. ตั้ง launch power  
3. เปิดช่องใน ROADM/WSS  
4. ตรวจ BER / Q-factor  
5. ตรวจ Constellation  
6. Lock channel & monitoring  

---

## 13) Power Equalization & Spectrum Flatness

ทำโดย:
- GFF (Gain Flattening Filter)  
- WSS (Per-channel equalization)  
- Pump Power Control  
- Equalization Tables  

---

## 14) Fault ที่พบบ่อยใน Optical Layer

- Power drop รายช่อง → WSS misalignment  
- OSNR ตกทั้ง spectrum → Repeater aging  
- CD Jump → มี splice ใหม่จากการซ่อม  
- Full band RDI → Interface/Transponder ปัญหา  
- สัญญาณแกว่ง → Laser drift, PLL ไม่ล็อก  

---

## สรุป Optical Layer

> Optical Transmission =  
> ระบบใหญ่ที่ประกอบด้วย DSP + Modulation + WDM + EDFA + Monitoring  
> ทำงานร่วมกันเพื่อส่งสัญญาณหลายพันกิโลเมตรผ่านทะเลลึก

---
