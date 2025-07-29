
<div dir=rtl>

# ما هو RemoteTransform2D؟

`RemoteTransform2D` هو عقدة في Godot تُستخدم لنسخ (مزامنة) التحويل (الموضع، الدوران، المقياس) من عقدة أخرى إلى العقدة التي تحتوي `RemoteTransform2D`.  
بمعنى آخر، تجعل العقدة التي تحوي `RemoteTransform2D` تتبع حركة وتحويل عقدة أخرى في المشهد بشكل تلقائي.

---

## متى نستخدم RemoteTransform2D؟

- عندما تريد أن تتحرك أو تدور أو تتغير عقدة ما طبقًا لعقدة أخرى بشكل مباشر دون الحاجة لكتابة كود.
- لتوصيل التحولات بين عقد مختلفة في المشهد بسهولة.
- مفيد للأشياء التي تريد تزامن تحركاتها مع عنصر آخر، مثل حامل سلاح يتبع اللاعب، أو تأثير يتبع جسم متحرك.

---

## الخصائص الرئيسية لـ RemoteTransform2D

| الخاصية           | الوصف                                     |
|-------------------|-------------------------------------------|
| **remote_path**   | مسار العقدة المصدر التي تريد نسخ تحويلها إليها (NodePath) |
| **remote_position** | هل تزامن الموضع (Position) من المصدر (bool) |
| **remote_rotation** | هل تزامن الدوران (Rotation) من المصدر (bool) |
| **remote_scale**    | هل تزامن المقياس (Scale) من المصدر (bool) |

---

## كيف يعمل RemoteTransform2D؟

- تُحدد عقدة المصدر عبر `remote_path`.
- العقدة التي تحوي RemoteTransform2D تستقبل تحديثات الموضع، الدوران، والمقياس من عقدة المصدر تلقائيًا.
- يمكن اختيار أي من هذه التحويلات التي تريد مزامنتها.

---

## كيفية الاستخدام

### 1. أضف RemoteTransform2D كطفل للعقدة التي تريد تحريكها تلقائيًا.

### 2. في خاصية `remote_path` حدد المسار لعقدة المصدر (العقدة التي تريد تتبعها).

### 3. فعّل أو أوقف مزامنة الموضع، الدوران، والمقياس حسب حاجتك.

---

## مثال عملي



<div dir=ltr>


```gdscript
# هيكل المشهد:
# Player (Node2D)
# ├── RemoteTransform2D
# Weapon (Node2D)

# هدف: جعل Weapon يتبع تحولات Player عبر RemoteTransform2D

func _ready():
    var weapon = $Weapon
    var remote_transform = weapon.get_node("RemoteTransform2D")
    remote_transform.remote_path = "../Player"
    remote_transform.remote_position = true
    remote_transform.remote_rotation = true
    remote_transform.remote_scale = false  # لن يتم مزامنة المقياس

```