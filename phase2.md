# 🟧 Phase 2 – Intermediate (ระดับปฏิบัติการ/วิศวกรภาคสนาม)

เข้าใจเชิงลึกมากขึ้น และสามารถนำไปใช้งานจริงใน CLS ได้

---

# A) PFE เชิงลึก (Advanced Power Feeding)

---

## 1) การคำนวณแรงดันและกระแส (Submarine Cable DC Feeding)

สูตรพื้นฐานของระบบจ่ายไฟสายใต้น้ำ:

\[
V = I \times R_{\text{total}} + \text{margin}
\]

- **I** = กระแสคงที่ (0.8–1.5 A)  
- **R_total** = ความต้านทานรวม (Ω/km × ระยะทาง)  
- **Margin** = aging, temperature, pump drift, repeaters loss  

### 🔸 ตัวอย่างจากระบบ APG
- Current: **1.0 A**  
- Resistance: **~1.5 Ω/km**  
- ระยะ 300 km → R ≈ **450 Ω**  
- Voltage ≈ **450 V + margin 100–200 V**  

แต่ระบบจริงใช้แรงดันระดับ  
→ **±1.5 kV ถึง ±2 kV**  
(เพราะรวม repeater chain ที่ยาวหลายพันกิโลเมตร)

---

## 2) Fault Handling ขั้นสูงใน PFE

---

### 🔥 Ground Fault
- ตัวนำแตะน้ำทะเล → เกิด leakage  
- มี **Earth current** ไหลกลับ  
- ตรวจโดย:  
  - Insulation Resistance (IR test)  
  - สังเกต Earth current drift  
  - Sectionalizing tests แยกฝั่ง  

---

### 🔥 Current Imbalance
- กระแสสองด้านของระบบ BEF ไม่เท่ากัน  
- บอกได้ว่า:  
  - BU เสีย  
  - Repeater เสีย  
  - Fault ที่ conductor  
- ใช้ **PFE telemetry** ตรวจ real-time

---

# B) Optical Transmission (DWDM, OSNR, Equalization)

---

## 1) DWDM Channel Management

สิ่งที่ต้องจัดการ:

- Channel spacing (50 GHz / 37.5 GHz / Flex-grid)  
- Channel plan  
- Launch power  
- Per-channel attenuation  
- Nonlinear limit  
- Equalization  

### 🔹 ตัวอย่าง – APG
- Coherent 100G / 200G  
- 37.5 GHz spacing  
- OSNR target: **14–17 dB**

### 🔹 ตัวอย่าง – CSN
- บาง segment = 10G NRZ  
- 50 GHz spacing  
- OSNR target ~18–23 dB (NRZ ต้องการสูงกว่า)

---

## 2) Gain Equalization & ASE Noise

### 🎯 เป้าหมาย: Flat Spectrum

ปัญหาที่พบ:

- EDFA ใต้น้ำมี **gain tilt**  
- BU / ROADM / NFV เพิ่ม loss  
- ASE noise จาก repeater chain เพิ่มตามระยะทาง  

วิธีแก้:

- ใช้ **GFF** (Gain Flattening Filter)  
- ปรับ per-channel ด้วย **WSS**  
- คำนวณ chain budget ให้ OSNR ไม่เกิน threshold ของ modulation

---

## ⚡ ASE Noise (Amplified Spontaneous Emission)

- เกิดใน EDFA ใต้น้ำทุกตัว  
- เป็น noise หลักที่ทำให้ OSNR ตก  
- ระยะยิ่งไกล → OSNR ยิ่งลดแบบ cumulative  
- ต้องวิเคราะห์ร่วมกับ ripple / tilt / nonlinear margin

---

# C) Fault Localization (การหาตำแหน่งขัดข้อง)

---

## 1) OTDR Trace แบบละเอียด (Long-range Subsea OTDR)

สิ่งที่ต้องอ่านให้เป็น:

- Event loss  
- Splice loss  
- Fiber attenuation  
- Reflective events  
- Dead zone  
- Distance to fault  

อุปกรณ์ที่ใช้ใน Subsea:

- Dynamic range: **40–50 dB**  
- Narrow pulse laser  
- Long-range optimized mode

---

## 2) SLM (Submarine Line Monitoring)

ระบบ Supervisory ใช้ตรวจ:

- Repeater status  
- Pump performance  
- BU state  
- Earth leakage trend  
- Aging & margin drift  
- Fault trend ก่อน outage

ทำงานผ่าน:

- Supervisory wavelength (OSC)  
- Telemetry กลับเข้า CLS

---

# 🎯 สรุป Phase 2

Phase 2 = ความรู้ระดับปฏิบัติการจริงของระบบ Submarine Cable เช่น:

- การเดินระบบ PFE  
- การแยก Fault แบบเบื้องต้นถึงขั้นลึก  
- DWDM / OSNR / Equalization  
- OTDR / SLM  
- Chain budget  

เป็นหัวใจสำคัญของการดูแลระบบ APG, CSN และ International Trunks ทุกเส้นทาง

---
