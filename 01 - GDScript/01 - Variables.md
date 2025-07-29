<div dir=rtl>

# ما هي المتغيرات؟

المتغير هو اسم يُستخدم لتخزين قيمة داخل البرنامج. يمكن أن تكون هذه القيمة رقم، نص، أو أي نوع بيانات آخر. نستخدم المتغيرات لنحفظ البيانات التي نحتاج نستخدمها أو نعدلها أثناء تشغيل اللعبة.

# كيف نعلن عن متغير في GDScript؟
<div dir=ltr>

```
var اسم_المتغير = القيمة

```
<div dir=rtl>

مثال:
<div dir=ltr>

```
var score = 10
var player_name = "ZomieX"
```
<div dir=rtl>

هنا score متغير يحمل الرقم 10، و player_name متغير يحمل النص "ZomieX".

# أنواع البيانات الأساسية في GDScript
<div dir=ltr>

| النوع        | الوصف                        | مثال                           |
| ------------ | ---------------------------- | ------------------------------ |
| `int`        | أعداد صحيحة (بدون كسور)      | `var age = 25`                 |
| `float`      | أعداد عشرية (كسور)           | `var speed = 4.5`              |
| `bool`       | صحيح أو خطأ (true/false)     | `var is_alive = true`          |
| `String`     | نصوص                         | `var name = "Godot"`           |
| `Vector2`    | نقطة أو إتجاه في بعدين       | `var pos = Vector2(10, 5)`     |
| `Vector3`    | نقطة أو إتجاه في ثلاثة أبعاد | `var pos3d = Vector3(1, 2, 3)` |
| `Array`      | قائمة من القيم               | `var list = [1, 2, 3]`         |
| `Dictionary` | خريطة مفاتيح وقيم            | `var dict = {"key": "value"}`  |
<div dir=rtl>

# تحديد نوع المتغير (Type Hinting)
في GDScript يمكن تحديد نوع المتغير لكي يساعد المحرر في كشف الأخطاء مبكراً:
<div dir=ltr>

```
var health: int = 100
var username: String = "Player"
var velocity: Vector2 = Vector2(0, 0)
```
<div dir=rtl>

- هنا health فقط يقبل أعداد صحيحة.
- إذا حاولت تخزين نص في health سيعطيك الخطأ.

# تغيير قيمة المتغير
يمكنك تعديل المتغير في أي وقت:
<div dir=ltr>

```
var score = 0

func _ready():
    score = 10  # عدل قيمة المتغير
    print(score)  # يطبع 10
```

<div dir=rtl>

# الثوابت Constants
إذا تريد متغير لا يتغير قيمته:
<div dir=ltr>

```
const PI = 3.14159
```
<div dir=rtl>

لا يمكن تعديل PI بعد تعريفه، هذا مفيد للقيم التي تبقى ثابتة في البرنامج.
