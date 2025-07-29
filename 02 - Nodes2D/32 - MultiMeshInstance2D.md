<div dir=rtl>

# ما هو MultiMeshInstance2D؟

`MultiMeshInstance2D` هو عقدة في Godot 2D تتيح لك رسم عدد كبير من نسخ (Instances) من نفس الـ Mesh بكفاءة عالية، باستخدام تقنية **الرسوم المتعددة (instancing)**.  
هذا مفيد جدًا عند الحاجة إلى عرض آلاف الأجسام المتشابهة (مثل الأشجار، العشب، أو الجسيمات) بأداء ممتاز.

---

## لماذا نستخدم MultiMeshInstance2D؟

- تحسين الأداء عند رسم أعداد كبيرة من العناصر المتشابهة.
- تقليل استهلاك الذاكرة والمعالج مقارنة بإنشاء نسخ منفصلة لكل جسم.
- مناسب لألعاب 2D التي تحتوي على الكثير من العناصر المتكررة في المشهد.

---

## الخصائص الأساسية لـ MultiMeshInstance2D

| الخاصية            | الوصف                                                      |
|--------------------|-------------------------------------------------------------|
| **multimesh**      | كائن `MultiMesh` يحتوي على بيانات النسخ (Mesh، عدد النسخ، التحويلات) |
| **color**          | لون افتراضي يمكن تطبيقه على النسخ (إذا كان الـ MultiMesh يدعم الألوان) |
| **mesh**           | الشكل الهندسي المستخدم لكل نسخة (يجب تعيينه داخل MultiMesh) |
| **visible_instances** | عدد النسخ المراد عرضها فعليًا                           |
| **transform_format** | صيغة التحويل المستخدمة (2D أو 3D)                        |

---

## كيف يعمل MultiMeshInstance2D؟

- يحتوي على Mesh واحد فقط يتم رسمه عدة مرات باستخدام بيانات تحويل (موضع، دوران، مقياس) لكل نسخة.
- البيانات مخزنة في `MultiMesh` وهو الذي يدير كل النسخ.
- يتم تحديث تحولات النسخ برمجيًا لتحريك أو تعديل النسخ.

---

## كيفية الاستخدام

### 1. إنشاء MultiMeshInstance2D وإعداد MultiMesh

<div dir=ltr>


```gdscript
var multi_mesh_instance = MultiMeshInstance2D.new()
add_child(multi_mesh_instance)

var multi_mesh = MultiMesh.new()
multi_mesh.mesh = preload("res://sprite_mesh.tres")  # تعيين الـ Mesh المستخدم
multi_mesh.instance_count = 1000  # عدد النسخ

multi_mesh_instance.multimesh = multi_mesh

# إعداد التحويلات لكل نسخة (مثال)
for i in range(multi_mesh.instance_count):
    var x = randf() * 800
    var y = randf() * 600
    var transform = Transform2D()
    transform.origin = Vector2(x, y)
    multi_mesh.set_instance_transform_2d(i, transform)
```


<div dir=rtl>

## 2. إضافة MultiMeshInstance2D إلى المشهد

- يتم إضافتها مثل أي عقدة أخرى.

-  لا تحتاج لإنشاء نسخ متعددة من العقد، كل شيء يُدار عبر ``MultiMesh``.