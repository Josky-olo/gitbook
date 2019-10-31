---
description: อยากทำ Microservice บนคลาว์เขาทำกันยังไงนะ?
---

# 👶 Azure Service Fabric

ในคอร์สนี้เราจะมาสอนการสร้าง **Microservices Architecture** ทั้งในเครื่องตัวเองและบนคลาว์กันดูบ้างว่ามันจะเป็นยังไง โดยในคอร์สนี้เราจะพามาเล่นคลาว์ของฝั่ง Microsoft ที่ชื่อว่า Azure และเราจะสร้างตัว microservices ไว้กับตัวที่มีชื่อว่า **Service Fabric** ที่ออกแบบมารองรับการทำงานของ architecture นี้โดยเฉพาะครับ

{% hint style="info" %}
คอร์สนี้กำลังค่อยๆเขียนอยู่ ซึ่งจะค่อยๆทยอยอัพเดทลงตรงนี้เรื่อยๆ ส่วนใครที่ไม่อยากพลาดอัพเดทคอร์สนี้หรืออยากรับบทความใหม่ๆ สามารถเข้าไปกด Like เพื่อรับข่าวสารใหม่ๆจาก [**Facebook Blog: Mr.Saladpuk**](https://www.facebook.com/mr.saladpuk) ได้นะครับ 😍
{% endhint %}

{% hint style="warning" %}
ในตอนนี้กำลังไล่ปิดบทความของ [👶 Microservices พื้นฐาน](https://saladpuk.gitbook.io/learn/basic/microservices) อยู่ครับรบกวนไปวิ่งเล่นซัก 2,000 รอบแล้วค่อยกลับมาอ่านต่อนะ เพราะช่วงนี้น่าจะวุ่นวายๆเลยทำให้บทความนี้น่าจะออกมาราวๆวันที่ **16/11**/2019 นี้ครับ
{% endhint %}

{% hint style="success" %}
**แนะนำให้อ่าน**  
ในบทความนี้เราจะพาเล่นคลาว์กัน แต่ถ้าเพื่อนๆยังไม่เคยลองเล่นคลาว์ของ Microsoft เลยก็สามารถเข้าไปลองเล่นได้ที่คอร์ส [👶 Microsoft Azure 101](https://saladpuk.gitbook.io/learn/cloud/azure101) หรือถ้ายังไม่รู้เลยว่าคลาว์คืออะไรก็สามารถเข้าไปศึกษาได้จากบทความนี้เลยครับ [👶 Cloud พื้นฐาน](https://saladpuk.gitbook.io/learn/basic/cloud101)
{% endhint %}

