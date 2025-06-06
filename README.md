


# การเรียนรู้ของเครื่องสำหรับค่าข้อมูลที่มีลักษณะไม่นิ่งในจลาดการเงิน (Thai version.)


โปรเจคนี้ COM0904 จากการแข่งขันรายการ SCiUS Forum 14th วันที่ 25 - 29 เมษายน 2567 สาขา Technology  and Computer ได้รางวัลเหรียญเงิน และ Popular Vote โดยโปรเจดนี้ถูกเขียนขึ้นมาในช่วงมัธยมปลาย หากมีข้อผิดพลาดประการใด ขออภัยใน ณ ที่นี้
โครงงานวิทยาศาสตร์นี้เป็นส่วนหนึ่งของการศึกษาตามหลักสูตร รายวิชา ESC 571 Project  I
โครงการ วมว. โรงเรียนดรุณสิกขาลัย พ.ศ. 2566

**บทคัดย่อ**

ปัจจัยที่หลากหลายในการลงทุนส่งผลให้การได้รับผลตอบแทนตามความคาดหวังทำได้ยาก หนึ่งใน  กลยุทธ์คือ factor investing เป็นการคัดเลือกกลุ่มหุ้นที่สามารถให้ผลตอบแทนตามที่นักลงทุนต้องการโดยการใช้ปัจจัยต่างๆ ที่ส่งผลต่อตลาดหลักทรัพย์ อีกทั้งยังสามารถนำมาคาดการณ์ผลตอบแทนในอนาคตของหุ้น อย่างไรก็ตามข้อมูลสินทรัพย์เป็นค่าข้อมูลที่มีลักษณะไม่นิ่ง (Non-stationarity) ส่งผลให้การคาดการณ์ผลตอบแทนในอนาคตของหุ้นเป็นไปได้ยาก โครงงานนี้จึงใช้ machine learning คือ neural network มาจัดการกับข้อมูลที่มีลักษณะไม่นิ่ง (Non-stationarity) โดยใช้ 2 เทคนิคได้แก่ sliding window และ transfer learning โดยชุดข้อมูลที่ใช้ในโครงงานนี้เป็น SET Index และ factor data หลังจากนั้นโมเดลจะถูกทดสอบและประเมินค่าความคลาดเคลื่อนของการทำนาย เพื่อแสดงประสิทธิภาพของเทคนิคต่างๆ จากผลการทดสอบประสิทธิภาพพบว่าเทคนิค transfer learning มีค่าความคลาดเคลื่อนของการทำนายที่น้อยกว่า เทคนิค sliding window อีกทั้งใช้เวลาในการเทรนและทรัพยากรที่น้อยกว่า

**คำสำคัญ:** Machine Learning/ Factor Investing/ Non-stationarity/ Financial Market


# **1.1**  **ความเป็นมาและความสำคัญของโครงงาน**

การลงทุนในหุ้นได้รับความนิยมในหมู่นักลงทุนตั้งแต่อดีตจนถึงปัจจุบันเนื่องจากผลตอบแทนสูงและมีขั้นตอนการลงทุนที่ง่าย แต่การเลือกหลักทรัพย์และจังหวะในการลงทุนที่เหมาะสมเพื่อให้ได้ผลตอบแทนตามความคาดหวังของนักลงทุนนั้นทำได้ยาก เนื่องจากปัจจัยความเสี่ยงที่หลากหลาย อาทิ ความผันผวนของตลาด สภาพเศรษฐกิจและการเมือง รวมถึงปัจจัยภายนอกที่ส่งผลต่อความผันผวนของราคาหุ้น ปัจจุบันจึงมีการพัฒนาคิดค้นกลยุทธ์การลงทุนหลากหลายรูปแบบเพื่อให้ได้ผลตอบแทนที่ดีที่สุดเมื่อเทียบกับค่าความเสี่ยง ซึ่งการลงทุนแบบ Factor Investing เป็นเครื่องมือสำคัญเพื่อคัดเลือกกลุ่มหุ้นที่สามารถให้ผลตอบแทนตามที่นักลงทุนต้องการโดยการใช้ปัจจัยต่าง ๆ อย่างไรก็ตามข้อมูลสินทรัพย์เป็นค่าข้อมูลที่มีลักษณะไม่นิ่ง (Non-stationarity) ส่งผลให้การคาดการณ์ผลตอบแทนในอนาคตของหุ้นแต่ละตัวเป็นไปได้ยาก

เทคนิค Machine Learning หรือ การเรียนรู้ของเครื่อง จึงได้รับความนิยมและนำมาประยุกต์ใช้กันอย่างแพร่หลายในตลาดการเงิน เนื่องจากปริมาณข้อมูลสินทรัพย์มีจำนวนมากเกินกว่าที่มนุษย์จะสามารถวิเคราะห์ได้ การเลือกใช้โมเดล Machine Learning จะทำให้วิเคราะห์ข้อมูลได้อย่างแม่นยำและรวดเร็วซึ่ง Machine Learning จะสามารถวิเคราะห์ได้ดีกับข้อมูลที่มีลักษณะนิ่ง (Stationarity)  งานวิจัยนี้ได้ศึกษาวิธีใช้ Machine Learning กับข้อมูลที่มีลักษณะไม่นิ่ง (Non-Stationarity) โดยเลือกศึกษา Machine Learning Algorithm คือ Neural Network และ Transfer Learning รวมถึงใช้ข้อมูลปัจจัยต่าง ๆ ของกลยุทธ์ Factor Investing มาคาดการณ์ผลตอบแทนในอนาคตของหุ้นแต่ละตัว เพื่อเป็นแนวทางการเลือกหลักทรัพย์และจังหวะการลงทุนที่เหมาะสมในการสร้างผลตอบแทนตามที่คาดหวังของนักลงทุน

# **1.2 วัตถุประสงค์ของโครงงาน**

1.2.1 เพื่อศึกษาและพัฒนาวิธีการคาดการณ์ผลตอบแทน (Assets return)  ของหุ้นในสภาวะของข้อมูลที่ไม่นิ่ง
1.2.2 เพื่อศึกษาผลจากการใช้ Machine Learning ในการนำมาใช้กับกลยุทธ์ Factor Investing

# **1.3 ขอบเขตของการศึกษา**
1.3.1 ดัชนีราคาตลาดหลักทรัพย์ที่แห่งประเทศไทย (SET Index)
1.3.2 ข้อมูลตั้งแต่ปีศริสต์ศักราช 2013 จนถึงปัจจุบัน
1.3.3 จัดทำ Machine Learning ด้วยวิธี Neural Network และ Transfer learning

# **1.4 ผลที่คาดว่าจะได้รับ**

สามารถนำเทคนิค Machine Learning มาประยุกต์ใช้กับกลยุทธ์ Factor Investing ในข้อมูลที่มีลักษณะ  
ไม่นิ่ง (Non-stationarity) เพื่อเป็นแนวทางให้กับนักลงทุนสำหรับการคาดการณ์ราคาตลาดหลักทรัพย์ในอนาคต

# **อื่น ๆ เพิ่มเติม**
[link Epostor and Extend Abtract](https://citly.me/zhPax)


# ML-for-Non-stationary-Data-in-Financial-Market (Eng version.)
The project COM0904 was presented at the 14th SCiUS Forum, held from April 25 to 29, 2024, under the Technology and Computer category. It was awarded a Silver Medal and the Popular Vote award. The project was developed during the authors’ upper secondary education. The authors would like to extend their apologies for any errors or shortcomings that may remain.  
This scientific project is part of the academic requirements for the course ESC 571: Project I, under the Science Classroom in University Affiliated School Project (SCiUS), Darunsikkhalai School, academic year 2023.

**Abstract**

Various factors in stock investment can make investors find difficulty in achieving expected returns. One of the strategies is factor investing, which involves selecting a group of stocks based on various factors that impact the returns of the portfolio. This allows the prediction of the return. However, the stock price is non-stationary data, which makes it challenging to predict the returns of stocks accurately. This study applies machine learning, i.e., neural network, to deal with non-stationary data together with two techniques: sliding window, and transfer learning. The datasets utilized in this work are historical SET Index and factor data. Then, the model is tested and evaluated with the prediction error to demonstrate the effectiveness of the methods. The experimental results demonstrate that the machine learning model can handle non-stationary data to a certain degree. Furthermore, the transfer learning technique outperforms the sliding window technique in terms of prediction error, requiring less training time and resources.

**Keywords :** Machine learning, Factor investing, SET Index, Non-stationarity, Financial market

# **1.1 Introduction**

Investing in stocks has been a popular choice for investors due to the potential for high returns, but selecting the right securities and timing the investment properly can be difficult.

Factor investing is a strategy of investing in stocks with specific characteristics, which historically have been associated with higher returns. However, asset data is non-stationary , which  changes data over time. Learning from that data is a challenging task for machine learning, which assumes the generation mechanism data  does not change over time.  Therefore, this study, a neural proposes a neural network for non-stationary returns of SET Index prediction, based on two techniques: a sliding window, in which the training datasets are divided into the periods, the different periods of data are learned to obtain the minimum overall loss, and a transfer learning  utilizes knowledge gained from a pre-trained model on a related task, to  effectively navigate the ever-changing data.

# **Other reference**
[link Epostor and Extend Abtract](https://citly.me/zhPax)

