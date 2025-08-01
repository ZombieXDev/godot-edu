
<div dir="rtl">

# ما هي TileMap؟

`TileMap` هي عقدة تستخدم لرسم خرائط ثنائية الأبعاد عن طريق وضع مربعات صغيرة (Tiles) من مجموعة جاهزة (TileSet).
هذا يساعدك تبني مستويات كبيرة بسرعة وبسهولة.

---

## كيف تستخدمها؟

1. تضيف عقدة `TileMap` للمشهد.
2. من خصائص العقدة، تحدد مجموعة البلاط (TileSet) التي تريد استخدامها.
3. تبدأ ترسم باستخدام محرر الـ TileMap داخل المحرك، تضغط لتضع البلاط في الخلايا (Cells).

---

## مصطلحات مهمة:

| المصطلح                | الشرح                                                     |
| ---------------------- | --------------------------------------------------------- |
| **TileSet**            | مجموعة من الصور/الأنماط (Tiles) التي تستعملها في TileMap. |
| **Cell**               | الخلية أو المربع الواحد الذي تضع فيه Tile.                |
| **Atlas**              | صورة تحتوي على عدة مربعات في صورة واحدة.                  |
| **Autotile / Terrain** | ميزة تتيح رسم البلاط تلقائيًا بناءً على الجوار.           |

---

## أهم الخصائص في واجهة `TileMap`:

| الخاصية              | الوصف                                                    |
| -------------------- | -------------------------------------------------------- |
| **Tile Set**         | مجموعة البلاط التي ستستخدمها في الرسم.                   |
| **Cell Size**        | حجم كل مربع (عادة 16×16 أو 32×32 بكسل).                  |
| **Cell/Tile Origin** | نقطة المرجع للمربعات (عادة الزاوية العليا اليسرى).       |
| **Collision Layer**  | تحديد طبقة التصادم للمربعات التي تحتوي تصادم.            |
| **Y Sort**           | تفعيل ترتيب العناصر عموديًا لتظهر بشكل صحيح عند التداخل. |
| **Quadrant Size**    | تحسين الأداء للخرائط الكبيرة بتقسيمها إلى أجزاء.         |

---

## استخدام المحرر (Editor)

* بعد ربط `TileSet`، تظهر لك الشبكة.
* يمكنك اختيار البلاط من الـ TileSet ثم النقر أو السحب لرسم الخريطة.
* يمكن مسح البلاط باستخدام أداة المسح.

---

</div>
