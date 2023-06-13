# Topic Modeling From Personalized Medicine: Redefining Cancer Treatment 📝💊

  Project นี้เป็นส่วนหนึ่งของวิชา CHHD304 การแพทย์แม่นยำเบื้องต้น (Introduction to Precision Medicine) ภาคเรียนที่ 1 ปีการศึกษา 2565 โดยข้อมูลที่ใช้มาจาก kaggle: [Personalized Medicine: Redefining Cancer Treatment](https://www.kaggle.com/competitions/msk-redefining-cancer-treatment/overview)

### 💡Objective
- เพื่อศึกษาว่าใน Dataset นี้ แต่ละ Class (ทั้ง 9 class) มีความหมายอย่างไร โดยใช้การทำ Topic Modeling เข้ามาช่วย 

เนื่องจากในรายละเอียดของ Dataset นี้ ไม่ได้ระบุไว้ว่าแต่ละ Class มีความหมายอย่างไรเลย ซึ่ง**การทำความเข้าใจข้อมูล**เป็นสิ่งที่สำคัญใน Data Science Process ซึ่งจะทำให้สามารถนำไปวิเคราะห์ต่อได้อย่างมีประสิทธิภาพ

สาเหตุที่กลุ่มพวกเราเลือกทำ Topic Modeling เพราะเป็นสิ่งที่กลุ่มเราไม่เคยลองทำมาก่อนเลย นี่จึงถือเป็นการเรียนรู้สิ่งใหม่ ๆ ไปด้วย และ Dataset นี้เป็นข้อมูล text ที่มีความยาวอย่างมาก จึงมีความน่าสนใจที่จะทำ Topic Modeling นอกจากนี้กลุ่มอื่น ๆ ที่ได้หัวข้อเดียวกับกลุ่มเรา ได้เลือกทำ Classification ไปแล้ว กลุ่มเราเลยตัดสินใจไม่ทำซ้ำจะได้ไม่เกิดข้อเปรียบเทียบขึ้น


### 📝สมาชิกกลุ่ม
- Rujikorn Sangsumrit
- [Piyatida Meesatean](https://github.com/Piyati)
- [Ornrakorn Mekchaiporn](https://github.com/mill-ornrakorn)

## Data source 📁
ข้อมูลที่ใช้มาจาก kaggle: [Personalized Medicine: Redefining Cancer Treatment](https://www.kaggle.com/competitions/msk-redefining-cancer-treatment/overview) ซึ่งในข้อมูลนี้มีหลายไฟล์มาก แต่ในการทำ Topic Modeling เราจะใช้ไฟล์ ```training_variants``` และ ```training_text``` 

- training_variants
  1. ID = (the id of the row used to link the mutation to the clinical evidence)
  2. Gene (the gene where this genetic mutation is located)
  3. Variation (the aminoacid change for this mutations)
  4. Class (1-9 the class this genetic mutation has been classified on)

<p align="center">
<img src="https://github.com/mill-ornrakorn/Topic-Modeling-From-Personalized-Medicine-Redefining-Cancer-Treatment/blob/main/pic%20for%20readme/3.jpg?raw=true" alt= "training_variants" height="200">
</br>
ตัวอย่างข้อมูลจากไฟล์ training_variants
</p>


- training_text
  1. ID (the id of the row used to link the clinical evidence to the genetic mutation)
  2. Text (the clinical evidence used to classify the genetic mutation)



<p align="center">
<img src="https://github.com/mill-ornrakorn/Topic-Modeling-From-Personalized-Medicine-Redefining-Cancer-Treatment/blob/main/pic%20for%20readme/4.jpg?raw=true" alt= "training_text" height="200">
</br>
ตัวอย่างข้อมูลจากไฟล์ training_text
</p>


## Exploratory Data Analysis (EDA) 📊
- **ความยาวของ Text ในข้อมูล**
<p align="center">
<img src="https://github.com/mill-ornrakorn/Topic-Modeling-From-Personalized-Medicine-Redefining-Cancer-Treatment/blob/main/pic%20for%20readme/0.jpg?raw=true" alt= "boxplot" height="90">
</p>

<p align="center">
<img src="https://github.com/mill-ornrakorn/Topic-Modeling-From-Personalized-Medicine-Redefining-Cancer-Treatment/blob/main/pic%20for%20readme/1.jpg?raw=true" alt= "histo" height="300">
</p>

จากทั้งสองกราฟ จะเห็นว่าข้อมูลนี้เป็นข้อมูล text ที่มีความยาวอย่างมาก ส่วนใหญ่จะมีความยาวประมาณ 5000 เลย 

</br>

เพื่อให้เห็นภาพมากขึ้นเรายกตัวอย่างข้อมูลจาก column TEXT **เพียง 1 row** โดยมีความยาว (str.len()) อยู่ที่ 39,672
<p align="center">
<img src="https://github.com/mill-ornrakorn/Topic-Modeling-From-Personalized-Medicine-Redefining-Cancer-Treatment/blob/main/pic%20for%20readme/2.jpg?raw=true" alt= "text" height="400">
</p>


- **จำนวนแต่ละ Class ในข้อมูล**
<!--เดี๋ยวมาเพิ่ม -->

- **จำนวน Gene ที่พบมาก 10 อันดับ**
<!--เดี๋ยวมาเพิ่ม -->

- **จำนวน Variation ที่พบมาก 10 อันดับ**
<!--เดี๋ยวมาเพิ่ม -->

- **Wordcloud**
<p align="center">
<img src="https://github.com/mill-ornrakorn/Topic-Modeling-From-Personalized-Medicine-Redefining-Cancer-Treatment/blob/main/pic%20for%20readme/wordcloud.png?raw=true" alt= "Wordcloud" height="300">
</p>


- **จำนวน Text ที่พบมาก 10 อันดับ**
<!--เดี๋ยวมาเพิ่ม -->

- **มี Text ที่เหมือนกัน แต่อยู่คนละ Class**
<!--เดี๋ยวมาเพิ่ม -->

- **สรุปสิ่งสิ่ที่ได้จากการทำ EDA**
  - จำนวนข้อมูลในแต่ละ Class ของข้อมูล train มีไม่เท่ากัน
  - ข้อมูลในบาง Class มีจำนวนน้อยเกินไป
  - column text ในบาง row เหมือนกันทั้งหมด
  - ความหมายของ Class ไม่ชัดเจน



## Modeling 

<p align="center">
<img src="https://github.com/mill-ornrakorn/Topic-Modeling-From-Personalized-Medicine-Redefining-Cancer-Treatment/blob/main/pic%20for%20readme/7.jpg?raw=true" alt= "text" height="300">
</p>

**📍note that:** รายละเอียดการทำ Data Preparation สามารถดูได้เพิ่มได้ใน 
[Code](https://github.com/mill-ornrakorn/Topic-Modeling-From-Personalized-Medicine-Redefining-Cancer-Treatment/blob/main/Topic_Modeling_From_Personalized_Medicine_Redefining_Cancer_Treatment.ipynb) 
นะคะ ซึ่งจะมีการจัดการกับ na ในข้อมูล, merge ทั้งสองไฟล์เข้าด้วยกัน, ลบสัญลักษณ์, เปลี่ยนเป็นตัวพิมพ์เล็ก, และลบ Stopwords


<p align="center">
<img src="https://github.com/mill-ornrakorn/Topic-Modeling-From-Personalized-Medicine-Redefining-Cancer-Treatment/blob/main/pic%20for%20readme/8.jpg?raw=true" alt= "text" height="200">
</p>

ในการทำ Topic Modeling จะใช้ Latent Dirichlet Allocation (LDA) โดยลักษณะของโมเดลเป็น 
Unsupervised learning [(1)](http://ir-ithesis.swu.ac.th/dspace/bitstream/123456789/1243/1/gs621130237.pdf)


## Result
<!--เดี๋ยวมาเพิ่ม -->








## Conclusion & Discussion
จากการทำ Topic Modeling พวกเรา พบว่า
- หลาย ๆ Class มีเนื้อหาที่ใกล้เคียงกัน
- แต่ในบาง Class มีเนื้อหาไปในทิศทางเดียวกัน เช่น Class 9 พูดถึง sf3b1 ชัดเจน แต่ยังต้องอาศัยความรู้ในการตีความ Topic ค่อนข้างมาก
- ด้วยเวลาที่จำกัดทำให้พวกเราไม่สามารถตีความทีละ Topic ได้

สาเหตุที่หลาย ๆ Class มีเนื้อหาที่ใกล้เคียงกันอาจเป็นเพราะ ข้อมูลชุดนี้ไม่สะอาด ซึ่งหมายถึง text ซ้ำกันเยอะมาก ทำให้ไม่สามารถหาความแตกต่างในแต่ละ Class ได้อย่างชัดเจน

ในการศึกษาครั้งหน้าพวกเราจึงอยาก
- ทำความเข้าใจข้อมูลให้ละเอียดมากขึ้น เช่น หาหน้าที่และความเกี่ยวข้องกันของ Gene หรือ Variation ในแต่ละ Class
- ลองใช้ grid search กับ LDA
- ลองนำข้อมูลที่ทำ Lemmatisation เข้า model ดู
- ลองใช้ Model อื่น ๆ ในการทำ Topic Modeling


## References 📖
1. ปียวรรณ ทองพลอย. การวิเคราะห์ข้อความภาษาไทยเกี่ยวกับการตั้งครรภ์ด้วยวิธีการสร้างแบบจำลองหัวข้อ (TOPIC MODELING) [อินเทอร์เน็ต]. 2563. [เข้าถึงเมื่อ 22 พ.ย. 65]. เข้าถึงได้จาก:
http://ir-ithesis.swu.ac.th/dspace/bitstream/123456789/1243/1/gs621130237.pdf