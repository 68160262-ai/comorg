# สรุปเนื้อหา: Basic Concepts and Computer Evolution
> **บทที่ 1: แนวคิดพื้นฐานและวิวัฒนาการของคอมพิวเตอร์**
### 🏛️ 1. Architecture vs Organization
ความแตกต่างที่สำคัญระหว่างสถาปัตยกรรมและการจัดองค์ประกอบ:
* **Computer Architecture (สถาปัตยกรรม):** คุณลักษณะที่โปรแกรมเมอร์มองเห็นได้ (Logical) เช่น ชุดคำสั่ง (Instruction Set), จำนวนบิตที่ใช้แทนข้อมูล, กลไก I/O
* **Computer Organization (การจัดองค์ประกอบ):** ส่วนประกอบทางกายภาพ (Physical) เช่น สัญญาณควบคุม, อินเทอร์เฟซระหว่างอุปกรณ์, เทคโนโลยีหน่วยความจำ (เช่น จะใช้ตรรกะแบบไหนในการสร้างวงจร)

---

### ⚙️ 2. Structure and Function (โครงสร้างและหน้าที่)
คอมพิวเตอร์มีฟังก์ชันการทำงานหลัก 4 อย่าง:
1.  **Data Processing:** การประมวลผลข้อมูล
2.  **Data Storage:** การจัดเก็บข้อมูล (ทั้งระยะสั้นและระยะยาว)
3.  **Data Movement:** การเคลื่อนย้ายข้อมูลระหว่างคอมพิวเตอร์กับอุปกรณ์ภายนอก
4.  **Control:** การควบคุมการทำงานของ 3 ฟังก์ชันข้างต้น

**โครงสร้างภายในหลัก (Main Components):**
* **CPU (Central Processing Unit):** ควบคุมการทำงานและประมวลผล
* **Main Memory:** หน่วยความจำหลักสำหรับเก็บข้อมูล
* **I/O:** ส่วนอินพุตและเอาต์พุต
* **System Interconnection:** กลไกการเชื่อมต่อ (เช่น System Bus)

---

### ⏳ 3. A Brief History of Computers (วิวัฒนาการ)
* **First Generation (Vacuum Tubes):** ยุคหลอดสุญญากาศ เช่น เครื่อง ENIAC และเครื่อง IAS (ต้นแบบสถาปัตยกรรม Von Neumann ที่เก็บโปรแกรมไว้ในหน่วยความจำ)
* **Second Generation (Transistors):** ใช้ทรานซิสเตอร์แทนหลอดสุญญากาศ ทำให้เครื่องเล็กลง ร้อนน้อยลง และเริ่มมีภาษาโปรแกรมระดับสูง (High-level programming languages)
* **Third Generation (Integrated Circuits):** ยุคแผงวงจรรวม (IC) นำไปสู่การเกิด **Moore’s Law** ที่ว่าจำนวนทรานซิสเตอร์จะเพิ่มขึ้น 2 เท่าในทุกๆ ปี (หรือ 18-24 เดือน)
* **Later Generations:** ยุค Semiconductor Memory และไมโครโปรเซสเซอร์ (LSI/VLSI) เริ่มต้นจาก Intel 4004

---

### 🚀 4. Evolution of Intel x86 & ARM
* **Intel x86:** เป็นสถาปัตยกรรมแบบ **CISC** (Complex Instruction Set Computer) เน้นการรักษาความเข้ากันได้ย้อนหลัง (Backward Compatibility)
* **ARM Architecture:** เป็นสถาปัตยกรรมแบบ **RISC** (Reduced Instruction Set Computer) ออกแบบมาให้ใช้พลังงานต่ำและมีประสิทธิภาพสูงในอุปกรณ์พกพา
    * **Cortex-A:** สำหรับแอปพลิเคชัน (Smartphones)
    * **Cortex-R:** สำหรับงาน Real-time (ระบบเบรก, ยานยนต์)
    * **Cortex-M:** สำหรับ Microcontrollers และอุปกรณ์ IoT
    * ###  ตารางเปรียบเทียบสถาปัตยกรรม: x86 vs ARM

| หัวข้อเปรียบเทียบ | Intel x86 Architecture | ARM Architecture |
| :--- | :--- | :--- |
| **ประเภทสถาปัตยกรรม** | **CISC** (Complex Instruction Set Computer) | **RISC** (Reduced Instruction Set Computer) |
| **ปรัชญาการออกแบบ** | เน้นคำสั่งที่ซับซ้อน ทำงานได้หลายอย่างในหนึ่งคำสั่ง | เน้นคำสั่งขนาดเล็ก เรียบง่าย และทำงานได้รวดเร็ว |
| **การใช้พลังงาน** | สูงกว่า (เน้นประสิทธิภาพสูงสุด) | ต่ำมาก (เน้นการประหยัดพลังงาน/Power Efficiency) |
| **กลุ่มเป้าหมายหลัก** | Desktop, Laptop, High-end Server | Smartphone, Tablet, Embedded Systems, IoT |
| **ความโดดเด่น** | **Backward Compatibility** (รันโปรแกรมเก่าได้ดี) | **Power Efficiency** (ประสิทธิภาพต่อวัตต์ยอดเยี่ยม) |
| **การผลิต** | Intel และ AMD เป็นผู้ผลิตหลัก | ARM ออกแบบและขาย License ให้เจ้าอื่นผลิต (เช่น Apple, Samsung) |
| **การจัดการหน่วยความจำ** | ใช้ชุดจัดการหน่วยความจำ (MMU) ที่ซับซ้อน | มีทั้งรุ่นที่มี MMU (Cortex-A) และไม่มี (Cortex-M) |

---

###  ARM (ARM Products)
ในเอกสารมีการแบ่งกลุ่มผลิตภัณฑ์ ARM ออกเป็น 3 โปรไฟล์หลักที่ควรทราบ:

1.  **Cortex-A (Application):** * **การใช้งาน:** สมาร์ทโฟน, แท็บเล็ต
    * **จุดเด่น:** รองรับระบบปฏิบัติการที่ซับซ้อน (Linux, Android, Windows)
2.  **Cortex-R (Real-time):**
    * **การใช้งาน:** ระบบเบรกรถยนต์ (ABS), คอนโทรลเลอร์ฮาร์ดดิสก์
    * **จุดเด่น:** ต้องการการตอบสนองที่แม่นยำในระดับเสี้ยววินาที (Low latency)
3.  **Cortex-M (Microcontroller):**
    * **การใช้งาน:** อุปกรณ์ IoT, เครื่องใช้ไฟฟ้าขนาดเล็ก
    * **จุดเด่น:** ราคาถูกมาก ใช้พลังงานต่ำที่สุด และออกแบบมาเพื่อระบบฝังตัวโดยเฉพาะ

---

### 🌐 5. Embedded Systems & IoT
* **Embedded System:** ระบบคอมพิวเตอร์ที่ถูกสร้างมาเพื่อทำงานเฉพาะทางอย่างใดอย่างหนึ่ง โดยฝังตัวอยู่ในอุปกรณ์อื่น (เช่น ระบบควบคุมในรถยนต์, เตาไมโครเวฟ)
* **Internet of Things (IoT):** เครือข่ายของอุปกรณ์ทางกายภาพที่มีเซนเซอร์และซอฟต์แวร์เชื่อมต่อกันผ่านอินเทอร์เน็ต
* **Deeply Embedded Systems:** ระบบที่ถูกฝังลึกจนผู้ใช้แทบไม่รู้ว่ามีคอมพิวเตอร์ควบคุมอยู่ มักมีทรัพยากรจำกัดมาก

---

### ☁️ 6. Cloud Computing (คลาวด์คอมพิวติ้ง)
รูปแบบการให้บริการทรัพยากรคอมพิวเตอร์ผ่านเครือข่ายอินเทอร์เน็ต:
1.  **SaaS (Software as a Service):** บริการซอฟต์แวร์สำเร็จรูป (เช่น Gmail)
2.  **PaaS (Platform as a Service):** บริการแพลตฟอร์มสำหรับนักพัฒนา (เช่น Google App Engine)
3.  **IaaS (Infrastructure as a Service):** บริการโครงสร้างพื้นฐาน (เช่น Virtual Machines, Storage)
