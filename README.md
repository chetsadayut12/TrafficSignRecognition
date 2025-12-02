# Traffic Sign Recognition for Driver Assistance System

โปรเจกต์นี้เป็นระบบจำแนกป้ายจราจรจำนวน **43 คลาส** โดยใช้โมเดล **Convolutional Neural Network (CNN)**  
พร้อมเว็บแอปให้ผู้ใช้สามารถอัปโหลดรูปภาพป้ายจราจรเพื่อทำนายผลแบบเรียลไทม์  
ออกแบบมาเพื่อเป็นส่วนหนึ่งของระบบช่วยเหลือผู้ขับขี่ (Driver Assistance System)

---

## Dataset (GTSRB)

ใช้ชุดข้อมูล **German Traffic Sign Recognition Benchmark (GTSRB)**  
ดาวน์โหลดจาก Kaggle:  
https://www.kaggle.com/datasets/adityajn105/gtsrb-german-traffic-sign

ภายในประกอบด้วยป้ายจราจรจำนวน 43 คลาส เช่น  
- Speed limit (20–120 km/h)  
- Stop  
- Yield  
- No entry  
- Dangerous curve  
- Go straight / turn left / turn right  
และอีกมากมาย

---

## Model Architecture

โมเดลถูกสร้างด้วย **CNN แบบลึกหลายชั้น**  
รายละเอียดตามโค้ด:

### Convolution + Pooling Layers
- Conv2D (32 filters, 3×3, ReLU)  
- Conv2D (32 filters, 3×3, ReLU)  
- MaxPooling2D (2×2)  
- Dropout(0.25)

- Conv2D (64 filters, 3×3, ReLU)  
- Conv2D (64 filters, 3×3, ReLU)  
- MaxPooling2D (2×2)  
- Dropout(0.25)

### Fully Connected Layers
- Flatten  
- Dense(256, ReLU)  
- Dropout(0.5)  
- Dense(43, Softmax)

### Optimizer / Loss
- Optimizer: **Adam**  
- Loss: **Sparse Categorical Crossentropy**  
- Metrics: **Accuracy**

---

## Training Result

โมเดลถูกเทรนทั้งหมด **40 epochs**  
ขนาด batch: **32**

### Final Validation Result:
- **Validation Accuracy:** ~0.998  
- **Validation Loss:** ~0.016  

### Classification Report (Precision / Recall / F1-score)
ทุกคลาสมีคะแนน **1.00** เกือบทั้งหมด  
ถือว่าความแม่นยำของโมเดลอยู่ในระดับสูงมาก

---

## Web Application (Streamlit)

มีเว็บแอปให้ทดสอบโมเดลแบบง่าย ๆ

### ฟีเจอร์ของเว็บ
- อัปโหลดภาพป้ายจราจร (JPG/PNG)  
- แสดงภาพตัวอย่าง  
- รันโมเดลเพื่อทำนาย  
- แสดงชื่อป้ายและ class number  


---

## สรุป

โปรเจกต์นี้ประกอบด้วย  
- โมเดล CNN ที่แม่นยำสูง (~99.7%+)  
- รองรับป้ายจราจร 43 คลาส  
- มีเว็บแอปใช้งานได้จริง  

