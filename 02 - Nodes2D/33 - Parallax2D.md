<div dir=rtl>

# ما هو Parallax2D؟

Parallax2D هو تأثير بصري يُستخدم في الألعاب ثنائية الأبعاد لإعطاء إحساس بالعمق عبر تحريك الخلفيات أو العناصر بمعدلات مختلفة نسبة لحركة الكاميرا أو اللاعب.  
في Godot، يُحقق هذا التأثير باستخدام عقدتين رئيسيتين:

- **ParallaxBackground2D**: العقدة الحاوية التي تدير تأثير التمرير المتوازي (parallax) كاملاً.
- **ParallaxLayer2D**: طبقات منفصلة داخل ParallaxBackground2D، كل طبقة تتحرك بسرعة مختلفة.

---

## كيف يعمل Parallax2D؟

- تتحرك طبقات الخلفية بسرعات مختلفة عن حركة الكاميرا أو اللاعب.
- الطبقات الأبعد تتحرك أبطأ لإعطاء إحساس بالمسافة والعمق.
- الطبقات الأقرب تتحرك أسرع، وكأنها أقرب للمشاهد.

---

## استخدامات Parallax2D

- خلق خلفيات غنية وذات أبعاد متعددة.
- إضافة عمق بصري للمشهد 2D.
- تحسين جمالية اللعبة وجعلها أكثر واقعية وحيوية.

---

## الخصائص الأساسية

### ParallaxBackground2D

| الخاصية       | الوصف                             |
|---------------|----------------------------------|
| **scroll_base_offset** | إزاحة البداية للتمرير             |
| **scroll_base_scale**  | مقياس حركة التمرير الأساسي       |
| **limit_begin**        | حد بداية التمرير (حدود الخلفية)  |
| **limit_end**          | حد نهاية التمرير                 |

### ParallaxLayer2D

| الخاصية          | الوصف                                                      |
|------------------|-------------------------------------------------------------|
| **motion_scale** | النسبة التي تتحرك بها الطبقة نسبة لحركة الكاميرا (Vector2)  |
| **motion_mirroring** | حجم التكرار الأفقي والعمودي للطبقة (لتكرار الخلفيات)       |
| **offset**        | إزاحة الطبقة                                            |

---

## كيفية الاستخدام

### 1. إعداد ParallaxBackground2D

- أضف عقدة `ParallaxBackground2D` في المشهد (عادةً كطفل لكاميرا أو Node2D رئيسي).

### 2. إضافة طبقات ParallaxLayer2D

- أضف عقدة `ParallaxLayer2D` كأبناء لـ `ParallaxBackground2D`.
- كل طبقة تحتوي على خلفية أو محتوى مختلف (عادةً Sprite أو TextureRect).

### 3. ضبط خصائص الحركة

- اضبط `motion_scale` لكل طبقة لتحديد سرعة حركتها نسبة لحركة الكاميرا.
  - قيمة أقل من (1,1) تعني حركة أبطأ (تبدو أبعد).
  - قيمة أكبر تعني حركة أسرع (تبدو أقرب).

---

## مثال عملي
<div dir=ltr>


```

ParallaxBackground2D
├── ParallaxLayer2D (motion\_scale = Vector2(0.5, 0.5))
│   └── Sprite (خلفية بعيدة)
├── ParallaxLayer2D (motion\_scale = Vector2(0.8, 0.8))
│   └── Sprite (خلفية وسطى)
└── ParallaxLayer2D (motion\_scale = Vector2(1, 1))
└── Sprite (الخلفية الأمامية)

````

<div dir=rtl>

---

## مثال بسيط

<div dir=ltr>


```gdscript
extends Node2D

func _ready():
    var parallax_bg = ParallaxBackground2D.new()
    add_child(parallax_bg)

    # طبقة خلفية بعيدة تتحرك بنصف سرعة الكاميرا
    var layer_far = ParallaxLayer2D.new()
    layer_far.motion_scale = Vector2(0.5, 0.5)
    parallax_bg.add_child(layer_far)

    var sprite_far = Sprite2D.new()
    sprite_far.texture = preload("res://background_far.png")
    layer_far.add_child(sprite_far)

    # طبقة خلفية وسطى تتحرك بسرعة 0.8
    var layer_mid = ParallaxLayer2D.new()
    layer_mid.motion_scale = Vector2(0.8, 0.8)
    parallax_bg.add_child(layer_mid)

    var sprite_mid = Sprite2D.new()
    sprite_mid.texture = preload("res://background_mid.png")
    layer_mid.add_child(sprite_mid)

    # طبقة أمامية تتحرك بسرعة الكاميرا (1,1)
    var layer_near = ParallaxLayer2D.new()
    layer_near.motion_scale = Vector2(1, 1)
    parallax_bg.add_child(layer_near)

    var sprite_near = Sprite2D.new()
    sprite_near.texture = preload("res://background_near.png")
    layer_near.add_child(sprite_near)
```

