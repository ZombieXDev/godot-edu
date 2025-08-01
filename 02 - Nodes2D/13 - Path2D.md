
<div dir="rtl">



# ما هي `Path2D`؟

`Path2D` هي عقدة تُستخدم لإنشاء مسار (خط منحني) في عالم ثنائي الأبعاد.
هذا المسار عبارة عن مجموعة نقاط متصلة يمكن أن تشكل أي شكل مثل خط مستقيم، منحنيات، أو مسارات معقدة.

---

## لماذا نستخدم `Path2D`؟

* لتحديد مسار حركة لعناصر اللعبة مثل الشخصيات، الكاميرا، أو الأعداء.
* لرسم خطوط أو مسارات مخصصة.
* لإنشاء تحكم ديناميكي لحركة الأجسام بناءً على مسار محدد.

---

## كيف تعمل؟

* تضيف `Path2D` إلى المشهد.
* تستخدم أداة تحرير المسار (Curve2D) في المحرر لرسم النقاط وتعديل المنحنيات.
* يمكن لعناصر أخرى مثل `PathFollow2D` أن تتبع هذا المسار وتتحرك عليه.

---

## الخصائص المهمة في `Path2D`

| الخاصية  | الوصف                                                |
| -------- | ---------------------------------------------------- |
| `curve`  | يحتوي على نقاط وأشكال المنحنى (Curve2D).             |
| `offset` | قيمة لتحريك بداية المسار على طول الخط.               |
| `loop`   | يحدد ما إذا كان المسار دائريًا (يعود للنقطة الأولى). |

---

## خطوات استخدام `Path2D`

1. أضف عقدة `Path2D` إلى المشهد.
2. في خصائصها، اضغط على `curve` لتحرير المسار.
3. أضف نقاطًا جديدة واضبط المنحنيات لتشكيل المسار المطلوب.
4. استخدم عقدة `PathFollow2D` لتحريك كائن على هذا المسار.

---

## ملاحظات

* `Path2D` بحد ذاتها لا تتحرك أو تظهر أي شيء، هي فقط تحدد المسار.
* الحركة أو التتبع يتم بواسطة عقد أخرى مثل `PathFollow2D`.
* يمكنك استخدام المسارات لجعل الأشياء تتحرك بسلاسة على أشكال معقدة.

---



</div>
