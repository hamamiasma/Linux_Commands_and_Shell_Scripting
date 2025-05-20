# Linux_Commands_and_Shell_Scripting


```bash
sudo apt update

```

1.ما يفعله هذا الأمر:
- يجلب قائمة جديدة من الحزم والإصدارات من الإنترنت (من المصادر المحددة في ملف: /etc/apt/sources.list)
- لا يثبت أو يغير أي شيء، فقط يحدث البيانات.

---

✅ 1.2 ترقية محرر النصوص nano

nano هو محرر نصوص بسيط يُستخدم داخل الطرفية (terminal).

🔧 الأمر المستخدم للترقية:
```bash
sudo apt upgrade nano
```
---


تمرين 2 - إنشاء وتحرير الملفات باستخدام Vim

---

📌 ما هو Vim؟
- Vim هو محرر نصوص قوي ومخصص للمستخدمين المتقدمين، ويتميز بالكفاءة والسرعة.
- ليس مثبتًا بشكل افتراضي، لذا يجب تثبيته يدويًا.

🔧 الأمر:

```bash
sudo apt install vim
```
---

🧪 تمرين 2 - إنشاء وتحرير الملفات باستخدام nano

✅ 2.1 الانتقال إلى مجلد المشروع
المجلد:
```bash
/home/project
```

🔧 الأمر:
```bash
cd/home/project
```

✅ 2.2 إنشاء وتحرير ملف نصي باستخدام nano

🔧 الأمر:

```bash
nano hello_world.txt
```
✍️ اكتب في المحرر:
```bash
Hello world!
This is the second line of my first-ever text file created with nano.
```
🛑 للحفظ والخروج:
- اضغط CTRL + X
- ثم Y للحفظ
- ثم Enter

2.3 التحقق من الملف

🔧 الأمر:
```bash
cat hello_world.txt
```
👀 يجب أن ترى:
```bash
Hello world!
This is the second line of my first-ever text file created with nano.
```
---

3.1 مقدمة سريعة عن Vim

 وضعا Vim:
- Insert Mode: لكتابة النص
- Command Mode: للتنقل والحفظ والخروج

🔧 تشغيل Vim:
```bash
vim
```
📖 أوامر مهمة:
- المساعدة: :
 ```bash
 -help
 ```
- الخروج:
```bash
:q
 ```

 للتعلم المتقدم: vim.org

---

3.2 إنشاء وتحرير ملف نصي باستخدام Vim

1️⃣ انتقل إلى مجلد المشروع:
 ```bash
cd /home/project
 ```
2️⃣ أنشئ وحرر ملفًا:
 ```bash
vim hello_world_2.txt
 ```
3️⃣ اضغط i للدخول إلى Insert Mode، ثم اكتب:
 ```bash
Hello World!
This is the second line.
 ```
4️⃣ اضغط Esc للعودة إلى Command Mode

5️⃣ للحفظ:
 ```bash
:w
 ```
6️⃣ للخروج:
 ```bash
:q
 ```
---

 مراجعة الأوامر الأساسية في Vim:

المهمة | الأمر داخل Vim
------|------------------
الدخول إلى Insert mode | i
الرجوع إلى Command mode | Esc
حفظ الملف | :w
الخروج من Vim | :q
حفظ وخروج معًا | :wq
الخروج بدون حفظ | :q!

---

 مقارنة بين Vim و Nano

المقارنة | Vim | Nano
---------|-----|------
سهولة الاستخدام | صعب للمبتدئين | سهل جدًا
وضعية التحرير | Insert + Command | مباشر
الوظائف المتقدمة | قوي جدًا | محدود
الاختصارات | تعتمد على الأوامر | واضحة أسفل الشاشة
السرعة | سريع بعد التعود | أبطأ قليلًا
الدعم البرمجي | ممتاز للمطورين | جيد للمستخدمين العاديين
الحفظ والخروج | :w و :q | Ctrl + O و Ctrl + X
الانتشار | شائع بين المطورين | شائع بين المبتدئين

---

 متى تستخدم كل محرر؟

✅ استخدم Nano إذا:
- كنت مبتدئًا في Linux
- تريد التحرير بسرعة وسهولة
- تقوم بتعديلات بسيطة

✅ استخدم Vim إذا:
- تحتاج لتعديلات معقدة
- تعمل كثيرًا في الطرفية
- تريد تخصيص وتطوير بيئة العمل

### 📝 Exercise 1: تعديل ملف باستخدام nano

1. افتح الملف الحالي:
```bash
nano hello_world.txt
```

2. أضف السطر التالي داخل الملف:
```
This is line three of my new file.
```

3. لحفظ الملف والخروج:
- اضغط `CTRL + X`
- ثم `Y` للحفظ
- ثم `Enter` لتأكيد اسم الملف

💡 **نصيحة:** استخدم زر السهم ↑ للرجوع إلى الأوامر السابقة في الطرفية.

---

### 📝 Exercise 2: إنشاء ملف نصي باستخدام Vim وتنفيذه باستخدام Bash

1. افتح محرر Vim لإنشاء الملف:
```bash
vim done.txt
```

2. اضغط `i` للدخول إلى Insert mode.

3. أضف السطر التالي:
```bash
echo "I am done with the lab!"
```

4. للحفظ والخروج:
- اضغط `Esc` للعودة إلى Command mode
- اكتب:
```bash
:wq
```
واضغط `Enter`

5. لتشغيل الملف باستخدام Bash:
```bash
bash done.txt
```


---


## تمرين - أوامر معلومات النظام والمستخدم

---

### 1.1 عرض اسم المستخدم الحالي
```bash
whoami
```
يعرض اسم المستخدم الحالي مثل:
```
theia
```

---

### 1.2 عرض معلومات النظام الأساسية
```bash
uname
```
 يعرض اسم النواة (Linux)

```bash
uname -a
```
 يعرض معلومات مفصلة مثل:
- اسم النواة
- اسم المضيف
- إصدار النواة وتاريخها
- نوع الجهاز والمنصة

---

### 1.3 معرفة هوية المستخدم والمجموعة
```bash
id
```
 مثال:
```
uid=1001(theia) gid=1001(theia) groups=1001(theia),27(sudo)
```

---

###  1.4 عرض المساحة المتوفرة في القرص
```bash
df
```
📌 يعرض المساحة بوحدات 512 بايت

```bash
df -h
```
 يعرض المساحة بصيغة قابلة للقراءة (مثل GB، MB)

---

###  1.5 عرض العمليات الجارية
```bash
ps
```
 يعرض عمليات المستخدم الحالي

```bash
ps -e
```
 يعرض جميع العمليات الجارية في النظام

---

### 1.6 عرض العمليات ومصادر النظام بشكل لحظي
```bash
top
```
يعرض العمليات واستهلاك المعالج والذاكرة

```bash
top -n 10
```
 التحديث 10 مرات ثم الخروج تلقائيًا

 مفاتيح الفرز داخل top:
- `m`: الذاكرة
- `p`: المعالج
- `n`: PID
- `t`: وقت التشغيل

---

### 1.7 طباعة رسالة على الشاشة
```bash
echo "Welcome to the linux lab"
```
نتيجة:
```
Welcome to the linux lab
```

```bash
echo -e "This will be printed \nin two lines"
```
نتيجة:
```
This will be printed
in two lines
```

---

### 1.8 عرض التاريخ والوقت الحالي
```bash
date
```
 يعرض التاريخ والوقت

```bash
date "+%D"
```
 يعرض التاريخ بصيغة mm/dd/yy

📋 أشهر الاختصارات:
- `%d`: يوم الشهر
- `%h`: اسم الشهر
- `%m`: رقم الشهر
- `%Y`: السنة
- `%T`: الوقت HH:MM:SS

---

### 1.9 عرض دليل الاستخدام لأمر ما
```bash
man ls
```
 يعرض صفحة المساعدة للأمر `ls`

```bash
man -k .
```
يعرض جميع صفحات المساعدة المتاحة

---

pwd: to get the location of your present working directory
ls: to list the files and directories within a directory
mkdir: to create a new directory
cd: to change your present working directory
touch: to create a new file
find: to search for and locate files
rm: to remove a file
mv: to rename or move a file
cp: to copy a file


---
 **النتيجة المتوقعة في الطرفية:**
```
I am done with the lab!
```
---


## 🔐 Security: Managing File Permissions and Ownership


### ❓ لماذا نحتاج لصلاحيات الملفات وملكيتها؟
نظام Linux هو نظام متعدد المستخدمين، ما يعني أن المستخدمين الآخرين يمكنهم رؤية ملفاتك ما لم تقم بتقييد ذلك. لتأمين ملفات حساسة (مثل وثائق ضريبية أو ملفات عمل)، تحتاج لتحديد من يستطيع الوصول إلى هذه الملفات.

---

### 👥 ملكية الملفات في Linux

هناك 3 مستويات للملكية:
- **User**: المستخدم الذي أنشأ الملف.
- **Group**: مجموعة من المستخدمين.
- **Other**: أي شخص آخر على النظام.

فقط مالك الملف يستطيع تغيير صلاحياته.

---

### 🔍 عرض صلاحيات الملفات

```bash
echo "Who can read this file?" > my_new_file
more my_new_file
ls -l my_new_file
```

 مثال الناتج:
```
-rw-r--r-- 1 theia users 25 Dec 22 17:47 my_new_file
```

 تفسير الصلاحيات:
- `rw-` → صلاحيات المستخدم: قراءة وكتابة
- `r--` → صلاحيات المجموعة: قراءة فقط
- `r--` → صلاحيات الآخرين: قراءة فقط

🚩 الملاحظة:
- `-` في البداية يعني ملف.
- `d` في البداية تعني مجلد (directory).

---

### 📁 صلاحيات المجلدات

| الصلاحية | المعنى                                      |
|----------|----------------------------------------------|
| r        | عرض محتويات المجلد (ls)                     |
| w        | إضافة أو حذف ملفات داخل المجلد             |
| x        | الدخول إلى المجلد باستخدام cd              |

---

### 🔒 جعل الملف خاص (Private)

```bash
chmod go-r my_new_file
ls -l my_new_file
```

 الناتج:
```
-rw------- 1 theia users 24 Dec 22 18:49 my_new_file
```

✅ باستخدام `chmod go-r` أزلنا صلاحية القراءة من المجموعة والآخرين.

---

### ⚙️ الملفات التنفيذية (Executable Files)

- الملف التنفيذي يحتوي على أوامر تُفسّر مباشرة من قبل النظام.
- يشمل البرامج النصية (Scripts) مثل Bash scripts.
  
 لكي يكون النص التنفيذي قابل للتشغيل:
1. يجب إعطاء صلاحية التنفيذ `chmod +x filename`
2. يجب أن يحتوي على **shebang** مثل:
```bash
#!/bin/bash
```

 مثال مستقبلي ستتعلمه في Scripting:
```bash
#!/bin/bash
echo "This is an executable script!"
```

---



## Exercise 1 - Viewing and Modifying File Access Permissions

---

###  1.1 عرض صلاحيات الوصول إلى الملفات

📥 **تنزيل الملفات المطلوبة:**
```bash
cd /home/project
wget https://cf-courses-data.s3.us.cloud-object-storage.appdomain.cloud/IBM-LX0117EN-SkillsNetwork/labs/module%201/usdoi.txt
```

 كل ملف يحتوي على صلاحيات مقسّمة إلى:
- **User (u)** – المستخدم صاحب الملف
- **Group (g)** – مجموعة المستخدم
- **Other (o)** – باقي المستخدمين

 **عرض الصلاحيات لملف:**
```bash
ls -l usdoi.txt
```

 **مثال ناتج:**
```
-rw-r--r-- 1 theia theia 8121 May 31 16:45 usdoi.txt
```

🔍 التحليل:
- `rw-` → للمستخدم: قراءة وكتابة
- `r--` → للمجموعة: قراءة فقط
- `r--` → للآخرين: قراءة فقط
- لا أحد لديه صلاحية التنفيذ (x)

---

### ✅ 1.2 تعديل صلاحيات الملفات

🛠 **أمر التعديل:** `chmod` (اختصار لـ change mode)

| الرمز | المعنى                 |
|-------|-------------------------|
| `r`   | قراءة (read)            |
| `w`   | كتابة (write)           |
| `x`   | تنفيذ (execute)         |
| `u`   | المستخدم                 |
| `g`   | المجموعة                 |
| `o`   | الآخرون                 |
| `+`   | إضافة صلاحية            |
| `-`   | إزالة صلاحية            |

---

 **أمثلة عملية:**

🔧 **إزالة صلاحية القراءة من الجميع:**
```bash
chmod -r usdoi.txt
ls -l usdoi.txt
```

🔧 **إعادة صلاحية القراءة للجميع:**
```bash
chmod +r usdoi.txt
ls -l usdoi.txt
```

🔧 **إزالة صلاحية القراءة فقط من "الآخرين":**
```bash
chmod o-r usdoi.txt
ls -l usdoi.txt
```

 تأكد في كل مرة من خلال:
```bash
ls -l usdoi.txt
```

---


## 🧪 Exercise 2 - Managing Directory Permissions

---

### ✅ 2.1 عرض صلاحيات الوصول الافتراضية للمجلدات

📁 **الصلاحيات الأساسية للمجلدات:**

| الصلاحية | الوظيفة                                 |
|----------|------------------------------------------|
| r        | عرض محتويات المجلد (`ls`)               |
| w        | إضافة/حذف ملفات من المجلد               |
| x        | الدخول إلى المجلد (`cd`)                |

🔧 **الخطوات:**
```bash
cd /home/project
mkdir test
ls -l
```

📌 **مثال ناتج:**
```
drwxr-sr-x 2 theia users 4096 May 15 14:06 test
```

🔍 **التفسير:**
- `drwxr-sr-x`: مجلد (`d`)
- `rwx`: للمستخدم (theia) — قراءة، كتابة، تنفيذ
- `r-x`: للمجموعة — قراءة، تنفيذ
- `r-x`: للآخرين — قراءة، تنفيذ
- `s`: صلاحية خاصة (SGID)

---
 **تجربة الدخول وإنشاء مجلدات:**
```bash
cd test
mkdir test2
cd ../
```

---

### 2.2 إزالة صلاحية التنفيذ للمستخدم

🔧 **إزالة صلاحية `x` من المستخدم:**
```bash
chmod u-x test
```

 **محاولة الدخول إلى test:**
```bash
cd test
```

 **النتيجة:**
```
bash: cd: test: Permission denied
```

 **لكن يمكنك مشاهدة محتويات المجلد:**
```bash
ls -l
```

 **محاولة إنشاء مجلد داخل test:**
```bash
mkdir test/test3
```

📌 **النتيجة:**
```
mkdir: cannot create directory ‘test/test’: Permission denied
```

---

### استرجاع صلاحية التنفيذ، وإزالة صلاحية الكتابة

🔧 **استرجاع التنفيذ وإزالة الكتابة:**
```bash
chmod u+x test
chmod u-w test
ls -l
```

**الدخول إلى test أصبح ممكنًا:**
```bash
cd test
```

🚫 **لكن لا يمكنك إنشاء مجلد جديد:**
```bash
mkdir test_again
```

 **النتيجة:**
```
mkdir: cannot create directory ‘test_again’: Permission denied
```

---


## Verwendung des `ls`-Befehls in Linux

Der `ls`-Befehl wird verwendet, um Dateien und Verzeichnisse in einem Verzeichnis aufzulisten. Mit verschiedenen Optionen kann das Verhalten des Befehls angepasst werden.

### Häufig verwendete Optionen

| Option | Beschreibung                                                                                    |
| ------ | ----------------------------------------------------------------------------------------------- |
| `-a`   | Listet alle Dateien auf, einschließlich versteckter Dateien (die mit einem Punkt beginnen)      |
| `-d`   | Zeigt nur Verzeichnisse an, keine Dateien                                                       |
| `-h`   | Gibt Dateigrößen in lesbarem Format aus (z. B. 1K, 234M, 2G); wird mit `-l` oder `-s` verwendet |
| `-l`   | Gibt eine detaillierte Liste aus mit Rechten, Besitzer, Größe und Änderungsdatum                |
| `-S`   | Sortiert nach Dateigröße, größte zuerst                                                         |
| `-t`   | Sortiert nach Änderungsdatum, neueste zuerst                                                    |
| `-r`   | Kehrt die Sortierreihenfolge um                                                                 |

### Beispiel

Um eine detaillierte Liste aller Dateien im Verzeichnis `/etc` anzuzeigen, einschließlich versteckter Dateien, verwenden Sie:

```bash
ls -la /etc
```

Diese Kombination von Optionen:

* `-l` zeigt eine lange Liste mit detaillierten Informationen,
* `-a` zeigt auch versteckte Dateien,
* `/etc` gibt das Zielverzeichnis an.

---

Weitere Informationen finden Sie in der Manpage mit:

```bash
man ls
```

