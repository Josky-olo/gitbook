# 24.Abstract Class

💬 เวลาที่เราสร้าง Base class ในบางทีเราอาจจะรู้แค่ มันน่าจะมี method ตัวนี้ไว้นะ แต่ไม่รู้ว่ามันต้องทำงานยังไง เพราะการทำงานของ method นั้นใน Derived Class แต่ละตัวทำงานไม่เหมือนกันเลย ก็เป็นไปได้ หรือในบางทีเราอยากสร้างคลาสที่มีหน้าที่เป็น Base Class เท่านั้นและห้ามนำมันมาใช้สร้าง object ล่ะ? ซึ่งจากคำถามที่ว่ามาทั้งหมดเจ้าตัวที่ชื่อว่า **Abstract Class** จะมาช่วยเราแก้ปัญหาในจุดนี้ขอรับ

{% embed url="https://www.youtube.com/watch?v=BKtYsqF8b2E&list=PLUjAn8nwWnijERZ3HpzBk7NfSrau74\_lQ&index=43" %}

## 🎯 สรุปสั้นๆ

### 👨‍🚀 Abstract Class คือ

แม่แบบของคลาส หรือ Template class นั่นเอง มีแค่โครงสร้างต่างๆไว้ให้ ส่วนคลาสลูกมีหน้าที่ไปกำหนดเอาเองว่าของด้านในจริงๆจะเป็นยังไง แต่ในขณะเดียวกันมันก็มี method ที่สมบูรณ์ในนั้นได้ด้วยนะ

{% hint style="warning" %}
**Abstract class**  
1.เราไม่สามารถสร้าง object จาก abstract class ได้นะ  
2.คลาสที่สืบทอด \(inheritance\) จาก abstract class ไปจะต้องทำการ implement abstract methods ทุกตัวทันทีด้วย  
3.ถ้า abstract class ทำการ inheritance จาก abstract ด้วยกัน จะยังไม่ทำการ implement abstract method ก็ได้นะจุ๊
{% endhint %}

ตัวอย่างการสร้าง Abstract class โดยให้คลาสลูกเป็นคนกำหนดว่าการคำนวณพื้นที่ของรูปแบบแต่ละอย่างเป็นยังไง

```csharp
public abstract class Shape
{
   public abstract double GetArea();
}

public class Circle : Shape
{
   public double Radius { get; set; }
   
   public override double GetArea()
   {
      return 3.141 * Radius * Radius;
   }
}

public class Triangle : Shape
{
   public double Width { get; set; }
   public double Height { get; set; } 
   
   public override double GetArea()
   {
      return 0.5 * Width * Height;
   }
}
```

