<div dir="rtl">


# ما هي `Skeleton2D`؟

`Skeleton2D` هي عقدة تُستخدم في الألعاب ثنائية الأبعاد للتحكم في حركة الشخصيات أو العناصر عن طريق نظام العظام (Bones).

يمكنك التفكير بها كهيكل عظمي داخل الشخصية يسمح بتحريك أجزاء مختلفة (كالذراعين، الساقين، الرأس) بطريقة سلسة وطبيعية.

---

## لماذا نستخدم `Skeleton2D`؟

* لتحريك الشخصيات أو الكائنات المعقدة بدون الحاجة لرسم كل حركة يدويًا.
* لتسهيل عمل الرسوم المتحركة (Animation) عن طريق تحريك العظام بدلاً من تحريك كل بكسل.
* يسمح بالتحكم الديناميكي بحركات الشخصية أثناء اللعب.

---

## كيف تعمل؟

* تحتوي `Skeleton2D` على مجموعة من العظام (Bones).
* كل عظمة يمكن ربطها بجزء من الصورة أو الرسمة (عادة عبر `Skin` أو `Mesh`).
* تحريك العظام يحرك الأجزاء المرتبطة بها بشكل سلس.

---

## الخصائص المهمة في `Skeleton2D`

| الخاصية       | الوصف                                              |
| ------------- | -------------------------------------------------- |
| `bones`       | قائمة العظام (Bones) التي يمكن تعديلها وإدارتها.   |
| `global_pose` | المصفوفة التي تحدد موقع العظام في المشهد بشكل عام. |
| `root_bone`   | العظمة الجذرية التي تبدأ منها بقية العظام.         |
| `custom_pose` | إمكانية تعديل وضعية العظام يدويًا أثناء التشغيل.   |
| `skin`        | الجلد أو الرسومات المرتبطة بالعظام.                |

---

## كيف تضيف وتستخدم `Skeleton2D`؟

1. أضف عقدة `Skeleton2D` للمشهد.
2. أضف العظام باستخدام أدوات Godot داخل محرر العظام.
3. اربط الرسومات أو أجزاء الصورة بالعظام.
4. تحكم بحركات العظام عبر البرمجة أو باستخدام `AnimationPlayer`.

---

## دوال مهمة في `Skeleton2D`

| الدالة                                 | الوصف                             |
| -------------------------------------- | --------------------------------- |
| `get_bone_count()`                     | تعيد عدد العظام في الهيكل.        |
| `get_bone_name(bone_idx)`              | تعيد اسم العظمة حسب رقمها.        |
| `find_bone(name)`                      | تعيد رقم العظمة حسب الاسم.        |
| `set_bone_global_pose(bone_idx, pose)` | تغير وضعية عظمة معينة في العالم.  |
| `get_bone_global_pose(bone_idx)`       | تحصل على وضعية العظمة في العالم.  |
| `set_bone_custom_pose(bone_idx, pose)` | تعيين وضعية مخصصة للعظمة (مؤقتة). |
| `clear_bones()`                        | تمسح جميع العظام من الهيكل.       |

---


</div>
