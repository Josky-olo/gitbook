# 9.การตัดสินใจด้วย Switch statements

💬 หลังจากที่เราได้เห็นการตัดสินใจของคอมพิวเตอร์ผ่านคำสั่ง **IF statements** กันไปบ้างละ ในรอบนี้เราลองมาดูการตัดสินใจแบบง่ายๆด้วยคำสั่งที่เรียกว่า **Switch statements** กันดูบ้างนะครับ

{% embed url="https://www.youtube.com/watch?v=futpp6q8l9c&list=PLUjAn8nwWnijERZ3HpzBk7NfSrau74\_lQ&index=17" %}



## 🎯 สรุปสั้นๆ

### 👨‍🚀 การเขียน Switch แบบมาตรฐาน

```text
switch( EXPRESSION )
{
  case PATTERN1:
     // ถ้า expression ตรงกับ pattern 1 จะเข้ามาที่งานที่นี่
     break;
  case PATTERN2:
     // ถ้า expression ตรงกับ pattern 2 จะเข้ามาที่งานที่นี่
     break;
  default:
     // ถ้า expression ไม่ตรงกับ pattern ไหนเลยจะเข้ามาทำงานที่นี่
     break;
}
```

{% hint style="info" %}
**เกร็ดความรู้ 1**  
ในการเขียน switch นั้นเราสามารถใส่วงเล็บ { } ลงไปใน case หรือ default ได้นะจ๊ะ เพื่อเป็นการบอกว่า scope ของการทำงานอยู่ที่ไหน ตามตัวอย่าง code ด้านล่าง
{% endhint %}

```text
switch( EXPRESSION )
{
  case PATTERN1:
     {
       // ถ้า expression ตรงกับ pattern 1 จะเข้ามาที่งานที่นี่
       break;
     }
   ...
}
```

{% hint style="info" %}
**เกร็ดความรู้ 2**  
เราสามารถรวม case ที่ทำงานเหมือนกันเอาไว้ด้วยกันได้ และ รวมถึงการรวม case default ด้วยเช่นกัน ตาม code ด้านล่าง
{% endhint %}

```text
switch( EXPRESSION )
{
  default:
  case PATTERN1:
  case PATTERN2:
  case PATTERN3:
     {
       // ถ้า expression ตรงกับ pattern 1,2,3 
       // หรือไม่ตรงกับ pattern อื่นๆเลยจะเข้ามาที่งานที่นี่
       break;
     }
   ...
}
```

### 👨‍🚀 การเขียน switch โดยใช้ Type pattern

ในภาษา C\# รุ่นใหม่ๆจะรองรับการใช้สิ่งที่เรียกว่า Type pattern แล้ว โดยเราสามารถเอาชนิดข้อมูลมาใช้เป็นเงื่อนไขได้

```text
switch( EXPRESSION )
{
  case int a:
       // ถ้า expression เป็น int จะเข้ามาที่งานที่นี่
       break;
  case double b:
       // ถ้า expression เป็น double จะเข้ามาที่งานที่นี่
       break;
   ...
}
```

### 👨‍🚀 การเขียน switch โดยใช้ When clause

```text
switch( EXPRESSION )
{
  case int a when a > 12:
       // ถ้า expression เป็น int และมีค่ามากกว่า 12 จะเข้ามาที่งานที่นี่
       break;
   ...
}
```

