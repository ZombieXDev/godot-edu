<div dir=rtl>

# ما هي الدالة (Function)؟

الدالة هي مجموعة من التعليمات البرمجية تقوم بمهمة معينة، يمكنك استدعاؤها (تشغيلها) متى ما أردت. تستخدم الدوال لتكرار الكود وتسهيل تنظيمه.

## كيفية تعريف دالة في GDScript؟

<div dir=ltr>

```
func اسم_الدالة(معاملات):
    # الكود هنا
```

<div dir=rtl>

- `func` كلمة مفتاحية تعني أنك تعرف دالة جديدة.

- `اسم_الدالة` هو اسم تختاره للدالة.

- `معاملات` (اختياري) هي قيم يمكن إرسالها للدالة لتستخدمها.

## مثال بسيط لدالة

<div dir=ltr>

```
func greet():
    print("مرحباً بك في Godot!")
```

<div dir=rtl>

ولتشغيل الدالة:

<div dir=ltr>

```
greet()
```

<div dir=rtl>

## دالة مع معاملات (Parameters)

<div dir=ltr>

```
func greet(name):
    print("مرحباً، " + name + "!")

```

تشغيل الدالة مع إرسال اسم:

```
greet("ZomieX")  # يطبع: مرحباً، ZomieX!
```

## دالة ترجع قيمة (Return Value)

```
func add(a, b):
    return a + b
```

يمكنك استخدام القيمة الناتجة:

```
var result = add(5, 7)
print(result)  # يطبع 12
```

## دوال مدمجة (Built-in Functions) مهمة في GDScript

- `print()`

تطبع نص أو قيمة في نافذة الإخراج.

```
print("Hello World")
print(5 + 3)
```

- `_ready()`

دالة خاصة تٌنادى تلقائياً عندما يكون المشهد (Scene) جاهز للتشغيل.

```
func _ready():
    print("المشهد جاهز")
```

- `_process(delta)`

تُنادى في كل إطار (Frame) أثناء تشغيل اللعبة. delta هو الوقت بين الإطار الحالي والسابق.

```
func _process(delta):
    print("يمر إطار جديد")
```

- `abs(x)`

تحسب القيمة المطلقة للرقم x.

```
print(abs(-10))  # يطبع 10
```

- `str(value)`

تحول القيمة إلى نص (String).

```
var score = 100
print("النقاط: " + str(score))
```

- `int(value) و float(value)`

تحول القيمة إلى عدد صحيح أو عشري.

```
print(int("42"))    # يطبع 42
print(float("3.14")) # يطبع 3.14
```

- `randi()`

تولد رقم عشوائي صحيح (غير موقوف).

```
print(randi())
```

- `randf()`

تولد رقم عشوائي عشري بين 0 و 1.

```
print(randf())
```
