
# ما هو الـ Class (الصنف)؟

الـ Class هو قالب (وصفة) لإنشاء كائنات (Objects) تحتوي على بيانات (متغيرات) وسلوك (دوال). يستخدم لتنظيم الكود، وإعادة استخدامه بطريقة نظيفة.

كل Node في Godot هو في الحقيقة Class موروث من Class آخر.

## تعريف Class خاص بك

في GDScript، يمكنك كتابة كلاس مثل هذا:
<div dir="ltr">

```
class_name Player

var name = "ZomieX"
var score = 0

func greet():
    print("أهلًا، " + name)
```
</div>

باستخدام class_name يمكنك استخدام هذا الكلاس في ملفات أخرى بسهولة.

## إنشاء كائن (Object) من كلاس

إذا كان الكلاس داخل ملف player.gd وفيه class_name Player:
<div dir="ltr">

```
var p = Player.new()
p.name = "Ahmed"
p.greet()  # يطبع: أهلًا، Ahmed
```
</div>

## دالة _init() (المنشئ / Constructor)

تُستخدم لتجهيز الكائن عند إنشائه:
```
class_name Player

var name
var score

func _init(new_name, new_score = 0):
    name = new_name
    score = new_score
```
وعند إنشاء كائن:
```
var p = Player.new("ZomieX", 100)
```
# الوراثة (Inheritance)

إذا أردت أن يرث كلاس من كلاس آخر:
```
# enemy.gd
class_name Enemy

func attack():
    print("العدو يهاجم!")
```
```
# zombie.gd
extends Enemy
class_name Zombie

func groan():
    print("آآآآغغغ!")

func attack():
    print("الزومبي يعض!")

var z = Zombie.new()
z.groan()     # آآآآغغغ!
z.attack()    # الزومبي يعض!
```
لاحظ أنك تستطيع إعادة تعريف دوال من الكلاس الأب.

## الكلمة المفتاحية extends

تستخدم لتعريف الوراثة من كلاس آخر:
```
extends Node2D  # ترث خصائص وسلوك Node2D
```
## الكلمة المفتاحية super

تُستخدم لاستدعاء دوال الكلاس الأب:
```
func attack():
    super.attack()  # ينفذ دالة attack من Enemy
    print("ثم يهاجم الزومبي!")
```


# أنواع الكلاسات في Godot
| النوع                      | الشرح                        |
| -------------------------- | ---------------------------- |
| Node                       | كل شيء في المشهد يرث من Node |
| Node2D                     | كائن ثنائي الأبعاد           |
| Control                    | واجهات المستخدم              |
| Sprite2D / CharacterBody2D | كائنات رسومية / متحركة       |
| Custom Class               | كلاس مخصص تكتبه أنت          |
