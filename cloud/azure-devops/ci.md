# ลองทำ Continuous Integration \(CI\)

{% hint style="success" %}
**แนะนำให้อ่าน**  
บทความนี้เป็นส่วนหนึ่งของคอร์ส [**👶 Azure DevOps**](https://saladpuk.gitbook.io/learn/cloud/azure-devops) ที่จะมาสอนการใช้งานทุกสิ่งที่ DevOps ควรจะต้องมี เพื่อให้เราสามารถทำ Feedback loop ได้ไวขึ้น ดังนั้นถ้าเพื่อนๆสนใจอยากดูว่ามันทำอะไรได้ก็กดไปอ่านที่บทความหลักได้เลยครัช
{% endhint %}

{% hint style="warning" %}
**คำเตือน**  
ถ้าเพื่อนๆต้องการทำตามบทความนี้ จะต้องมีโปรเจคใน **Azure DevOps** ที่มีการนำ source code ตัว asp.net core mvc ขึ้นมาไว้บน repository เสียก่อน แต่ถ้าใครยังไม่มีก็สามารถไปทำตามได้จากบทตัวนี้ก่อน [**เล่นกับ Repository**](https://saladpuk.gitbook.io/learn/cloud/azure-devops/repository) แล้วค่อยกลับมาทำตามบทความนี้ก็ได้ครัช
{% endhint %}

หลังจากที่เราได้นำ source code ของเว็บ asp.net core mvc ขึ้นมาไว้บน Azure DevOps เรียบร้อยแล้ว ถัดมาเราก็จะทำการสร้าง **Build pipeline** เพื่อทำให้โปรเจคของเรามันทำการตรวจสอบความถูกต้องของโค้ดที่เรานำขึ้นมาต่อ โดยเป้าหมายของการทำ Build pipeline คือการทำให้ของทุกอย่างมันกลายเป็น **Automation** ไปทั้งหมดเพื่อลดการเสียเวลาของคนนั่นเอง ดังนั้นเราไปดูกันต่อเบย

{% hint style="danger" %}
บทความนี้กำลังเขียนอยู่ + ผมมีงานแทรกอยู่ช่วงนี้ เลยทำให้บทความนี้น่าจะเสร็จราวๆเย็นๆของวันที่ **3/11**/2019 นี้ครัช ฝากกดติดตาม [**Facebook Blog: Mr.Saladpuk**](https://www.facebook.com/mr.saladpuk) และถ้ากดแชร์ให้ด้วยจะเป็นพระคุณมากขอรับ 😍
{% endhint %}



