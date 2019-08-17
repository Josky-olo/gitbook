---
description: Software Design
---

# 🤴 Design Patterns

## ❓ มันคืออะไร ?

**Design patterns** เป็นแนวคิดในการแก้ปัญหาที่เราเจอบ่อยๆในการออกแบบซอฟต์แวร์ ซึ่งถ้าเรามี `ปัญหา` แล้วปัญหานั้นมีลักษณะตรงกับ `pattern` ไหนก็ตาม เราก็จะสามารถนำแนวคิดของ pattern นั้นๆไปแก้ปัญหาของเราได้เลย

**Pattern** แต่ละตัวจะเป็นแค่ `แนวคิดในการแก้ไขปัญหา` เท่านั้น ซึ่งมันไม่ได้บอกชัดเจนว่าเราต้องมีทำอะไรบ้างเพื่อจะแก้ปัญหาที่เจอ ดังนั้นวิธีการแก้ปัญหาที่เจอจะขึ้นกับการตัดสินใจของ developer เอง

## 😒 ข้อดีข้อเสีย

### 👍 ข้อดี

* เมื่อเกิดปัญหาในการออกแบบซอฟต์แวร์ สามารเอา pattern มาแก้ปัญหาได้เลย
* สามารถรับมือเมื่อเจอกับ business requirement ที่ซับซ้อนได้
* ลดการเกิด coupling, โค้ดยืดหยุ่นขึ้น, โค้ดนำกลับมาใช้ใหม่ได้

### 👎 ข้อเสีย

* Design pattern แต่ละตัวไม่ได้เข้าใจง่ายสำหรับ developer มือใหม่
* Developer ส่วนใหญ่จะนำ design pattern ไปใช้เลย โดยไม่ได้ชั่งน้ำหนักก่อนใช้ให้ดีก่อน ทำให้โค้ดมีความซับซ้อนเพิ่มขึ้นโดยไม่จำเป็น

{% hint style="danger" %}
**คำเตือน**  
การนำ design pattern ไปใช้ไม่ใช่เรื่องเท่ เพราะมันมี cost \(memory, processing overhead & complexity\) ของมันค่อนข้างสูง ดังนั้นก่อนใช้ให้ **ชั่งน้ำหนัก ข้อดี/ข้อเสีย** ให้ดีก่อน ไม่งั้นโค้ดจะทำงานได้แต่ maintenance ยากขึ้นโดยใช่เหตุ **ดังนั้นอย่าเมากาวแล้วตะบี้ตะบันเอา pattern ไปใช้เลยตลอดเวลา** \(อาตตามาเตือนแล้วนะ\)
{% endhint %}

## 👑 กลุ่มของ patterns ต่างๆ

Pattern ทั้งหมดถูกแบ่งออกเป็น 3 กลุ่ม ตามวัตถุประสงค์ในการแก้ไขปัญหาของมัน โดยแต่ละกลุ่มจะช่วยให้โค้ดนั้น ลดการเกิด coupling, มีความยืดหยุ่นขึ้นและนำกลับมาใช้ใหม่ได้

### 🦈 **Creational patterns**

> ช่วยในการออกแบบเมื่อจะสร้าง object ต่างๆ

{% page-ref page="creational-patterns/abstract-factory.md" %}

{% page-ref page="creational-patterns/builder.md" %}

{% page-ref page="creational-patterns/factory-method.md" %}

{% page-ref page="creational-patterns/prototype.md" %}

{% page-ref page="creational-patterns/singleton.md" %}

### 🦈 **Structural patterns**

> ช่วยในการออกแบบโครงสร้างของ class ต่างๆ

{% page-ref page="structural-patterns/adapter.md" %}

{% page-ref page="structural-patterns/bridge.md" %}

* ~~Composite pattern~~

{% page-ref page="structural-patterns/decorator.md" %}

{% page-ref page="structural-patterns/facade.md" %}

* ~~Flyweight pattern~~

{% page-ref page="structural-patterns/proxy.md" %}

### 🦈 **Behavioral patterns** 

> ช่วยในการออกแบบให้ class ต่างๆทำงานร่วมกัน

{% page-ref page="behavioral-patterns/chain-of-responsibility.md" %}

{% page-ref page="behavioral-patterns/command.md" %}

* ~~Interpreter pattern~~

{% page-ref page="behavioral-patterns/iterator.md" %}

{% page-ref page="behavioral-patterns/mediator.md" %}

{% page-ref page="behavioral-patterns/memento.md" %}

{% page-ref page="behavioral-patterns/observer.md" %}

{% page-ref page="behavioral-patterns/state.md" %}

{% page-ref page="behavioral-patterns/strategy.md" %}

{% page-ref page="behavioral-patterns/template-method.md" %}

{% page-ref page="behavioral-patterns/visitor.md" %}

{% hint style="warning" %}
ตัว pattern ที่เหลือโอกาสใช้มันค่อนข้างต่ำมากถ้ามีเวลาผมจะมาทำต่อนะครับ
{% endhint %}

{% hint style="info" %}
เนื้อหานี้ผมเคยเขียนครั้งแรกไว้ที่ Github ถ้าสนใจก็เข้าไปดูได้จากลิงค์ด้านล่างนี้เลยนะครับ  
[https://github.com/saladpuk/design-patterns](https://github.com/saladpuk/design-patterns)
{% endhint %}

