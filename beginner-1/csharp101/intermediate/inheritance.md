# 22.การสืบทอด Inheritance

💬 หลังจากที่เราเริ่มใช้งานคลาสมาได้ในระดับนึงละ ซึ่งผมอยากจะบอกว่าที่ผ่านมาทั้งหมดเป็นแค่เพียงน้ำจิ้มของ C\# เท่านั้นเอง!! ดังนั้นในรอบนี้เราจะเริ่มดื่มด่ำกับโลกของ C\# ที่แท้จริงเลยละกัน ซึ่งนั่นคือโลกของ object หรือสิ่งที่เราเรียกว่าการเขียนโปรแกรมแบบ **Object-Oriented Programming** หรือ **OOP** นั่นเอง

{% embed url="https://www.youtube.com/watch?v=ewhjQ6GaKFY&list=PLUjAn8nwWnijERZ3HpzBk7NfSrau74\_lQ&index=38" %}

## 🎥 ตัวอย่างการทำ Inheritance

{% embed url="https://www.youtube.com/watch?v=hXpZ00f6cFI&list=PLUjAn8nwWnijERZ3HpzBk7NfSrau74\_lQ&index=39" %}

## 🎯 สรุปสั้นๆ

### 👨‍🚀 Inheritance

คือการสืบทอดความสามารถจากคลาสนึงไปยังอีกคลาสนึง โดยคลาสที่เป็นต้นแบบเราเรียกมันว่า Base Class หรือคลาสแม่ในภาษาไทย ส่วนคลาสที่สืบทอดความสามารถมาเราเรียกมันว่า **Derived Class** \(บางตำราเรียกมันว่า **Sub Class**\) ส่วนในภาษาไทยเราเรียกมันว่าคลาสลูก

{% hint style="warning" %}
คลาส 1 คลาส สามารถมี Base Class ได้เพียงตัวเดียวเท่านั้นนะ
{% endhint %}

### 👨‍🚀 ความสัมพันธ์

**Derived Class** จะมีทุกอย่างที่ **Base Class** มี เช่น Fields, Methods บลาๆ แต่ยกเว้นสิ่งที่เป็น  **private** แต่ในทางตรงกันข้ามกัน **Base Class** จะไม่รับรู้อะไรที่เกิดจาก **Derived Class** ของมันเลยแม้แต่นิดเดียว

