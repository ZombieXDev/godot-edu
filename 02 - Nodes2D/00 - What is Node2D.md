<div dir="rtl">

# ما هو Node2D ؟

---

## التعريف

`Node2D` هو نوع من العقد (Nodes) في Godot يُستخدم كقاعدة أساسية لكل العناصر التي تعمل في بيئة ثنائية الأبعاد (2D).

يوفّر `Node2D` خصائص تساعد في التحكم بموقع العنصر، اتجاهه، حجمه، وترتيبه عند العرض، وهي:

- `position`: لتحديد مكان العنصر.
- `rotation`: لتدوير العنصر.
- `scale`: لتكبير أو تصغير العنصر.
- `z_index`: لترتيب ظهور العناصر (أمام أو خلف غيرها).

---

## ما وظيفة Node2D؟

`Node2D` بحد ذاته لا يعرض شيئًا على الشاشة، بل يُستخدم كقاعدة تنطلق منها باقي العناصر.

أي عنصر ثنائي الأبعاد مثل الصور، الشخصيات، الأرضيات، الكاميرات، والمناطق الفيزيائية (مثل التصادم) — جميعها تعتمد على `Node2D` كأساس.

بمعنى آخر:
> كل شيء ثنائي الأبعاد في Godot يبدأ من `Node2D` أو من عنصر يرث منه.

---

## متى أستخدمه؟

تستخدم `Node2D` عندما تحتاج إلى:
- تحديد موقع عنصر على الشاشة.
- تدوير العنصر أو قلبه.
- تجميع عناصر متعددة تحت عنصر رئيسي واحد (مثل اللاعب الذي يحتوي على صورة، وتصادم، وصوت).
- بناء عنصر جديد خاص بك يعتمد على بيئة ثنائية الأبعاد.

---

## خطوات إضافة Node2D في محرّك Godot:

1. افتح مشروعك في Godot.
2. في الزاوية العليا من نافذة المشهد (Scene)، اضغط على زر **"+"** لإضافة عنصر جديد.
3. في خانة البحث التي تظهر، اكتب: `Node2D`.
4. اختر العنصر، ثم اضغط على زر **Create**.

سيتم إضافة `Node2D` كعنصر رئيسي فارغ داخل المشهد الحالي.

---

## مثال عملي (شجرة عناصر)

في هذا المثال، نصنع مشهد خاص باللاعب، يبدأ بـ `Node2D` كعنصر رئيسي، وبداخله نضيف عناصر أخرى:

```
Player (Node2D)
├── Sprite2D ← يعرض صورة اللاعب
├── CollisionShape2D ← يستخدم لتحديد منطقة التصادم
├── AnimationPlayer ← لتشغيل الحركات (Animations)
```


هذا التنظيم مفيد لفصل مكونات اللاعب داخل مشهد واحد، مما يسهل التحكم بها لاحقًا.

---

## الخصائص الأساسية في Node2D

| الخاصية       | النوع      | الوصف                                                        |
|---------------|------------|---------------------------------------------------------------|
| `position`    | Vector2    | يحدد موقع العنصر على المحور X و Y داخل المشهد.              |
| `rotation`    | float      | يحدد زاوية التدوير (بالراديان).                             |
| `rotation_degrees` | float | تدوير العنصر ولكن بالدرجات بدل الراديان (أسهل للفهم).       |
| `scale`       | Vector2    | يحدد حجم العنصر (1 = الحجم الطبيعي، 2 = ضعف الحجم، وهكذا).   |
| `z_index`     | int        | يحدد ترتيب عرض العنصر أمام أو خلف عناصر أخرى.                |
| `global_position` | Vector2 | موقع العنصر بعد تطبيق تأثيرات الأب (Position النهائي).     |

---

## المستوى الإحداثي في 2D في Godot

- المحور X يزيد لما تتحرك يمين، وينقص لما تتحرك يسار.
- المحور Y يزيد لما تتحرك تحت، وينقص لما تتحرك فوق.
- نقطة الأصل (0,0) عادة تكون في الزاوية العليا اليسرى للشاشة.
- مثال: النقطة (100, 50) تعني 100 وحدة يمين و50 وحدة تحت نقطة الأصل.
- هذا النظام مختلف عن الرياضيات التقليدية حيث Y يزيد للأعلى.


---

## ملاحظات مهمة

- `Node2D` لا يعرض أي رسومات أو أصوات.
- لا يمكن رؤيته داخل اللعبة إلا إذا أضفت عناصر مرئية بداخله، مثل `Sprite2D`.
- يتم استخدامه كثيرًا كـ "عنصر تجميع" (Parent) لعناصر أخرى.
- جميع العناصر 2D الأخرى في Godot (مثل `Area2D`, `Sprite2D`, `TileMap`) ترث من `Node2D`.


---

## 🧠 معلومة إضافية: العلاقة مع المشهد

في Godot، المشهد (Scene) هو عبارة عن مجموعة من العناصر (Nodes) مرتبة بشكل شجري.

`Node2D` غالبًا يكون هو **العنصر الرئيسي** لمشهد ثنائي الأبعاد، لأنه يوفّر الخصائص التي نحتاجها لبناء أي كائن مرئي أو متحرك في لعبة 2D.

---

## ✅ خلاصة

- `Node2D` هو عنصر أساسي لكل ما يتعلق بعالم 2D في Godot.
- لا يعرض شيئًا بحد ذاته، لكنه يعطيك التحكم في الموقع، التدوير، الحجم، والترتيب.
- يجب أن يحتوي على عناصر أخرى ليؤدي وظائف معينة.

</div>
