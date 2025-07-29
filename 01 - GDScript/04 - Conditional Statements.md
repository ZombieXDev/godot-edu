<div dir=rtl>

# ما هي جملة if؟
## الشكل الأساسي:
<div dir="ltr">

```
if شرط:
    # كود ينفذ إذا كان الشرط صحيح
```

</div>

## مثال بسيط:
<div dir="ltr">

```
var score = 90

if score > 80:
    print("ممتاز!")
```

</div>

النتيجة: يطبع "ممتاز!" لأن الشرط score > 80 صحيح.

## استخدام else (وإلا)

else تُستخدم إذا لم يتحقق الشرط في if.
<div dir="ltr">

```
var health = 0

if health > 0:
    print("اللاعب حي")
else:
    print("اللاعب مات")
```

</div>

إذا health صفر أو أقل، راح يطبع "اللاعب مات".

## استخدام elif (وإلا إذا)

elif تسمح لك بإضافة شروط إضافية قبل الوصول إلى else.
<div dir="ltr">

```
var grade = 75

if grade >= 90:
    print("ممتاز")
elif grade >= 70:
    print("جيد جداً")
elif grade >= 50:
    print("ناجح")
else:
    print("راسب")
```
</div>

## شروط متعددة باستخدام and / or

- ``and:`` كل الشروط يجب أن تكون صحيحة.

- ``or:`` يكفي شرط واحد يكون صحيح.

<div dir="ltr">

```
var age = 20
var has_id = true

if age >= 18 and has_id:
    print("مسموح بالدخول")
```

</div> 

## استخدام not لنفي الشرط
<div dir="ltr">

```
var is_dead = false

if not is_dead:
    print("اللاعب لا يزال حي")
```

</div> 

## ملاحظات مهمة:

- لا تنسى كتابة النقطة : بعد if, elif, و else.

- كل الكود الذي يتبع الشرط يجب أن يكون مزاحاً لليمين (بـ Tab أو 4 مسافات).

- يمكن استخدام () حول الشروط لكن ليس إلزامياً.