
<div dir=rtl>

# ما هو MeshInstance2D؟

`MeshInstance2D` هو عقدة في Godot 2D تُستخدم لعرض أشكال هندسية (Mesh) ثنائية الأبعاد في المشهد.  
تتيح لك هذه العقدة رسم مجسمات أو أشكال مخصصة قابلة للتعديل بديناميكية، بدون الحاجة إلى استخدام صور (Sprites).

---

## استخدامات MeshInstance2D

- رسم أشكال هندسية متقدمة مثل مستطيلات، دوائر، مضلعات، أو أشكال مخصصة.
- إنشاء تأثيرات بصرية تعتمد على الأشكال الهندسية.
- رسم خطوط أو مساحات قابلة للتلوين والتحكم بشكل برمجي.
- استخدام Mesh لتوفير أداء أفضل عند التعامل مع أشكال متكررة أو قابلة للتغيير.

---

## الخصائص الأساسية لـ MeshInstance2D

| الخاصية       | الوصف                                                      |
|---------------|-------------------------------------------------------------|
| **mesh**      | الشكل الهندسي (Mesh) الذي سيتم عرضه (مثل QuadMesh، PolygonMesh، إلخ) |
| **material**  | مادة (Material) لتعديل مظهر الـ Mesh مثل اللون، الشفافية، التأثيرات |
| **color**    | لون افتراضي لتلوين الـ Mesh (يستخدم مع بعض المواد)           |
| **transform** | تحكم في موضع، تدوير، مقياس الـ Mesh في المشهد               |
| **z_index**   | ترتيب العرض بالنسبة للعناصر الأخرى                           |

---

## أنواع Mesh شائعة الاستخدام في 2D

- **QuadMesh**: شكل مستطيل بسيط.
- **Polygon2D**: رسم مضلع ثنائي الأبعاد.
- **PrimitiveMesh**: أشكال هندسية أولية.
- **Custom Mesh**: يمكن تعريف Mesh مخصص عبر الكود.

---

## كيفية الاستخدام

### 1. إضافة MeshInstance2D

- أضف عقدة `MeshInstance2D` في مشهد 2D.

### 2. تعيين Mesh

- في الخصائص، عيّن خاصية `mesh` إلى نوع Mesh مناسب (مثل QuadMesh أو PolygonMesh).
- يمكنك إنشاء Mesh جديد من قائمة Mesh أو عبر الكود.

### 3. تعديل المظهر

- عدل المادة (Material) لتغيير اللون، الإضاءة، التأثيرات.
- غيّر خصائص `color` أو `transform` للتحكم في مظهر وموقع الـ Mesh.

---

## مثال عملي باستخدام GDScript

<div dir=ltr>


```gdscript
extends Node2D

func _ready():
    var mesh_instance = MeshInstance2D.new()
    add_child(mesh_instance)

    # إنشاء QuadMesh مستطيل 100x50
    var quad = QuadMesh.new()
    quad.size = Vector2(100, 50)

    mesh_instance.mesh = quad

    # تلوين Mesh باللون الأحمر
    var mat = StandardMaterial2D.new()
    mat.albedo_color = Color(1, 0, 0)
    mesh_instance.material = mat

    # وضع Mesh في وسط الشاشة
    mesh_instance.position = Vector2(200, 200)
```