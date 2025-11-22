# PFE + Sea Earth + Station Earth + SEF/BEF Diagram

ภาพรวมโครงสร้างการจ่ายไฟสำหรับระบบเคเบิลใต้น้ำ  
รวมการแยก Station Earth / Sea Earth และโหมดจ่ายไฟ SEF / BEF

                         ┌──────────────────────────────────────┐
                         │            CLS BUILDING              │
                         │        (Cable Landing Station)       │
                         └──────────────────────────────────────┘
                                    │
                                    │  Station Earth (Grounding)
                                    ▼
                          ┌─────────────────┐
                          │  Station Earth  │
                          │ (Earth Pit /    │
                          │  Ground Rod)    │
                          └──────┬──────────┘
                                 │   (ใช้กับอุปกรณ์ CLS)
           ┌────────────────────┼──────────────────────────┐
           │                    │                          │
           ▼                    ▼                          ▼
   [Router/SLTE]       [DC Plant / UPS]           [Lightning System]



                       ======== PFE (Power Feeding Equipment) ========

                 ┌────────────────────────────────────────────────────┐
                 │                     PFE Unit                        │
                 │                                                    │
                 │     +HV  ──────────────────────┐                   │
                 │                                  │ FEED            │
                 │     -HV  ──────────────────────┐ │ CURRENT         │
                 │                                  │ 1.0–1.5 A       │
                 │     Sea Earth ────────┐          ▼                 │
                 │                        │  (return / reference)     │
                 └────────────────────────┴────────────────────────────┘
                                              |
                                              |
                                       Sea Earth Cable
                                              |
                                              ▼
                               ┌──────────────────────────┐
                               │    Sea Earth Electrode   │
                               │ (Titanium/Graphite Plate)│
                               └───────────┬──────────────┘
                                           │
                                           ▼
                                        SEA WATER
                                (Submarine Return Path)



          ========================== SUBSEA CABLE ===========================

     +HV Conductor  ---------------------------------------------------------->
                                     Repeater Chain
                                     (60–80 km/Repeater)
                                 BU (ถ้ามีสาขาใต้น้ำ)

<--------------------------------------------------------------------------  Sea Return
                                  Sea Water Path



# โหมดการจ่ายไฟ (Feeding Modes)

## 1) SEF – Single-End Feed with Sea Return

                       (ฝั่ง A จ่ายไฟ, ฝั่ง B ใช้ Sea Return)

     PFE (+) A  --->  Conductor ---> Repeaters ---> ลงทะเลปลายทาง
     PFE (-) A  <---  Sea Earth A <--- Sea Water <--- Remote Sea Return

คุณสมบัติ:
- จ่ายไฟจากฝั่งเดียว
- กระแสกลับทางน้ำทะเล (sea return)
- ใช้เมื่อฝั่ง B ไม่พร้อม / offline / maintenance
- เหมาะกับสายสั้น–กลาง (เช่น CSN)

## 2) BEF – Both-End Feed (ส่งไฟทั้งสองฝั่ง)

                     (ฝั่ง A และฝั่ง B จ่ายไฟเข้าหากัน)

      PFE(+) A --->------------------------------>
                     Conductor
<-----------------------------------<--- PFE(-) B

      PFE(-) A <--- Sea Earth A / Sea Return --> PFE(+) B

คุณสมบัติ:
- จ่ายไฟสองฝั่งเข้าหากัน
- ลดแรงดันที่ปลายแต่ละด้าน (แบ่งโหลด)
- ใช้กับสายยาวระดับระหว่างประเทศ เช่น APG
- เพิ่ม redundancy: ถ้าฝั่งหนึ่งล่ม อีกฝั่งยัง feed ได้

## 3) Earth-Free Mode (Reference-Free)

     PFE +HV และ -HV แยกจาก station earth ทั้งหมด
     feed circuit “ลอย” ไม่เกี่ยวกับ earth ใด ๆ

