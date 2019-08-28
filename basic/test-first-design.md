---
description: พลังที่แท้จริงของการออกแบบโดยใช้ Test-Driven Development (TDD)
---

# 👦 ⏳Test-First Design

รอบนี้จะโชว์พลังที่แท้จริงของ **Test-Driven Development \(TDD\)** และ **Pair Programming** ให้ดูว่ามันช่วยเรื่อง **Code Design** ได้ยังไง ซึ่งในบทความนี้แปลจากหนังสือ Agile Principles, Patterns, and Practices in C\# \(Robert C. Martin\) เพราะอ่านแล้วรู้สึกว่ามันทำให้เห็นศักยภาพการทำ **Test-First** และ **Pair Programming** ได้ดีมากๆ เลยอยากให้เพื่อนๆได้เอาไปศึกษาปรับใช้ดู

{% hint style="danger" %}
## บทนี้ยังไม่เสร็จกำลังเขียนอยู่
{% endhint %}

{% hint style="success" %}
**ความเข้าใจผิดกับการเขียนเทส**  
Developer หลายๆคนจะบ่นว่า _"การเขียนเทสทำให้งานช้า"_ เลยหลีกเลี่ยงไม่ยอมเขียนเทสก่อนเขียนโค้ด แต่ในขณะที่ครูระดับระดับตำนานและนักเขียนโค้ดระดับเทพทุกคนเขาเขียนเทสกันก่อนเขียนโค้ดทุกคน และงานส่วนใหญ่ก็ชี้ออกมาแล้วว่า **"การเขียนเทสก่อนสุดท้ายมันเร็วกว่าการไม่เขียนเทสเยอะมาก"**
{% endhint %}

![Agile Principles, Patterns, and Practices in C\# \(Robert C. Martin\)](../.gitbook/assets/image%20%286%29.png)

## A Programming Episode

ในหนังสือบทนี้เขาจะแสดงหลักการเขียนโค้ดของ Agile ให้ดู ซึ่งเป็นเหตุการณ์ที่เกิดขึ้นจริงจากมหาเทพทั้งสอง **Robert S. Koss \(ป๋าโรเบิร์ด\)** กับ **Robert C. Martin \(ลุงบ๊อบ\)** จะมาทำ Pair Programming เพื่อช่วยกันเขียนโปรแกรมคำนวณคะแนนเกมโบลิ่ง

{% hint style="info" %}
**Pair Programming**  
คือการให้ developer 2 คนมานั่งทำงานโดยใช้คอมเครื่องเดียวกันเขียนโค้ด โดยที่ทั้ง 2 คนจะต้องคุยกันตลอดเวลาว่ากำลังจะเขียนโค้ดเรื่องอะไร จะออกแบบยังไง ทำไมต้องทำแบบนี้ ซึ่งจะสลับกันเขียนโค้ด และในขณะเดียวกันฝ่ายที่ไม่ได้เขียนโค้ดจะต้องคอยดูแลความถูกต้องและคอยแย้งเพื่อหาผลลัพท์ที่ดีที่สุดในการเขียนโค้ดในครั้งนั้น _\(ไม่ใช่หยิบมือถือขึ้นมาเล่นตอนที่ไม่ได้เขียนโค้ด_ 😡_\)_
{% endhint %}

### 🎳 กฏิกาเกมโบลิ่ง \(ถ้ารู้กฏอยู่แล้วข้ามได้เลย\)

> โบลิ่งเป็นเกมที่เราต้องโยนบอลให้ไหลไปตามราง เพื่อให้บอลไปชนพิน **\(Pin\)** ที่ตั้งไว้ให้ล้มให้ได้มากที่สุด  
> ซึ่งโบลิ่ง 1 เกมจะแบ่งออกเป็น 10 **เฟรม \(Frame\)** ซึ่งแต่ละเฟรมจะตั้งพินให้ 10 ตัว และเราสามารถโยนบอลได้สูงสุด 2 ครั้งต่อเฟรม  
>   
> ถ้าผู้เล่นสามารถ**ล้มพินได้ทั้งหมดในการโยนครั้งแรก**จะเรียกว่า **สไตรค์ \(Strike\)** และจะถือว่าจบเฟรมนั้นทันที  
> ถ้าผู้เล่นสามารถ**ล้มพินได้หมดในการโยนครั้งที่สอง**จะเรียกว่า **สแปร์ \(Spare\)** และมื่อโยนบอลครบ 2 ครั้งแล้วจะถือว่าจบเฟรมนั้นทันที  
>   
> ถ้าผู้เล่นได้ **สไตรค์** จะได้ 10 คะแนน และ รวมกับจำนวนพินที่ล้มได้ในการโยนบอล 2 ครั้งถัดด้วย  
> ถ้าผู้เล่นได้ **สแปร์** จะได้ 10 คะแนน และ รวมกับจำนวนพินที่ล้มได้ในการโยนบอล 1 ครั้งถัดไปด้วย  
> ถ้าผู้เล่นไม่สามารถทำ สไตรค์ หรือ สแปร์ได้ จะได้คะแนนตามจำนวนพินที่ล้มได้ในเฟรมนั้น  
>   
> ถ้าผู้เล่นทำ **สไตรค์** ได้ในเฟรมที่ 10 จะได้โยนบอลต่ออีก 2 ครั้ง เพื่อจะได้ครบเงื่อนไขการนับคะแนนแบบ สไตรค์  
> ถ้าผู้เล่นทำ **สแปร์** ได้ในเฟรมที่ 10 จะได้โยนบอลต่ออีก 1 ครั้ง เพื่อจะได้ครบเงื่อนไขการนับคะแนนแบบ สแปร์

### 💬 บทสนทนา

> ผมตัดบางบทสนธนาออกให้กระชับ + ปรับคำพูดให้เข้าใจง่ายขึ้นนะ

**ลุงบ๊อบ**: เฮ้ย มาช่วยอั๊วเขียนโปรแกรมคำนวณคะแนนเกมโบลิ่งหน่อยดิ ว่างป่าว?  
**ป๋าโรเบิร์ด**: เยี่ยมไปเลยบ๊อบ แล้วเราจะเริ่มจาก **User story** ไหนดีล่ะ ?  
**ลุงบ๊อบ**: เอาเป็นการคิดคะแนนแค่เกมเดียวละกัน  
**ป๋าโรเบิร์ด**: อืมแล้ว User story นี้มันมี **Input** กับ **Output** อะไรบ้างล่ะ ?  
**ลุงบ๊อบ**: อั๊วคิดว่า **Input** น่าจะเป็นผลจากการโยนบอลนะ โดยที่มันจะบอกว่าการโยนครั้งนั้นทำพินล้มไปได้กี่อัน ส่วน **Output** น่าจะเป็นคะแนนที่ได้ในแต่ละเฟรมละกัน  
**ป๋าโรเบิร์ด**: งั้นตูสมมุติว่าเอ็งเป็นคนใช้โปรแกรมนะบ๊อบ เอ็งอยากให้โปรแกรมรับ Input กับ Output เป็นยังไงดีล่ะ?  
**ลุงบ๊อบ**: อืมสมมุติอั๊วเป็นคนใช้โปรแกรมก็ได้ ส่วนโปรแกรมสำหรับใส่ Input กับ Ouput ให้มันเป็นแบบนี้ได้ไหม

```csharp
ThrowBall(6);
ThrowBall(3);
Assert.AreEqual(9, GetScore());
```

**ป๋าโรเบิร์ด**: ได้ๆ  
**ลุงบ๊อบ**: แล้วเราจะเริ่มไงต่อดีหว่า มาออกแบบระบบกันเลยดีไหม ?  
**ป๋าโรเบิร์ด**: อะนี่ UML diagram ที่มีเกมที่สามารถโยนได้ 10 เฟรม และแต่ละเฟรมก็สามารถโยนได้ 1-3 ครั้ง

![](../.gitbook/assets/image%20%2811%29.png)

**ป๋าโรเบิร์ด**: งั้นเรามาเขียนคลาสก่อนเลยละกัน ตูขอเลือกคลาส **Throw** ละกัน เพราะมันเป็นคลาสทุกตัวต้องเกี่ยวข้องด้วย เราจะได้เริ่มเขียนเทสได้ง่ายขึ้น  
**ลุงบ๊อบ**: แน่นอน งั้นลื้อเขียนเทสเคสของคลาส Thow ไปเลย  
**ป๋าโรเบิร์ด**: พิมพ์ๆๆ

{% code-tabs %}
{% code-tabs-item title="ThrowTest.cs" %}
```csharp
public class ThrowTest
{
    [Test]
    public void Test???
}
```
{% endcode-tabs-item %}
{% endcode-tabs %}

**ป๋าโรเบิร์ด**: อืมมมม เอ็งพอจะมีไอเดียไหมว่าเจ้า object จากคลาส Throw มันควรจะทำงานยังไงเป็นยังไง  
**ลุงบ๊อบ**: มันก็แค่เก็บจำนวนของพินที่ล้มได้ไง  
**ป๋าโรเบิร์ด**: ถ้ามันเป็นแบบนั้น แล้วเราจะเทสอะไรล่ะมีแค่เลขตัวเดียว! งั้นเราไปดู object ที่เรารู้ว่ามันทำงานยังไงก่อนไหม ?  
**ลุงบ๊อบ**: อืมมม ลื้อกำลังบอกว่าคลาส Throw จริงๆมันไม่ต้องมีก็ได้งั้นซินะ ?  
**ป๋าโรเบิร์ด**: ถ้ามันไม่มีการทำงานอะไรเลย แล้วจะเก็บมันไว้เป็นคลาสทำไม? ตูแค่คิดว่าเราไปมองคลาสอื่นดีกว่าที่จะมานั่งคิดคลาสที่มีแค่อ่านเขียนตัวเลขตัวเดียว แต่ถ้าเอ็งคิดอะไรออกลองเอาไปเขียนดูดิ ... \(สไลด์คีย์บอร์ดให้ลุงบ๊อบ\)  
**ลุงบ๊อบ**: เอาตามนั้นก็ได้ งั้นเราข้ามไปดูคลาส **Frame** เลยละกัน แล้วมันมีเทสเคสอะไรบ้างล่ะ \(ดันคีย์บอร์ดกลับมาให้ป๋าโรเบิร์ด\)  
**ป๋าโรเบิร์ด**: ดี งั้นเริ่มเขียนเทสเคสเลยละกัน ... พิมพ์ๆๆ

{% code-tabs %}
{% code-tabs-item title="FrameTest.cs" %}
```csharp
public class FrameTest
{
    [Test]
    public void Test???
}
```
{% endcode-tabs-item %}
{% endcode-tabs %}

**ลุงบ๊อบ**: นี่เป็นครั้งที่ 2 แล้วนะที่เราพิมพ์อะไรแบบนี้ ลื้อพอจะคิดเทสเคสให้กับเจ้าคลาส Frame ออกไหม ?  
**ป๋าโรเบิร์ด**: คลาส Frame น่าจะเก็บคะแนน กับ จำนวนพินที่ล้มได้ของเฟรมนั้นๆเอาไว้นะ และมันต้องจำด้วยว่าเป็น สไตรค์ หรือ สแปร์ หรือเปล่าด้วย  
**ลุงบ๊อบ**: เยี่ยม งั้นเขียนเลย  
**ป๋าโรเบิร์ด**: พิมพ์ๆๆ

{% code-tabs %}
{% code-tabs-item title="FrameTest.cs" %}
```csharp
public class FrameTest
{
    [Test]
    public void TestScoreNoThrows()
    {
        Frame f = new Frame();
        Assert.AreEqual(0, f.Score);
    }
}
```
{% endcode-tabs-item %}

{% code-tabs-item title="Frame.cs" %}
```csharp
public class Frame
{
    public int Score
    {
        get { return 0; }
    }
}
```
{% endcode-tabs-item %}
{% endcode-tabs %}

{% hint style="warning" %}
**การดูโค้ดตัวอย่าง**  
เจ้าโค้ดด้านบนสังเกตุดีๆมันจะมีชื่อไฟล์อยู่ด้านบนนะครับ **FrameTest.cs** กับ **Frame.cs** ให้กดที่ชื่อไฟล์ แล้วมันจะเปิดโค้ดให้ดูนะ \(ตัวอย่างโค้ดถัดๆไปจะเป็นลักษณะนี้นะ\)
{% endhint %}

**ลุงบ๊อบ:** เยี่ยมเทสผ่านละ แต่ Score นี่มันเป็น property โง่ๆเลย งั้นต่อไปลื้อลองเพิ่มเทสเคส เพิ่มคะแนนที่ได้จากการโยนบอลเข้าไปดูดิ๊ เราจะได้ตรวจผลคะแนนที่ได้กันต่อ  
**ลุงบ๊อบ**: พิมพ์ๆๆ

{% code-tabs %}
{% code-tabs-item title="FrameTest.cs" %}
```csharp
[Test]
public void TestAddOneThrow()
{
    Frame f = new Frame();
    f.Add(5);
    Assert.AreEqual(5, f.Score);
}
```
{% endcode-tabs-item %}
{% endcode-tabs %}

**ลุงบ๊อบ:** เฮ้ยมัน Compile ไม่ได้นิ เพราะยังไม่ได้เขียน method Add\(\) ของคลาส Frame เลยนิ  
**ป๋าโรเบิร์ด:** เอ็งก็เขียนดิ  
**ลุงบ๊อบ:** พิมพ์ๆๆ

{% code-tabs %}
{% code-tabs-item title="Frame.cs" %}
```csharp
public class Frame
{
    public int Score
    {
        get { return 0; }
    }
    
    public void Add(Throw t)
    {
    }
}
```
{% endcode-tabs-item %}
{% endcode-tabs %}

**ลุงบ๊อบ:** มันก็ยังทำงานไม่ได้อยู่ดีแหละ เพราะเรายังไม่เขียนคลาส Throw เลย  
**ป๋าโรเบิร์ด:** บ๊อบบอกตูที ในเทสเคสอะมันส่งตัวเลขเข้าไป แต่ method ที่เอ็งเขียนดันรับ object จากคลาส Throw ... มันทำแบบนั้นไม่ได้นะเฟร้ย เพราะถ้าเรายังคิดการทำงานของคลาส Throw ไม่ออก เราก็จะยังไม่มีคลาส Throw  
**ลุงบ๊อบ:** เอ่อว่ะ อั๊วไม่ทันสังเกตุเลย ว่าอั๊วเขียน f.Add\(5\) ลงไป เพราะตอนแรกอั๊วคิดที่จะเขียนเป็น  
f.Add\(new Throw\(5\)\); แต่มันน่าเกลียดมาก เลยเขียนเป็น f.Add\(5\) ลงไปซะก่อน  
**ป๋าโรเบิร์ด:** น่าเกลียดหรือเปล่าตูไม่สนหรอก แต่เอ็งบอกหน่อยเหอะ ว่าการทำงานของคลาส Throw มันเป็นยังไง ?  
**ลุงบ๊อบ:** อั๊วไม่รู้เฟร้ย อั๊วแค่คิดว่ามันน่าจะเก็บแค่ตัวเลขไว้แค่นั้นจริงๆ  แต่ช่าง\(หัว\)มันก่อนใช้ Frame.Add\(int\) ไปก่อนก็ได้  
**ป๋าโรเบิร์ด:** งั้นตูว่าก็ทำแบบนั้นไปแหละถ้ายังไม่มีเหตุผลอื่น แล้วถ้าทนไม่ได้ค่อยกลับมาแก้มันอีกทีละกัน  
**ลุงบ๊อบ:** อืมเห็นด้วย

{% code-tabs %}
{% code-tabs-item title="Frame.cs" %}
```csharp
public void Add(int pins)
{
}
```
{% endcode-tabs-item %}
{% endcode-tabs %}

**ลุงบ๊อบ:** โอเคตอนนี้ Compile ได้ละ และเทสก็ fail ด้วย เอาละมาทำให้มันผ่านกัน

{% code-tabs %}
{% code-tabs-item title="Frame.cs" %}
```csharp
public class Frame
{
    private int score;
    
    public int Score
    {
        get { return score; }
    }
    
    public void Add(int pins)
    {
        score += pins;
    }
}
```
{% endcode-tabs-item %}
{% endcode-tabs %}

**ลุงบ๊อบ:** เอาละผ่านเทสหมดละ แล้วมันจะเกิดอะไรขึ้นอั๊วใส่ 11 เข้าไปใน Frame.Add\(\) ?  
**ป๋าโรเบิร์ด:** มันก็จะเกิด exception ไง แต่ใครมันจะมาใช้ method นั้นกัน? สิ่งที่เรากำลังเขียนอยู่มันไม่ได้เขียนเป็น framework ที่จะให้คนมาใช้เป็นพันๆคนซักหน่อย เอ็งแค่จะเอามาเขียนเล่นๆไม่ใช่เหรอ? และคนใช้ก็มีแค่เอ็งคนเดียวด้วยใช่ไหม งั้นก็อย่างส่ง 11 เข้าไปดิ!  
**ลุงบ๊อบ:** เป็นความคิดที่ดี แล้วพวกเทสส่วนใหญ่ของโปรแกรมก็เป็นเคสใส่ข้อมูลผิดๆเข้ามา เดี๋ยวค่อยไปเช็คเอา ตอนนั้นก็ได้ เอาล่ะตอนนี้ method Add มันยังไม่ได้จัดการเรื่อง **สไตรค์** กับ **สแปร์** เลย เรามาเขียนเคสนี้กันเถอะ  
**ป๋าโรเบิร์ด:** อืมมม ถ้าเราส่ง Add\(10\) ก็ถือว่าเป็นสไตรค์แล้วกัน  
**ลุงบ๊อบ:** ถ้าทำแบบที่ลื้อว่า กับส่ง Add\(7\) แล้วตามด้วย Add\(3\) มันก็จะเหมือนกันอะดิ และจริงๆ Frame นั้นจะมีคะแนนเป็นเท่าไหร่ มันต้องไปดู object ของคลาส Frame ตัวสุดท้ายเพื่อเอาไปคำนวณคะแนนมานิ แต่ถ้ามันไม่มี Frame ตัวสุดท้ายล่ะ จะให้มันส่ง -1 มาเหรอ? อั๊วไม่อยากได้แบบนั้นนะ  
**ป๋าโรเบิร์ด:** ตูก็ไม่ชอบเหมือนกัน แต่เอ็งกำลังบอกว่าคลาส Frame จะต้องรู้จักคลาส Frame ตัวอื่นเหรอ? แล้วใครจะเป็นคนเก็บ object ของคลาส Frame พวกนั้นล่ะ?  
**ลุงบ๊อบ:** object ของคลาส Game ไง  
**ป๋าโรเบิร์ด:** หมายความว่า Game จะรู้จัก Frame และ Frame ก็จะรู้จัก Game เหรอ ตูไม่เอาแบบนั้นนะเฟร้ย  
**ลุงบ๊อบ:** ไม่ใช่ว้อย Frame ไม่ต้องรู้จักกับ Game เราแค่เก็บ Frame ไว้ในรูปแบบ **Linked list** ก็พอ \(Frame แต่ละตัวจะรู้ว่า Frame ก่อนหน้าและถัดไปของมันคือตัวไหน\) ทำให้เวลามันได้คะแนน สไตรค์ หรือ สแปร์ จะได้ไปคิดคะแนนจาก Frame ถัดไปได้ไง  
**ป๋าโรเบิร์ด:** เยี่ยมเลย รู้สึกตัวเองโง่ลงเลย เพราะคิดไม่ถึงว่ามีวิธีนั้นด้วย เอาบ๊อบเขียนโค้ดเลย  
**ลุงบ๊อบ:** จัดไป แต่เราต้องเขียนเทสเคสก่อน  
**ป๋าโรเบิร์ด:** จะเอาเทสเคสของ Game หรือเทสเคสของ Frame ?  
**ลุงบ๊อบ:** รอบนี้ลองเขียนเทสเคสให้ Game ดูบ้าง เพื่อจะได้พิสูจน์ว่าเราต้องการ Linked list ของ Frame จริงๆ  
**ลุงบ๊อบ:** พิมพ์ๆๆ

{% code-tabs %}
{% code-tabs-item title="GameTest.cs" %}
```csharp
public class GameTest
{
    [Test]
    public void TestOneThrow()
    {
        Game game = new Game();
        game.Add(5);
        Assert.AreEqual(5, game.Score);
    }
}
```
{% endcode-tabs-item %}

{% code-tabs-item title="Game.cs" %}
```csharp
public class Game
{
    private int score;
    
    public int Score
    {
        get { return score; }
    }
    
    public void Add(int pins)
    {
        score += pins;
    }
}
```
{% endcode-tabs-item %}
{% endcode-tabs %}

**ลุงบ๊อบ:** อะเค เทสผ่านละ  
**ป๋าโรเบิร์ด:** เยี่ยมเลย ต่อไปเราก็แค่พิสูจน์ว่าเราต้องการ Linked list ของ Frame object จริงหรือเปล่า ?  
**ลุงบ๊อบ:** นั่นแหละที่ต้องการ อั๊วเชื่อว่าถ้าเราเริ่มใส่เทสเคส ไตรค์ กับ สแปร์ เข้าไปแล้ว เราคงจะได้เห็น Linked list แล้วล่ะ แต่ที่อั๊วไม่สร้าง Linked list ไว้ก่อนก็เพราะ**อยากให้มันโดนบังคับจากเทสเคสจริงๆก่อนถึงค่อยทำ  
ป๋าโรเบิร์ด:** เป็นเหตุผลที่ดี งั้นเราไปเขียนเทสเคสให้กับ Game กันต่อเลย เอาเป็น โยน 2 ครั้งแต่ก็ไม่ได้สแปร์เป็นไง  
**ลุงบ๊อบ:** จัดไป ... พิมพ์ๆๆ

{% code-tabs %}
{% code-tabs-item title="GameTest.cs" %}
```csharp
[Test]
public void TestTwoThrowsNoMark()
{
    Game game = new Game();
    game.Add(5);
    game.Add(4);
    Assert.AreEqual(9, game.Score);
}
```
{% endcode-tabs-item %}
{% endcode-tabs %}

**ลุงบ๊อบ:** เยี่ยมผ่านเหมือนเดิม งั้นลองโยน 4 ครั้งโดยไม่ได้สแปร์เลย แล้วลองตรวจเรื่องอื่นๆด้วยละกัน

{% code-tabs %}
{% code-tabs-item title="GameTest.cs" %}
```csharp
[Test]
public void TestFourThrowsNoMark()
{
    Game game = new Game();
    game.Add(5);
    game.Add(4);
    game.Add(7);
    game.Add(2);
    Assert.AreEqual(18, game.Score);
    Assert.AreEqual(9, game.ScoreForFrame(1));
    Assert.AreEqual(18, game.ScoreForFrame(2));
}
```
{% endcode-tabs-item %}
{% endcode-tabs %}

**ป๋าโรเบิร์ด:** โอ้ววว เกือบลืมไปเลยว่าต้องโชว์คะแนนจากเฟรมอื่นๆด้วย  
**ลุงบ๊อบ:** ฮ่าๆ งั้นมาเขียนเทสให้ fail กันเถอะ โดยการเพิ่ม ScoreForFrame\(\) ให้กับ Game

{% code-tabs %}
{% code-tabs-item title="Game.cs" %}
```csharp
public int ScoreForFrame(int theFrame)
{
    return 0;
}
```
{% endcode-tabs-item %}
{% endcode-tabs %}

**ลุงบ๊อบ:** เอาละ fail แล้ว แล้วจะทำยังไงให้มันผ่านได้ล่ะ ?  
**ป๋าโรเบิร์ด:** ตอนนี้เราจะสร้าง Linked list เพื่อจัดการกับ Frame ก็ได้นะ  
**ลุงบ๊อบ:** ยังก่อน เราใส่โค้ดแบบเรียบง่ายให้มันใช้งานได้ไปก่อนละกัน โดยใช้ int array แทน Linked list ก็ได้ แล้วใส่ลงไปในคลาส Game แล้วทุกครั้งที่ใช้ Add\(\) เราก็แค่เก็บเลขนั้นลงใน array ส่วนเวลาใช้ ScoreForFram\(\) เราก็ไปไล่คำนวณจาก array ได้เหมือนกัน ... พิมพ์ๆๆ

{% code-tabs %}
{% code-tabs-item title="Game.cs" %}
```csharp
public class Game
{
    private int score;
    private int[] throws = new int[21];
    private int currentThrow;
    
    public int Score
    {
        get { return score; }
    }
    
    public void Add(int pins)
    {
        throws[currentThrow++] = pins;
        score += pins;
    }
    
    public int ScoreForFrame(int theFrame)
    {
        int ball = 0;
        int score = 0;
        for (int currentFrame = 0;
            currentFrame < theFrame;
            currentFrame++)
        {
            int firstThrow = throws[ball++];
            int secondThrow = throws[ball++];
            score += firstThrow + secondThrow;
        }

        return score;
    }
}
```
{% endcode-tabs-item %}
{% endcode-tabs %}

**ลุงบ๊อบ:** เยี่ยม เทสผ่านละ  
**ป๋าโรเบิร์ด:** เฮ้ยบ๊อบ เลข 21 ในบรรทัดที่ 4 คืออะไรเหรอ ?  
**ลุงบ๊อบ:** จำนวนครั้งสูงสุดที่บอลสามารถโยนได้ต่อเกมไง  
**ลุงบ๊อบ:** งั้นถัดไปมาเขียนเคสได้ สแปร์ ละกัน ... พิมพ์ๆๆ

{% code-tabs %}
{% code-tabs-item title="GameTest.cs" %}
```csharp
[Test]
public void TestSimpleSpare()
{
    Game game = new Game();
}
```
{% endcode-tabs-item %}
{% endcode-tabs %}

**ลุงบ๊อบ:** อืมมม เหมือนทุกครั้งที่จะเริ่มเขียนเทส เราจะต้องสร้าง game object เสมอเลยนะ งั้นขอ **Refactor** หน่อยละกัน ... พิมพ์ๆๆ

{% code-tabs %}
{% code-tabs-item title="GameTest.cs" %}
```csharp
private Game game;

public GameTest()
{
   game = new Game();
}
```
{% endcode-tabs-item %}
{% endcode-tabs %}

**ลุงบ๊อบ:** อะเคใช้ได้ละ งั้นเรี่ยมเขียนเทสเคส สแปร์ ต่อเลยละกัน ... พิมพ์ๆๆ

{% code-tabs %}
{% code-tabs-item title="GameTest.cs" %}
```csharp
[Test]
public void TestSimpleSpare()
{
    Game game = new Game();
    game.Add(3);
    game.Add(7);
    game.Add(3);
    Assert.AreEqual(13, game.ScoreForFrame(1));
}
```
{% endcode-tabs-item %}
{% endcode-tabs %}

**ลุงบ๊อบ:** โอเค ตอนนี้มัน fail ละ ต่อไปมาเขียนให้มันผ่านกันเถอะ  
**ป๋าโรเบิร์ด:** มาตูเขียนเอง ... พิมพ์ๆๆ 

> เพิ่มบรรทัดที่ 12~18

{% code-tabs %}
{% code-tabs-item title="Game.cs" %}
```csharp
public int ScoreForFrame(int theFrame)
{
    int ball = 0;
    int score = 0;
    for (int currentFrame = 0;
        currentFrame < theFrame;
        currentFrame++)
    {
        int firstThrow = throws[ball++];
        int secondThrow = throws[ball++];

        int frameScore = firstThrow + secondThrow;

        // spare needs next frames first throw
        if (frameScore == 10)
            score += frameScore + throws[ball++];
        else
            score += frameScore;
    }

    return score;
}
```
{% endcode-tabs-item %}
{% endcode-tabs %}

**ป๋าโรเบิร์ด:** อะฮ๊าา ใช้ได้ๆ ผ่านละ  
**ลุงบ๊อบ:** \(แย่งคียบอร์ดมา\) อั๊วคิดว่าการเพิ่มค่า ball ตอนที่ frameScore == 10 ไม่ไม่ควรอยู่ตรงนี้นะ เดี๋ยวจะลองใส่เทสเคสนี้เพื่อพิสูจน์ให้ดู ... พิมพ์ๆๆ

{% code-tabs %}
{% code-tabs-item title="GameTest.cs" %}
```csharp
[Test]
public void TestSimpleFrameAfterSpare()
{
    game.Add(3);
    game.Add(7);
    game.Add(3);
    game.Add(2);
    Assert.AreEqual(13, game.ScoreForFrame(1));
    Assert.AreEqual(18, game.Score);
}
```
{% endcode-tabs-item %}
{% endcode-tabs %}

**ลุงบ๊อบ:** เห็นไหมตามที่บอกเลย fail เลย เอาละเดี๋ยวอั๊วไปเอาไอ้ที่เพิ่มค่า ball ออกดู ... พิมพ์ๆ

{% code-tabs %}
{% code-tabs-item title="Game.cs" %}
```csharp
if (frameScore == 10)
    score += frameScore + throws[ball];
```
{% endcode-tabs-item %}
{% endcode-tabs %}

**ลุงบ๊อบ:** อ่าว ยัง fail อยู่เหมือนเดิมนิหว่า หรือว่าเราเขียนเจ้า Score property ผิดหว่า? งั้นลองเปลี่ยนมาใช้ ScoreForFram\(2\) แทนละกัน ... พิมพ์ๆๆ

> แก้แค่บรรทัด 9

{% code-tabs %}
{% code-tabs-item title="GameTest.cs" %}
```csharp
[Test]
public void TestSimpleFrameAfterSpare()
{
    game.Add(3);
    game.Add(7);
    game.Add(3);
    game.Add(2);
    Assert.AreEqual(13, game.ScoreForFrame(1));
    Assert.AreEqual(18, game.ScoreForFrame(2));
}
```
{% endcode-tabs-item %}
{% endcode-tabs %}

**ลุงบ๊อบ:** อืมมมมมมม ผ่านวุ้ย แสดงว่า Score property มันผิดชัวร์ๆ ไหนลองดูดิ๊

{% code-tabs %}
{% code-tabs-item title="Game.cs" %}
```csharp
public int Score
{
    get { return score; }
}

public void Add(int pins)
{
    throws[currentThrow++] = pins;
    score += pins;
}
```
{% endcode-tabs-item %}
{% endcode-tabs %}

**ลุงบ๊อบ:** นั่นไงผิดจริงๆด้วย เพราะ Score property มันแค่ส่งผลรวมของพินที่ล้มได้ออกมานิหว่า เดี๋ยวเราเปลี่ยนให้มันส่งผลลัพท์จาก ScoreForFrame\(\) ของเฟรมปัจจุบันกลับมาละกัน  
**ป๋าโรเบิร์ด:** ตัว Game มันไม่รู้ว่าตอนนี้มันอยู่เฟรมไหนนะ งั้นเอ็งลองเพิ่มให้มันรู้ว่าตอนนี้มันอยู่เฟรมไหนไปด้วยเลยดิ  
**ลุงบ๊อบ:** ได้เลย ... พิมพ์ๆๆ

> เพิ่มบรรทัด 6

{% code-tabs %}
{% code-tabs-item title="GameTest.cs" %}
```csharp
[Test]
public void TestOneThrow()
{
    game.Add(5);
    Assert.AreEqual(5, game.Score);
    Assert.AreEqual(1, game.CurrentFrame);
}
```
{% endcode-tabs-item %}

{% code-tabs-item title="Game.cs" %}
```csharp
public int CurrentFrame
{
    get { return 1; }
}
```
{% endcode-tabs-item %}
{% endcode-tabs %}

**ลุงบ๊อบ:** อะเคผ่านละ แต่ติงต๊องมาก ลองไปใส่ในเคสอื่นบ้างดิ๊ ... พิมพ์ๆ

> เพิ่มบรรทัด 7

{% code-tabs %}
{% code-tabs-item title="GameTest.cs" %}
```csharp
[Test]
public void TestTwoThrowsNoMark()
{
    game.Add(5);
    game.Add(4);
    Assert.AreEqual(9, game.Score);
    Assert.AreEqual(1, game.CurrentFrame);
}
```
{% endcode-tabs-item %}
{% endcode-tabs %}

**ลุงบ๊อบ:** ผ่านเหมือนกัน ไหนลองตัวถัดไปดิ๊

> เพิ่มบรรทัด 12

{% code-tabs %}
{% code-tabs-item title="GameTest.cs" %}
```csharp
[Test]
public void TestFourThrowsNoMark()
{
    Game game = new Game();
    game.Add(5);
    game.Add(4);
    game.Add(7);
    game.Add(2);
    Assert.AreEqual(18, game.Score);
    Assert.AreEqual(9, game.ScoreForFrame(1));
    Assert.AreEqual(18, game.ScoreForFrame(2));
    Assert.AreEqual(2, game.CurrentFrame);
}
```
{% endcode-tabs-item %}
{% endcode-tabs %}

**ลุงบ๊อบ:** อะฮ๊า fail ละ ไปทำให้มันผ่านกัน  
**ป๋าโรเบิร์ด:** ตูคิดว่าวิธีคิดมันง่ายๆนะ แค่เอาจำนวนครั้งที่โยนไปหาร 2 เพราะสูงสุดมันโยนได้ 2 ครั้งต่อเฟรม ยกเว้นได้สไตรค์ แต่ช่างมันก่อนก็ได้เรายังไม่ได้มีเคส สไตรค์เลย

{% code-tabs %}
{% code-tabs-item title="Game.cs" %}
```csharp
public int CurrentFrame
{
    get { return 1 + (currentThrow - 1) / 2; }
}
```
{% endcode-tabs-item %}
{% endcode-tabs %}

**ลุงบ๊อบ:** อั๊วไม่ถูกใจโค้ดแบบนี้เลย  
**ป๋าโรเบิร์ด:** งั้นไม่คำนวณตลอดเวลาก็ได้ เอาเป็นไปคำนวณตอนที่โยนบอลแต่ละครั้งละกัน  
**ลุงบ๊อบ:** โอเคจัดไป ... พิมพ์ๆ

{% code-tabs %}
{% code-tabs-item title="Game.cs" %}
```csharp
private int currentFrame;
private bool isFirstThrow = true;

public int CurrentFrame
{
    get { return currentThrow; }
}

public void Add(int pins)
{
    throws[currentThrow++] = pins;
    score += pins;

    if(isFirstThrow)
    {
        isFirstThrow = false;
        currentFrame++;
    }
    else
    {
        isFirstThrow = true;
    }
}
```
{% endcode-tabs-item %}
{% endcode-tabs %}

**ป๋าโรเบิร์ด:** โอเค เทสยังผ่านหมดอยู่ แต่ต้องจำไว้ด้วยว่าเจ้า CurrentFrame คือเฟรมที่โยนบอลครั้งสุดท้ายนะ ไม่ใช่เฟรมที่จะโยนบอลครั้งถัดไป  
**ลุงบ๊อบ:** โอ้ยอั๊วจำไม่ได้หรอก แต่อั๊วขอแก้ให้โค้ดมันอ่านง่ายขึ้นหน่อยละกันก่อนที่จะทำต่อ อั๊วจะย้ายตัวคำนวณเฟรมออกมาจาก Add\(\) นะ  
**ป๋าโรเบิร์ด:** ฟังดูไม่เลว ลงมือเลย

{% code-tabs %}
{% code-tabs-item title="Game.cs" %}
```csharp
public void Add(int pins)
{
    throws[currentThrow++] = pins;
    score += pins;

    AdjustCurrentFrame();
}

private void AdjustCurrentFrame()
{
    if (isFirstThrow)
    {
        isFirstThrow = false;
        currentFrame++;
    }
    else
    {
        isFirstThrow = true;
    }
}
```
{% endcode-tabs-item %}
{% endcode-tabs %}

**ป๋าโรเบิร์ด:** เยี่ยมเลย แต่ตูไม่ชอบที่ตัวแปร currentFrame มันเริ่มที่ 0 อยู่เลย มาเปลี่ยนให้มันเข้าใจง่ายๆดีกว่า  
**ลุงบ๊อบ:** อืม เห็นด้วย

> Game.cs เพิ่มบรรทัด 1 กับ 13  
> GameTest.cs เพิ่มบรรทัดที่ 9 กับ 21 และ แก้ไขบรรทัด 30 กับ 44

{% code-tabs %}
{% code-tabs-item title="Game.cs" %}
```csharp
private int currentFrame = 1;

private void AdjustCurrentFrame()
{
    if (isFirstThrow)
    {
        isFirstThrow = false;
        currentFrame++;
    }
    else
    {
        isFirstThrow = true;
        currentFrame++;
    }
}
```
{% endcode-tabs-item %}

{% code-tabs-item title="GameTest.cs" %}
```csharp
[Test]
public void TestSimpleSpare()
{
    Game game = new Game();
    game.Add(3);
    game.Add(7);
    game.Add(3);
    Assert.AreEqual(13, game.ScoreForFrame(1));
    Assert.AreEqual(2, game.CurrentFrame);
}

[Test]
public void TestSimpleFrameAfterSpare()
{
    game.Add(3);
    game.Add(7);
    game.Add(3);
    game.Add(2);
    Assert.AreEqual(13, game.ScoreForFrame(1));
    Assert.AreEqual(18, game.ScoreForFrame(2));
    Assert.AreEqual(3, game.CurrentFrame);
}

[Test]
public void TestTwoThrowsNoMark()
{
    game.Add(5);
    game.Add(4);
    Assert.AreEqual(9, game.Score);
    Assert.AreEqual(2, game.CurrentFrame);
}

[Test]
public void TestFourThrowsNoMark()
{
    Game game = new Game();
    game.Add(5);
    game.Add(4);
    game.Add(7);
    game.Add(2);
    Assert.AreEqual(18, game.Score);
    Assert.AreEqual(9, game.ScoreForFrame(1));
    Assert.AreEqual(18, game.ScoreForFrame(2));
    Assert.AreEqual(3, game.CurrentFrame);
}
```
{% endcode-tabs-item %}
{% endcode-tabs %}

{% hint style="danger" %}
บทนี้ยังไม่เสร็จกำลังเขียนอยู่
{% endhint %}

