
<div dir=rtl>

# ما هو ParallaxLayer2D؟

`ParallaxLayer2D` هو عقدة تُستخدم ضمن عقدة `ParallaxBackground2D` لإنشاء طبقة من الخلفية تتحرك بسرعة مختلفة عن حركة الكاميرا أو اللاعب، لتحقيق تأثير **التمرير المتوازي (Parallax scrolling)** في الألعاب ثنائية الأبعاد.

كل طبقة تتحكم في معدل تحرك محتواها بالنسبة لتحرك الكاميرا، ما يعطي إحساسًا بالعمق والبعد بين الطبقات.

---

## الخصائص الأساسية لـ ParallaxLayer2D

| الخاصية           | الوصف                                                        |
|-------------------|---------------------------------------------------------------|
| **motion_scale**  | النسبة التي تتحرك بها الطبقة بالنسبة لحركة الكاميرا (Vector2). قيمة (1,1) تعني نفس سرعة الكاميرا. |
| **motion_mirroring** | حجم التكرار الأفقي والعمودي للطبقة (Vector2). تُستخدم لجعل الخلفية تتكرر تلقائيًا. |
| **offset**        | إزاحة الطبقة (Vector2) تستخدم لتحريك محتوى الطبقة عن موضعه الأصلي. |

---

## كيف يعمل ParallaxLayer2D؟

- تتحرك طبقة المحتوى بسرعة محددة بحسب `motion_scale`.
- عندما تتحرك الكاميرا أو `ParallaxBackground2D`، تتحرك الطبقة بنسبة معينة من الحركة.
- القيم الأقل من (1,1) تعني أن الطبقة تتحرك أبطأ من الكاميرا، مما يجعلها تبدو أبعد.
- القيم الأكبر تعني حركة أسرع، تظهر الطبقة أقرب.

---

## استخدام ParallaxLayer2D

1. **إنشاء ParallaxBackground2D** في المشهد.

2. **إضافة ParallaxLayer2D كطفل لـ ParallaxBackground2D**.

3. **إضافة محتوى داخل ParallaxLayer2D** (مثل Sprites أو TileMaps).

4. ضبط خاصية `motion_scale` لكل طبقة للتحكم بسرعة حركتها.

---

## مثال عملي

<div dir=ltr>


```gdscript
extends Node2D

func _ready():
    var parallax_bg = ParallaxBackground2D.new()
    add_child(parallax_bg)

    # إنشاء طبقة تتحرك بنصف سرعة الكاميرا
    var layer1 = ParallaxLayer2D.new()
    layer1.motion_scale = Vector2(0.5, 0.5)
    parallax_bg.add_child(layer1)

    var sprite1 = Sprite2D.new()
    sprite1.texture = preload("res://background_far.png")
    layer1.add_child(sprite1)

    # إنشاء طبقة تتحرك بسرعة الكاميرا كاملة
    var layer2 = ParallaxLayer2D.new()
    layer2.motion_scale = Vector2(1, 1)
    parallax_bg.add_child(layer2)

    var sprite2 = Sprite2D.new()
    sprite2.texture = preload("res://background_near.png")
    layer2.add_child(sprite2)
```