---
description: "\U0001F914 คนเก่งๆเขาการจัดการโปรเจคยังไงให้มีประสิทธิภาพกันนะ ?"
---

# 👦 Agile Methodology

## 😢 ปัญหา

เบื่อไหมในการทำโปรเจคแต่ละรอบเราก็จะเจอแต่ปัญหาเดิมๆ ส่งงานไม่ทัน ทำงานไม่ตรงที่ลูกค้าอยากได้ ทำงานได้ช้ากว่าที่รับปากลูกค้าไว้ และอีกสารพัดปัญหาที่คอยตามหลอกหลอนในการทำโปรเจค แล้วเราจะแก้ปัญหาพวกนี้ยังไงกันดีนะ?

## 😄 วิธีแก้ปัญหา

ปัญหาที่ว่ามานั้นเกิดจาก **"กระบวนการจัดการโปรเจค"** ยังไงล่ะ ถ้าเราวางแผนจัดการมันได้ดีพอ ปัญหาที่ว่ามาก็จะลดน้อยลงมากเลยนะ และทีมที่ทำงานก็ไม่เครียดด้วย โดยในปัจจุบันกระบวนการบริหารจัดการโปรเจคที่เรานิยมใช้กันอยู่นั้น คือเจ้าสิ่งที่เรียกว่า **Agile** นั่นเอง \(อะจาล เอจาล อะไจล์ เอไจล์ แล้วแต่จะออกเสียงเลยเอาที่สบายใจ\)

{% hint style="danger" %}
**หลุมพรางของ Agile**  
หลักในการปฏิบัติของ agile นั้นอ่านแล้วดูเหมือนง่าย แต่ถ้าคนไม่เคยทำไปหัดลองทำส่วนใหญ่ 99% จะทำผิดหมดเลย และยิ่งถ้าไม่ทำเป็นกิจวัตรประจำวัน หรือที่เขาเรียกว่าทำจนเข้าเส้น ผมรับประกันเลยว่า **สิ่งที่คุณทำอยู่มันไม่ใช่ agile**
{% endhint %}

จากที่ร่ายยาวมาทั้งหมดผมอยากให้เพื่อนๆลองทำความเข้าใจในคอร์ส Agile ทั้งหมดนี่จริงๆจังเสียก่อนว่ามันคืออะไร แล้วย้อนกลับมาดูว่าที่กำลังทำอยู่มันใช่ agile หรือเปล่า? และ จริงๆแล้วเราควรจะใช้มันดีไหม? เพราะไม่อย่างนั้น เราก็จะบอกว่า Agile ห่วย ทั้งๆที่เราใช้มันอย่างไม่ถูกวิธีนั่นเอง \(เหมือนกับเอาค้อนไปเลื่อยไม้ แล้วบ่นว่าค้อนมันกากไงงี้เลย\)

## 👑 **ทำความเข้าใจกันก่อน**

บทความนี้เป็นคอร์สหลักเรื่อง **Agile Methodology** ดังนั้นเราจะแค่เกริ่นก่อนว่าความเป็นมาของ agile เป็นยังไง และจะค่อยลงลึกเรื่อยๆในแต่ละเรื่องว่า เราได้อะไรจากเรื่องนี้บ้าง และ ทีมควรปรับเอาเรื่องอะไรไปใช้บ้าง  โดยจะใช้ **Scrum** เป็นตัวอย่างในการอธิบาย

ซึ่งผมขอเคลียก่อนว่า**ผมไม่ได้มาเพื่อที่จะบอกว่าตัวไหนดีกว่าตัวไหน** แต่ผมต้องการจะให้เห็นภาพใหญ่ว่า ตัวเลือกในการบริหารจัดการนั้นมันมีอะไรบ้าง ซึ่งสุดท้ายแล้วเราก็อาจจะไปสร้างวิธีการจัดการของตัวเองออกมาก็ได้ เพราะบริษัทแต่ละที่ก็จะมีวัฒนธรรม ความชอบที่ไม่เหมือนกันนั่นเอง \(ซึ่งในมุมมองผม ไม่ว่าจะเลือกวิธีจัดการแบบไหน agile ก็สามารถเข้าได้กับการทำงานทุกรูปแบบอยู่ดี\)

## 🤔 Agile คืออะไร ?

เอาแบบเร็วๆเลยนะ ราวๆปี 2001 วงการ Software ได้มาถึงจุดที่น่าเป็นห่วง เพราะโปรเจคส่วนใหญ่จะพังลงเมื่อทำไปถึงจุดนึง ดังนั้นเหล่ามหาเทพระดับโลกที่คร่ำหวอดในวงการนี้ เลยนัดรวมตัวกัน มาเถียงกันอย่างเอาเป็นเอาตายเพื่อหาทางออกให้กับปัญหาโลกแตกนี้อยู่หลายวัน \(เทพแต่ละองค์โคตรหัวดื้อเลยจะบอกให้\) จนสุดท้ายเหล่าทวยเทพก็ได้ข้อสรุปที่เห็นพ้องต้องกันว่าจะแก้ปัญหาเรื่องนี้ยังไงดี โดยได้ข้อสรุปที่เป็น**หัวใจ 4 ข้อ**ออกมาเรียกว่า **Agile manifesto** และ **หลักในการปฏิบัติ 12 ข้อ** หรือที่เราเรียกว่า **12 Principles of Agile Software** จากที่ว่ามาเหมือนทุกอย่างจะจบลงได้ด้วยดี ... ซะเมื่อไหร่!! เพราะทั้งหมดที่ว่ามามันเป็นแค่**หลักคิดแบบกลางๆเท่านั้น** มันไม่ได้บอกเลยว่าต้องทำยังไง! ดังนั้นเทพแต่ละองค์ก็เอาหลักคิดนี้ไปสร้างเป็นการบริหารจัดการซอฟต์แวร์ของตัวเองต่อนั่นเอง!!

![http://agilemanifesto.org](../../.gitbook/assets/background.jpg)

จากที่ร่ายยาวมา เราลองไปดูก่อนว่าข้อสรุปของเหล่าองค์เทพได้ทิ้งอะไรไว้ให้เรากันบ้าง

## 🤔 Agile Manifesto มีไรบ้าง ?

บทความนี้ศักสิทธิ์มากเลยอยากให้เพื่อนๆได้ลองไปอ่านของจริงดูจากลิงค์นี้ [Agile Manifesto](http://agilemanifesto.org/) ซึ่งแปลออกมาก็ราวๆนี้

> 1. **คนและการมีปฏิสัมพันธ์กัน** มากกว่าการทำตามขั้นตอนและเครื่องมือ
> 2. **ซอฟต์แวร์ที่นำไปใช้งานได้จริง** มากกว่าเอกสารที่ครบถ้วนสมบูรณ์
> 3. **ร่วมมือทำงานกับลูกค้า** มากกว่าการต่อรองให้เป็นไปตามสัญญา
> 4. **การตอบรับกับการเปลี่ยนแปลง** มากกว่าการทำตามแผนที่วางไว้

เป็นยังไงบ้างซาบซึ้งในรสพระธรรมเลยใช่ไหม ... ก็อย่างที่บอกว่า **มันเป็นแนวคิดอย่างเดียวเลย** ไม่ได้บอกว่าต้องทำอะไรบ้าง ซึ่งคือหัวใจหลักของมันมีแค่นี้จริงๆนะ ดังนั้นผมจะแปลให้ฟังใหม่ว่า

**การทำ software มันต้องร่วมมือกันทำมันถึงจะสำเร็จ** โดยให้เราเน้นไปที่เรื่อง

1. **เน้นให้คนแต่ละคนได้พูดคุยทำความเข้าใจกันในทุกๆเรื่องๆ** ดีกว่าให้แต่ละฝ่ายคอยทำตามขั้นตอนที่วางไว้ 1234 ถ้าใครทำไม่ถูกโดนตัดหัว และอย่าไปสนใจเครื่องมือมากนัก \(สังเกตได้จากงานราชกาลประเทศไรไม่รู้ ต้องทำตามขั้นตอนอืดอาดวุ่นวาย เพื่อที่ได้ดำเนินการกัน ทั้งๆที่เอ็งนั่งข้างๆกัน กินข้าวเที่ยงด้วยกันเนี่ยนนะ\)
2. **เน้นให้เราทำซอฟต์แวร์ที่มันเอาไปใช้งานได้จริง มันแก้ปัญหาลูกค้าได้จริงๆ** ดีกว่าไปไล่ทำตามเอกสารที่ลูกค้าเขียนไว้ 2,048 ข้อ \(เหมือน TOR ของประเทศไรก็ไม่รู้ พูดแล้วมีโมโห พอทำเสร็จก็ส่งงานได้อยู่หรอก แต่ขนาดคนเขียนเองยังรู้เลยว่ามันไม่ได้แก้ปัญหาของเอ็งหรอกคุณลูกค้าที่เคารพ\)
3. **เน้นให้เรากับลูกค้าได้พูดคุยร่วมกันแก้ปัญหา เพื่อหาผลลัพท์ที่ดีที่สุดกับสถานะการณ์จริงของลูกค้า** ดีกว่าไปต่อรองว่า อ้าวก็ลูกค้าบอกว่าอยากได้ไอ้นี่ ผมก็ทำไอ้นี่ตามสัญญาที่ว่าไว้แล้วนิ! ตามในหนังสือสัญญาเลยนะ ไม่เชื่อดูดิ!
4. **เน้นให้ทีมยอมรับในความเป็นจริง ว่าในวงการนี้ทุกอย่างเปลี่ยนแปลงได้เสมอ และทีมพร้อมที่จะเปลี่ยนเพื่อของที่ตอบโจทย์ลูกค้าได้มากกว่า** ดีกว่าไปยึดติดกับแผนที่วางไว้แล้ว ซึ่งมันอาจจะไม่ตอบโจทย์ลุกค้าแล้วก็ได้ \(พูดให้เห็นภาพคือ มันถึงเวลานอนแล้ว แต่บ้านดันไฟไหม้ขึ้นมา คุณยังจะยึดแผนเดิมคือเข้านอนเหรอ?\)

{% hint style="success" %}
**หัวใจหลักของ Agile**  
จากที่เราเห็นเราก็จะค้นพบว่า **หัวใจหลักในการแก้ปัญหาของ Agile คือการใช้เหตุผลและข้อเท็จจริงคุยกัน เพื่อช่วยกันหาทางออกที่ดีที่สุดของเราและลูกค้านั่นเอง**
{% endhint %}

## 🤢 Agile คือบ้าไรเนี่ย?

ก่อนที่จะไปต่อผมอยากให้เข้าใจก่อนว่า **Agile มันมีแต่แนวคิด ไม่ได้บอกว่าเราต้องทำอะไรบ้าง** ดังนั้นผมจะยังไม่พูดถึงหลักปฏิบัติ 12 ข้อว่ามีอะไรบ้าง เพราะไม่งั้นคนที่จะเหลือรอดอ่านบทความผมต่อคงจะเข้าใกล้ 0 เข้าไปเรื่อยๆ ดังนั้นเราไปดูกันก่อนว่า ถ้าเราใช้ Agile แบบถูกวิธีจริงๆเราจะได้อะไรบ้าง

## 🤔 ทำ Agile แล้วได้อะไร ?

ขอเขียนแบบรวมๆไม่ได้ไล่ความสำคัญแบบคร่าวๆละกันว่า

* ทีมและลูกค้าไม่เครียด และ ต่างฝ่ายต่างเชื่อใจกันมากขึ้น
* ทีมสามารถส่งงานได้ตามกำหนด และปรับแก้แผนงานได้
* ทุกคนคุยกันช่วยกันทำงาน ไม่ใช่หุ่นยนต์ที่เอาแต่รอรับคำสั่งรายวัน
* งานที่เราส่งให้ลูกค้า เป็นของที่ตอบโจทย์ลูกค้าที่แท้จริง
* ทีมและลูกค้าสามารถวางแผนงานและค่าใช้จ่ายได้ใกล้เคียงความเป็นจริงมากขึ้น
* งานที่ทีมทำจะมีคุณภาพดีขึ้นกว่าเดิม
* ค่าใช้จ่ายลดลง ทั้งทีมและลูกค้าเลย

มันไม่ได้มีดีแค่นี้หรอก แต่ผมเชื่อว่าเพียงแค่นี้ก็สามารถ**แก้ปัญหาส่วนใหญ่ที่เราเจอกันอยู่**ทุกวันอยู่แล้ว

## 🤔 อะไรบ้างที่ใช้ Agile?

อย่างที่บอกว่า Agile เป็นแค่หลักในการคิดเท่านั้น ดังนั้นมันเลยมีรูปแบบในการบริหารจัดการหลายตัวเลยที่เอาหลักการนี้ไปใช้ เช่น `Scrum`, `Extreme Programming (XP)`, `Lean & Kanban` บลาๆ ซึ่งแต่ละตัวเป็นยังไงบ้างเดี๋ยวเราค่อยไปลงรายละเอียดกันอีกที

## 🤔 หลักปฏิบัติ 12 ข้อมีไรบ้าง?

ตอนแรกว่าจะไม่เอามาลงละ เพราะไม่งั้นบทความนี้จะออกมาเป็หนังสือวิชาการเลยซึ่งน่าเบื่อมาก ดังนั้นผมเลยขอให้ไปอ่านเองจากลิงค์นี้ละกัน[ ภาษาอังกฤษ](http://agilemanifesto.org/principles.html) กับ [ภาษาไทย](http://agilemanifesto.org/iso/th/principles.html) เลือกอ่านเอาเองละกัน

## 🧭 เนื้อหาของคอร์สทั้งหมด

สิ่งที่จะได้จากคอร์สนี้คือ เข้าใจว่า Agile คืออะไร ส่วนหลักในการทำ agile นั้นส่วนใหญ่ในไทยเราจะดังในเรื่องของ **Scrum** \(สกรัม: สะ-กรัม อย่ามาอ่านว่า สก-รัม ให้ผมได้ยินนะผมจะกลั้นหัวเรอะไว้ไม่อยู่\) ดังนั้นเดี๋ยวเราจะมาลองดูกันว่าแต่ละพิธีกรรมของเขามีอะไรบ้าง และหัวใจหลักจริงๆในแต่ละพิธีกรรมมันมีอะไรบ้าง

{% hint style="info" %}
คอร์สนี้กำลังค่อยๆเขียนอยู่ ซึ่งถ้าเขียนเสร็จก็จะเอามาลงไว้ในหน้านี้แหละ ถ้าไม่อยากพลาดอัพเดท ก็ไปกดติดตามได้จากลิงค์นี้เบย [**Saladpuk Facebook**](https://facebook.com/mr.saladpuk)
{% endhint %}

**ลำดับเรื่องที่จะเล่าแบบคร่าวๆ**

{% page-ref page="agile-in-a-nutshell.md" %}

{% page-ref page="sdlc.md" %}

{% page-ref page="code-review.md" %}

* Scrum คืออะไร? และมันจะช่วยเราได้ยังไงในภาพรวม
* แต่ละ Sprint เขาทำอะไรบ้าง
* หน้าที่และบทบาทของ Scrum มีอะไร? และต้องทำไรบ้าง?
* มันเยอะมากเดี๋ยวค่อยว่ากันคิดอะไรออกเดี๋ยวเอามาเขียนไว้ตรงนี้ละกัน

## 🎯 บทสรุป

**Agile** คือ**หลักในการบริหารจัดการ** ที่สามารถ**เอาไปใช้กับอะไรก็ได้**ไม่จำเป็นต้องเป็นซอฟต์แวร์อย่างเดียวเท่านั้น โดยมันมีหัวใจหลักคืออการทำงานร่วมกันเป็นทีม โดยตั้งอยู่บทเหตุและผลที่เป็นข้อเท็จจริง เพื่อให้แต่ละฝ่ายช่วยกันหาทางออกที่ดีที่สุดให้กันและกัน ซึ่งในวงการซอฟต์แวร์นั้นมีการนำหลักนี้ไปปรับใช้เป็นวิธีการของตัวเองอยู่หลายตัว และของที่ได้จากการทำ agile โดยรวมแล้วมีผลดีมากกว่าผลเสีย เพราะ**ทีมจะไม่ติดหนี้**ในหลายๆเรื่อง และ**สร้างความเชื่อใจให้กับทุกฝ่าย**นั่นเอง

