# 23.Polymorphism

💬 หลังจากที่เห็นน้ำจิ้มตัวแรกในโลกของ object กันไปละ คราวนี้เราจะมาดูความสามารถที่ได้จากการทำ Inheritance ที่เรียกว่า **Polymorphism** กันดูบ้างว่ามันมาช่วยแก้ปัญหาเรื่องอะไรได้อีกบ้างกันครับ

{% embed url="https://www.youtube.com/watch?v=sG0C6PyW9e8&list=PLUjAn8nwWnijERZ3HpzBk7NfSrau74\_lQ&index=40" %}

## 🎥 ตัวอย่างการใช้ Polymorphism

{% embed url="https://www.youtube.com/watch?v=rTlmBkTXggE&list=PLUjAn8nwWnijERZ3HpzBk7NfSrau74\_lQ&index=41" %}

## 🎯 สรุปสั้นๆ

### 👨‍🚀 สิ่งที่สามารถทำได้เมื่อทำ inheritance แล้ว

**1.การเปลี่ยนรูปของคลาส  
Base Class** สามารถเก็บ object ของ **Derived Class** ของมันได้ ซึ่งความสามารถนี้คือหัวใจหลักของ Polymorphism เลยล่ะ

{% hint style="warning" %}
**เจ้าลูกทรพี!**  
ในทางกลับกัน **Derived Class** จะไม่สามารถเก็บ object ของ **Base Class** ได้
{% endhint %}

**2.virtual & override keyword**  
เราสามารถใช้คำสั่ง virtual ให้กับ method ของ Base Class ได้ เพื่อบอกว่าถ้า Derived Class ตัวไหนอยากเปลี่ยนการทำงานไปจาก Base Class ก็สามารถเปลี่ยนได้ โดย

{% hint style="info" %}
**new** keyword  
ถ้า Derived Class อยากตัดความสัมพันธ์จาก Base Class แล้ว ก็สามารถทำได้ด้วยการใช้ new keyword ไปวางไว้หน้า property หรือ method ที่เป็น virtual นั่นเอง
{% endhint %}

**3.base keyword**  
เป็นการบอกว่าให้เรียกใช้งานความสามารถนั้นๆจาก Base Class

**4.sealed keyword**  
เป็นการระบุว่า ณ จุดนั้นๆ ไม่อนุญาติให้คลาสอื่นๆมาสืบทอดหรือเปลี่ยนแปลงมันได้อีกต่อไปแล้ว \(เป็นหมันนั่นเอง\)

{% hint style="info" %}
**sealed class**  
คือคลาสที่ไม่ยอมให้คลาสอื่นสืบทอดได้อีก
{% endhint %}

{% hint style="info" %}
**sealed member**  
คือ member ที่ไม่ยอมให้ Derived Class มาทำการแก้ไขมันได้อีกแล้ว เช่น sealed method นั่นเอง
{% endhint %}

  


