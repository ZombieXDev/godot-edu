

<div dir=rtl>

# ما هو DirectionalLight2D؟

`DirectionalLight2D` هو نوع من الإضاءة في Godot مخصص للألعاب ثنائية الأبعاد (2D)، يصدر ضوءًا باتجاه واحد ثابت، يشبه ضوء الشمس أو ضوء بعيد المصدر، حيث تنتشر الأشعة الضوئية في اتجاه معين بشكل متوازي.

---

## مميزات DirectionalLight2D

- يُضيء المشهد من اتجاه محدد بدون نقطة انبعاث محددة (على عكس PointLight2D).
- الضوء يغطي منطقة واسعة باتجاه ثابت.
- لا يعتمد على المسافة (أي الضوء له مدى لا ينقص تدريجيًا).
- مناسب لمحاكاة ضوء الشمس أو ضوء متساوي الاتجاه في مشاهد 2D.

---

## الخصائص الرئيسية لـ DirectionalLight2D

| الخاصية             | الوصف                                                    |
|---------------------|-----------------------------------------------------------|
| **color**           | لون الضوء                                                |
| **energy**          | شدة الضوء (كمية الإضاءة التي يصدرها)                     |
| **shadow_enabled**   | تفعيل أو تعطيل الظلال الناتجة عن هذا الضوء              |
| **shadow_color**     | لون الظل                                                 |
| **shadow_buffer_size** | دقة خريطة الظل (كلما زادت، زادت جودة الظل وأداء أقل) |
| **z_index**          | ترتيب عرض الضوء بالنسبة للعناصر الأخرى                   |
| **transform (rotation)** | اتجاه الضوء (تحديد زاوية اتجاه الأشعة الضوئية)        |

---

## كيف يعمل DirectionalLight2D؟

- يصدر أشعة ضوئية متوازية في اتجاه معين (يتم التحكم فيه عبر تدوير العقدة).
- الضوء يؤثر على جميع الكائنات التي تقبل الإضاءة (مثل Sprites التي تملك خاصية "Light Mode" مفعلة).
- إذا كانت الظلال مفعلة، تُسقط الظلال بناءً على عوائق موجودة في المشهد (مثل `LightOccluder2D`).

---

## كيفية الاستخدام

### 1. إضافة DirectionalLight2D إلى المشهد

- أضف عقدة `DirectionalLight2D` داخل مشهد 2D.

### 2. ضبط الاتجاه

- قم بتدوير العقدة لتغيير اتجاه الضوء (زاوية الدوران تمثل اتجاه الأشعة الضوئية).

### 3. تعديل الخصائص

- قم بتغيير اللون (`color`) وشدة الإضاءة (`energy`) حسب حاجتك.
- فعل الظلال (`shadow_enabled`) إذا أردت ظلالًا حقيقية.

### 4. إضافة LightOccluder2D للأجسام

- لتظهر الظلال، يجب على الأجسام أن تحتوي على عقدة `LightOccluder2D` مع شكل (`OccluderShape2D`) يحدد شكل الظل.

---

## مثال عملي باستخدام GDScript

<div dir=ltr>

```gdscript
extends Node2D

func _ready():
    var dir_light = DirectionalLight2D.new()
    add_child(dir_light)
    
    dir_light.color = Color(1, 1, 0.8)  # ضوء أصفر دافئ
    dir_light.energy = 1.5
    dir_light.shadow_enabled = true
    
    # توجيه الضوء بزاوية 45 درجة
    dir_light.rotation_degrees = 45
```