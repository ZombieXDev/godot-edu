<div dir=rtl>

# ما هو LightOccluder2D؟

`LightOccluder2D` هو عقدة في Godot تُستخدم مع نظام الإضاءة ثنائي الأبعاد (2D) لتحديد المناطق التي تقوم **بحجب الضوء**، أي توليد الظلال عندما يصطدم الضوء بأجسام معينة.

---

## الغرض من LightOccluder2D

- تعريف شكل (شكل ظل) يحجب الضوء الصادر من مصادر الإضاءة مثل `DirectionalLight2D` و`PointLight2D`.
- يسمح لمحاكاة الظلال الواقعية في ألعاب 2D.
- يجعل المشهد أكثر ديناميكية وحيوية باستخدام تأثيرات الإضاءة والظل.

---

## كيف يعمل LightOccluder2D؟

- يُرفق عادةً بجسم مرئي (مثل Sprite أو CollisionShape2D).
- يحتوي على شكل (`OccluderShape2D`) يحدد حدود الجسم التي تحجب الضوء.
- عندما يصطدم الضوء بهذا الشكل، يُنتج ظل في الاتجاه المعاكس لمصدر الضوء.

---

## الخصائص الأساسية لـ LightOccluder2D

| الخاصية              | الوصف                                   |
|----------------------|----------------------------------------|
| **occluder**         | الشكل المستخدم لتحديد منطقة الحجب (OccluderShape2D) |
| **enabled**          | تفعيل أو تعطيل تأثير حجب الضوء        |
| **light_mask**       | قناع الضوء الذي يؤثر عليه هذا الحجب (للتحكم في أنواع معينة من الأضواء) |

---

## إعداد OccluderShape2D

- `OccluderShape2D` يحدد الشكل الهندسي (مثل مستطيل، مضلع، دائرة...) الذي يحجب الضوء.
- يمكن رسمه يدويًا لتحديد المنطقة التي تحجب الضوء بدقة.

---

## كيفية الاستخدام

### 1. إضافة LightOccluder2D

- أضف عقدة `LightOccluder2D` كطفل لكائن في المشهد (مثلاً Sprite أو RigidBody2D).

### 2. إضافة OccluderShape2D

- داخل LightOccluder2D، أضف `OccluderShape2D`.
- اضبط الشكل ليغطي الجزء من الجسم الذي تريد أن يحجب الضوء.

### 3. تفعيل الظلال في مصدر الضوء

- تأكد من تفعيل `shadow_enabled` في مصدر الضوء (`DirectionalLight2D` أو `PointLight2D`).

---

## مثال عملي بسيط

<div dir=ltr>


```gdscript
extends Node2D

func _ready():
    var sprite = Sprite2D.new()
    sprite.texture = preload("res://box.png")
    add_child(sprite)

    var occluder = LightOccluder2D.new()
    sprite.add_child(occluder)

    var occluder_shape = OccluderShape2D.new()
    occluder.occluder = occluder_shape

    # رسم شكل مضلع لحجب الضوء
    occluder_shape.shape = ConvexPolygonShape2D.new()
    occluder_shape.shape.set_points([
        Vector2(-32, -32),
        Vector2(32, -32),
        Vector2(32, 32),
        Vector2(-32, 32),
    ])
```