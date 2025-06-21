# 📜 البرمجة النصية في Linux (Shell Scripting)

## 📋 المحتويات

- [مقدمة عن Shell Scripting](#-مقدمة-عن-shell-scripting)
- [ما هو الـ Shebang](#-ما-هو-الـ-shebang)
- [إنشاء أول سكربت](#-إنشاء-أول-سكربت)
- [إدارة الصلاحيات](#-إدارة-الصلاحيات)
- [المتغيرات في Shell](#-المتغيرات-في-shell)
- [الشروط والتحكم](#-الشروط-والتحكم)
- [الحلقات والتكرار](#-الحلقات-والتكرار)
- [السكربتات التفاعلية](#-السكربتات-التفاعلية)
- [أمثلة عملية متقدمة](#-أمثلة-عملية-متقدمة)
- [أفضل الممارسات](#-أفضل-الممارسات)
- [استكشاف الأخطاء](#-استكشاف-الأخطاء)

## 🎯 مقدمة عن Shell Scripting

### ما هو السكربت؟
**السكربت** هو ملف نصي يحتوي على مجموعة أوامر تُنفذها **مفسّرات (interpreters)** مثل Bash أو Python.

### خصائص السكربتات:
- ❌ **لا تُترجم** (compile) مثل C أو Java
- ✅ **تُنفذ مباشرةً** سطراً بسطر (تفسير حي/فوري)
- ⚡ **أبطأ** من اللغات المترجمة، لكنها **أسهل وأسرع** في التطوير
- 🔄 **قابلة للتعديل** بسهولة بدون إعادة ترجمة

### فوائد Shell Scripting:
- 🤖 **أتمتة المهام المتكررة**
- 💾 **نسخ احتياطي تلقائي**
- ⚙️ **إدارة النظام بكفاءة**
- 🚀 **تجهيز وإعداد المشاريع**
- 🛠️ **إنشاء أدوات مخصصة**
- 📊 **معالجة البيانات والتقارير**

### متى تستخدم Shell Scripts؟
| الاستخدام | الأمثلة |
|-----------|---------|
| **الأتمتة** | تنظيم الملفات، تنظيف النظام |
| **الإدارة** | مراقبة الخوادم، إدارة المستخدمين |
| **التطوير** | build scripts، deployment |
| **النسخ الاحتياطي** | أرشفة البيانات، مزامنة الملفات |

## 🔗 ما هو الـ Shebang؟

### التعريف
**Shebang** (`#!`) هو السطر الأول في السكربت، ويحدد **المفسّر الذي يشغّل السكربت**.

### الصيغة العامة:
```bash
#!/path/to/interpreter
```

### أمثلة شائعة:

| Shebang | الوصف | الاستخدام |
|---------|--------|-----------|
| `#!/bin/bash` | Bash shell (الأشهر) | السكربتات العامة |
| `#!/bin/sh` | Bourne shell | التوافق الأوسع |
| `#!/usr/bin/env bash` | يبحث عن bash في PATH | المرونة في المسارات |
| `#!/usr/bin/env python3` | Python 3 | سكربتات Python |
| `#!/usr/bin/perl` | Perl | معالجة النصوص |

### أهمية الـ Shebang:
- ✅ يحدد المفسر الصحيح تلقائياً
- ✅ يجعل السكربت قابل للتنفيذ مباشرة
- ✅ يضمن التوافق عبر أنظمة مختلفة
- ⚠️ **بدونه**: يجب تحديد المفسر يدوياً

## 🚀 إنشاء أول سكربت

### مثال: Hello World

#### الطريقة التفاعلية (خطوة بخطوة):

```bash
# 1. إنشاء ملف سكربت
touch hello_world.sh

# 2. إضافة الـ shebang
echo "#!/bin/bash" >> hello_world.sh

# 3. إضافة الأمر داخل السكربت
echo "echo 'Hello World!'" >> hello_world.sh

# 4. فحص محتوى الملف
cat hello_world.sh
```

**محتوى الملف:**
```bash
#!/bin/bash
echo 'Hello World!'
```

#### الطريقة المباشرة (باستخدام محرر):

```bash
# إنشاء وتحرير مباشر
nano hello_world.sh
```

**اكتب في المحرر:**
```bash
#!/bin/bash
# سكربت ترحيبي بسيط
echo "مرحباً بك في عالم Shell Scripting!"
echo "تاريخ اليوم: $(date)"
echo "اسم المستخدم: $(whoami)"
```

### تشغيل السكربت

#### الطريقة 1: إعطاء صلاحية تنفيذ

```bash
# إعطاء صلاحية تشغيل
chmod +x hello_world.sh

# تشغيل السكربت
./hello_world.sh
```

#### الطريقة 2: تشغيل مباشر بالمفسر

```bash
# تشغيل بدون إعطاء صلاحيات
bash hello_world.sh
```

### الناتج المتوقع:
```
مرحباً بك في عالم Shell Scripting!
تاريخ اليوم: الجمعة 20 يونيو 2025 10:30:15 UTC
اسم المستخدم: username
```

## 🔐 إدارة الصلاحيات

### فهم صلاحيات السكربت

```bash
# فحص الصلاحيات
ls -l hello_world.sh
```

**قبل chmod +x:**
```
-rw-r--r-- 1 user user 45 Jun 20 10:30 hello_world.sh
```

**بعد chmod +x:**
```
-rwxr-xr-x 1 user user 45 Jun 20 10:30 hello_world.sh
```

### أنواع صلاحيات التنفيذ:

| الأمر | التأثير |
|-------|----------|
| `chmod +x script.sh` | صلاحية تنفيذ للجميع |
| `chmod u+x script.sh` | صلاحية تنفيذ للمالك فقط |
| `chmod 755 script.sh` | rwxr-xr-x (صلاحية كاملة للمالك) |
| `chmod 700 script.sh` | rwx------ (خاص بالمالك فقط) |

### نصائح الأمان:
- 🔒 استخدم `chmod 700` للسكربتات الحساسة
- ⚠️ تجنب `chmod 777` (خطير!)
- ✅ راجع الصلاحيات دورياً

## 📊 المتغيرات في Shell

### إنشاء واستخدام المتغيرات

#### القواعد الأساسية:

```bash
# إنشاء متغير (بدون مسافات!)
firstname=Jeff
lastname=Grossman
age=25

# استخدام المتغير (مع $)
echo $firstname
echo "الاسم: $firstname $lastname"
echo "العمر: $age سنة"
```

#### قواعد تسمية المتغيرات:
- ✅ تبدأ بحرف أو `_`
- ✅ تحتوي على أحرف وأرقام و `_`
- ❌ لا تحتوي على مسافات أو رموز خاصة
- ❌ لا تبدأ برقم

```bash
# صحيح ✅
user_name=Ahmed
USER_AGE=30
file1=data.txt

# خطأ ❌
1user=Ahmed      # يبدأ برقم
user name=Ahmed  # مسافة
user-age=30      # شرطة
```

### أنواع المتغيرات:

#### 1. متغيرات النصوص:

```bash
name="أحمد محمد"
message='مرحباً بك!'
path="/home/user/documents"

echo "الاسم: $name"
echo $message
echo "المسار: $path"
```

#### 2. متغيرات الأرقام:

```bash
num1=10
num2=20
result=$((num1 + num2))

echo "النتيجة: $result"
```

#### 3. متغيرات خاصة:

| المتغير | المعنى |
|---------|---------|
| `$0` | اسم السكربت |
| `$1, $2, ...` | البارامترات المرسلة |
| `$#` | عدد البارامترات |
| `$*` | جميع البارامترات |
| `$$` | PID للعملية الحالية |
| `$?` | رمز الخروج للأمر السابق |

#### مثال على البارامترات:

```bash
#!/bin/bash
# مثال: script.sh param1 param2

echo "اسم السكربت: $0"
echo "البارامتر الأول: $1"
echo "البارامتر الثاني: $2"
echo "عدد البارامترات: $#"
echo "جميع البارامترات: $*"
```

**تشغيل:**
```bash
./script.sh احمد 25
```

**النتيجة:**
```
اسم السكربت: ./script.sh
البارامتر الأول: احمد
البارامتر الثاني: 25
عدد البارامترات: 2
جميع البارامترات: احمد 25
```

## 🔄 الشروط والتحكم

### بنية if الأساسية

```bash
#!/bin/bash
filename="myfile.txt"

if [ -f "$filename" ]; then
    echo "✅ الملف '$filename' موجود."
else
    echo "❌ الملف '$filename' غير موجود."
fi
```

### عمليات الفحص الشائعة:

#### فحص الملفات:

| التعبير | المعنى |
|---------|---------|
| `[ -f file ]` | هل الملف موجود؟ |
| `[ -d dir ]` | هل المجلد موجود؟ |
| `[ -r file ]` | هل الملف قابل للقراءة؟ |
| `[ -w file ]` | هل الملف قابل للكتابة؟ |
| `[ -x file ]` | هل الملف قابل للتنفيذ؟ |
| `[ -e path ]` | هل المسار موجود؟ |

#### فحص النصوص:

| التعبير | المعنى |
|---------|---------|
| `[ "$a" = "$b" ]` | هل النصان متساويان؟ |
| `[ "$a" != "$b" ]` | هل النصان مختلفان؟ |
| `[ -z "$str" ]` | هل النص فارغ؟ |
| `[ -n "$str" ]` | هل النص غير فارغ؟ |

#### فحص الأرقام:

| التعبير | المعنى |
|---------|---------|
| `[ $a -eq $b ]` | مساوي |
| `[ $a -ne $b ]` | غير مساوي |
| `[ $a -lt $b ]` | أقل من |
| `[ $a -le $b ]` | أقل من أو يساوي |
| `[ $a -gt $b ]` | أكبر من |
| `[ $a -ge $b ]` | أكبر من أو يساوي |

### أمثلة عملية للشروط:

#### مثال 1: فحص عمر المستخدم

```bash
#!/bin/bash
echo "كم عمرك؟"
read age

if [ $age -ge 18 ]; then
    echo "🎉 أنت بالغ!"
elif [ $age -ge 13 ]; then
    echo "👦 أنت مراهق"
else
    echo "👶 أنت طفل"
fi
```

#### مثال 2: فحص وجود ملف وإنشاؤه

```bash
#!/bin/bash
config_file="config.txt"

if [ ! -f "$config_file" ]; then
    echo "إنشاء ملف الإعدادات..."
    echo "# ملف الإعدادات" > "$config_file"
    echo "version=1.0" >> "$config_file"
    echo "✅ تم إنشاء $config_file"
else
    echo "📁 ملف الإعدادات موجود مسبقاً"
fi
```

#### مثال 3: شروط مركبة

```bash
#!/bin/bash
echo "أدخل اسم المستخدم:"
read username
echo "أدخل كلمة المرور:"
read -s password  # -s لإخفاء كلمة المرور

if [ "$username" = "admin" ] && [ "$password" = "secret" ]; then
    echo "✅ تم تسجيل الدخول بنجاح!"
elif [ "$username" = "admin" ] && [ "$password" != "secret" ]; then
    echo "❌ كلمة مرور خاطئة"
else
    echo "❌ اسم مستخدم غير صحيح"
fi
```

## 🔁 الحلقات والتكرار

### حلقة for الأساسية

```bash
#!/bin/bash
echo "📂 الملفات النصية الموجودة:"

for file in *.txt; do
    if [ -f "$file" ]; then
        echo "🔹 الملف: $file"
        echo "المحتوى:"
        head -n 1 "$file"
        echo "-------------------"
    fi
done
```

### أنواع حلقات for:

#### 1. حلقة عبر قائمة:

```bash
#!/bin/bash
fruits="تفاح برتقال موز عنب"

for fruit in $fruits; do
    echo "🍎 الفاكهة: $fruit"
done
```

#### 2. حلقة عبر أرقام:

```bash
#!/bin/bash
echo "العد من 1 إلى 10:"

for i in {1..10}; do
    echo "الرقم: $i"
done
```

#### 3. حلقة C-style:

```bash
#!/bin/bash
echo "جدول الضرب للرقم 5:"

for ((i=1; i<=10; i++)); do
    result=$((5 * i))
    echo "5 × $i = $result"
done
```

### حلقة while:

```bash
#!/bin/bash
counter=1

echo "العد حتى 5:"
while [ $counter -le 5 ]; do
    echo "العداد: $counter"
    counter=$((counter + 1))
done
```

### أمثلة عملية للحلقات:

#### مثال 1: نسخ احتياطي متعدد

```bash
#!/bin/bash
directories="Documents Pictures Videos Music"
backup_dir="/backup"

mkdir -p "$backup_dir"

for dir in $directories; do
    if [ -d "$HOME/$dir" ]; then
        echo "📦 نسخ احتياطي لـ $dir..."
        tar -czf "$backup_dir/${dir}_backup.tar.gz" "$HOME/$dir"
        echo "✅ تم: ${dir}_backup.tar.gz"
    else
        echo "⚠️ المجلد $dir غير موجود"
    fi
done

echo "🎉 انتهت عملية النسخ الاحتياطي!"
```

#### مثال 2: مراقبة النظام

```bash
#!/bin/bash
max_checks=5
current_check=1

while [ $current_check -le $max_checks ]; do
    echo "=== فحص رقم $current_check ==="
    echo "الوقت: $(date)"
    echo "المعالج: $(uptime | awk -F'load average:' '{print $2}')"
    echo "الذاكرة: $(free -h | grep Mem | awk '{print $3"/"$2}')"
    echo "القرص: $(df -h / | tail -1 | awk '{print $5}')"
    echo "------------------------"
    
    current_check=$((current_check + 1))
    sleep 5
done
```

## 🗣️ السكربتات التفاعلية

### قراءة المدخلات من المستخدم

#### استخدام read الأساسي:

```bash
#!/bin/bash
echo "ما هو اسمك؟"
read name
echo "أهلاً بك يا $name!"
```

#### خيارات read المتقدمة:

```bash
#!/bin/bash

# قراءة مع رسالة في نفس السطر
read -p "أدخل اسمك: " name

# قراءة كلمة مرور (مخفية)
read -s -p "أدخل كلمة المرور: " password
echo  # سطر جديد

# قراءة مع حد أقصى للوقت
read -t 10 -p "لديك 10 ثوان لإدخال إجابتك: " answer

# قراءة حرف واحد فقط
read -n 1 -p "اضغط على أي مفتاح للمتابعة..." key
echo
```

### مثال شامل: سكربت تفاعلي لإدارة الملفات

```bash
#!/bin/bash
# سكربت تفاعلي لإدارة الملفات

echo "🗂️ مدير الملفات التفاعلي"
echo "=========================="

while true; do
    echo
    echo "اختر العملية:"
    echo "1) عرض الملفات الحالية"
    echo "2) إنشاء ملف جديد"
    echo "3) حذف ملف"
    echo "4) نسخ ملف"
    echo "5) البحث عن ملف"
    echo "6) خروج"
    echo
    read -p "اختيارك (1-6): " choice

    case $choice in
        1)
            echo "📁 الملفات في المجلد الحالي:"
            ls -la
            ;;
        2)
            read -p "اسم الملف الجديد: " filename
            if [ ! -z "$filename" ]; then
                touch "$filename"
                echo "✅ تم إنشاء الملف: $filename"
            else
                echo "❌ يجب إدخال اسم الملف"
            fi
            ;;
        3)
            read -p "اسم الملف المراد حذفه: " filename
            if [ -f "$filename" ]; then
                read -p "هل أنت متأكد من حذف '$filename'؟ (y/n): " confirm
                if [ "$confirm" = "y" ] || [ "$confirm" = "Y" ]; then
                    rm "$filename"
                    echo "✅ تم حذف الملف: $filename"
                else
                    echo "❌ تم إلغاء العملية"
                fi
            else
                echo "❌ الملف غير موجود"
            fi
            ;;
        4)
            read -p "اسم الملف المصدر: " source
            read -p "اسم الملف الهدف: " target
            if [ -f "$source" ]; then
                cp "$source" "$target"
                echo "✅ تم نسخ $source إلى $target"
            else
                echo "❌ الملف المصدر غير موجود"
            fi
            ;;
        5)
            read -p "اسم الملف للبحث عنه: " searchfile
            found=$(find . -name "*$searchfile*" -type f)
            if [ ! -z "$found" ]; then
                echo "🔍 الملفات الموجودة:"
                echo "$found"
            else
                echo "❌ لم يتم العثور على ملفات تحتوي على: $searchfile"
            fi
            ;;
        6)
            echo "👋 شكراً لاستخدام مدير الملفات!"
            exit 0
            ;;
        *)
            echo "❌ اختيار غير صحيح. يرجى اختيار رقم من 1 إلى 6"
            ;;
    esac
done
```

## 🛠️ أمثلة عملية متقدمة

### مثال 1: نظام نسخ احتياطي ذكي

```bash
#!/bin/bash
# نظام نسخ احتياطي ذكي

BACKUP_SOURCE="$HOME/Documents"
BACKUP_DEST="$HOME/Backups"
DATE=$(date +%Y%m%d_%H%M%S)
LOG_FILE="$BACKUP_DEST/backup.log"

# دالة للكتابة في السجل
log_message() {
    echo "$(date '+%Y-%m-%d %H:%M:%S'): $1" >> "$LOG_FILE"
}

# إنشاء مجلد النسخ الاحتياطية
mkdir -p "$BACKUP_DEST"

echo "🔄 بدء عملية النسخ الاحتياطي..."
log_message "بدء النسخ الاحتياطي"

# فحص وجود المجلد المصدر
if [ ! -d "$BACKUP_SOURCE" ]; then
    echo "❌ المجلد المصدر غير موجود: $BACKUP_SOURCE"
    log_message "خطأ: المجلد المصدر غير موجود"
    exit 1
fi

# حساب حجم البيانات
SOURCE_SIZE=$(du -sh "$BACKUP_SOURCE" | cut -f1)
echo "📊 حجم البيانات: $SOURCE_SIZE"

# إنشاء النسخة الاحتياطية
BACKUP_FILE="$BACKUP_DEST/backup_$DATE.tar.gz"

echo "📦 إنشاء الأرشيف..."
if tar -czf "$BACKUP_FILE" -C "$(dirname "$BACKUP_SOURCE")" "$(basename "$BACKUP_SOURCE")" 2>/dev/null; then
    BACKUP_SIZE=$(du -sh "$BACKUP_FILE" | cut -f1)
    echo "✅ تم إنشاء النسخة الاحتياطية: backup_$DATE.tar.gz"
    echo "📦 حجم الأرشيف: $BACKUP_SIZE"
    log_message "نجح النسخ الاحتياطي - الحجم: $BACKUP_SIZE"
    
    # حذف النسخ القديمة (أكثر من 7 أيام)
    OLD_BACKUPS=$(find "$BACKUP_DEST" -name "backup_*.tar.gz" -mtime +7)
    if [ ! -z "$OLD_BACKUPS" ]; then
        echo "🧹 حذف النسخ القديمة..."
        echo "$OLD_BACKUPS" | while read backup; do
            rm "$backup"
            echo "🗑️ تم حذف: $(basename "$backup")"
        done
        log_message "تم حذف النسخ القديمة"
    fi
else
    echo "❌ فشل في إنشاء النسخة الاحتياطية"
    log_message "فشل النسخ الاحتياطي"
    exit 1
fi

echo "🎉 انتهت عملية النسخ الاحتياطي بنجاح!"
```

### مثال 2: مراقب النظام الشامل

```bash
#!/bin/bash
# مراقب النظام الشامل

REPORT_FILE="system_report_$(date +%Y%m%d_%H%M%S).txt"

# دالة لإضافة عنوان للتقرير
add_header() {
    echo "========================================" >> "$REPORT_FILE"
    echo "$1" >> "$REPORT_FILE"
    echo "========================================" >> "$REPORT_FILE"
}

# دالة لإضافة محتوى للتقرير
add_content() {
    echo "$1" >> "$REPORT_FILE"
    echo "" >> "$REPORT_FILE"
}

echo "🔍 جمع معلومات النظام..."

# معلومات أساسية
add_header "معلومات النظام الأساسية"
add_content "تاريخ التقرير: $(date)"
add_content "اسم الجهاز: $(hostname -f)"
add_content "نظام التشغيل: $(uname -a)"
add_content "المستخدم الحالي: $(whoami)"
add_content "وقت تشغيل النظام: $(uptime)"

# معلومات المعالج والذاكرة
add_header "أداء النظام"
add_content "معلومات المعالج:"
add_content "$(lscpu | grep 'Model name\|CPU(s)\|MHz')"
add_content "استخدام الذاكرة:"
add_content "$(free -h)"
add_content "متوسط الحمولة:"
add_content "$(uptime | awk -F'load average:' '{print $2}')"

# مساحة القرص
add_header "مساحة التخزين"
add_content "$(df -h)"

# الشبكة
add_header "معلومات الشبكة"
add_content "واجهات الشبكة:"
add_content "$(ip addr show | grep -E 'inet|UP')"
add_content "اختبار الاتصال:"
if ping -c 3 8.8.8.8 &>/dev/null; then
    add_content "✅ الاتصال بالإنترنت متاح"
else
    add_content "❌ لا يوجد اتصال بالإنترنت"
fi

# العمليات النشطة
add_header "العمليات النشطة (أكثر 10 استهلاكاً للمعالج)"
add_content "$(ps aux --sort=-%cpu | head -11)"

# تحذيرات النظام
add_header "تحذيرات النظام"

# فحص مساحة القرص
DISK_USAGE=$(df / | tail -1 | awk '{print $5}' | sed 's/%//')
if [ $DISK_USAGE -gt 80 ]; then
    add_content "⚠️ تحذير: مساحة القرص الرئيسي ممتلئة بنسبة $DISK_USAGE%"
fi

# فحص الذاكرة
MEMORY_USAGE=$(free | grep Mem | awk '{printf("%.0f", $3/$2 * 100.0)}')
if [ $MEMORY_USAGE -gt 80 ]; then
    add_content "⚠️ تحذير: استخدام الذاكرة مرتفع: $MEMORY_USAGE%"
fi

# فحص الحمولة
LOAD_AVG=$(uptime | awk -F'load average:' '{print $2}' | awk -F',' '{print $1}' | sed 's/ //')
CPU_CORES=$(nproc)
HIGH_LOAD=$(echo "$LOAD_AVG > $CPU_CORES" | bc -l 2>/dev/null || echo 0)
if [ "$HIGH_LOAD" = "1" ]; then
    add_content "⚠️ تحذير: حمولة النظام مرتفعة: $LOAD_AVG (الأنوية: $CPU_CORES)"
fi

echo "✅ تم إنشاء التقرير: $REPORT_FILE"
echo "📊 لعرض التقرير: cat $REPORT_FILE"
```

## ✨ أفضل الممارسات

### 1. هيكلة السكربت

```bash
#!/bin/bash
# عنوان السكربت ووصف وظيفته
# المؤلف: اسمك
# التاريخ: تاريخ الإنشاء
# الإصدار: 1.0

# ===============================
# المتغيرات العامة
# ===============================
SCRIPT_NAME=$(basename "$0")
LOG_FILE="/var/log/script.log"
DEBUG=false

# ===============================
# الدوال
# ===============================
log_message() {
    echo "$(date '+%Y-%m-%d %H:%M:%S'): $1" | tee -a "$LOG_FILE"
}

show_help() {
    echo "الاستخدام: $SCRIPT_NAME [options]"
    echo "Options:"
    echo "  -h, --help     عرض هذه المساعدة"
    echo "  -v, --verbose  وضع مفصل"
    echo "  -d, --debug    وضع التشخيص"
}

# ===============================
# الكود الرئيسي
# ===============================
main() {
    log_message "بدء تشغيل السكربت"
    
    # منطق السكربت هنا
    
    log_message "انتهاء السكربت بنجاح"
}

# تشغيل الدالة الرئيسية
main "$@"
```

### 2. معالجة الأخطاء

```bash
#!/bin/bash
# تعيين خيارات الأمان
set -euo pipefail  # توقف عند أي خطأ

# دالة للخروج الآمن
cleanup() {
    echo "تنظيف الملفات المؤقتة..."
    rm -f /tmp/script_temp_*
}

# تسجيل دالة التنظيف للتشغيل عند الخروج
trap cleanup EXIT

# دالة لمعالجة الأخطاء
error_handler() {
    echo "❌ خطأ في السطر $1"
    echo "الأمر الفاشل: $2"
    exit 1
}

# تسجيل معالج الأخطاء
trap 'error_handler ${LINENO} "$BASH_COMMAND"' ERR

# مثال على استخدام معالجة الأخطاء
safe_copy() {
    local source="$1"
    local dest="$2"
    
    if [ ! -f "$source" ]; then
        echo "❌ الملف المصدر غير موجود: $source"
        return 1
    fi
    
    if cp "$source" "$dest"; then
        echo "✅ تم نسخ $source إلى $dest"
    else
        echo "❌ فشل في نسخ الملف"
        return 1
    fi
}
```

### 3. التحقق من البارامترات

```bash
#!/bin/bash

# دالة للتحقق من البارامترات
validate_params() {
    if [ $# -lt 2 ]; then
        echo "❌ خطأ: يجب تمرير بارامترين على الأقل"
        show_help
        exit 1
    fi
    
    if [ ! -f "$1" ]; then
        echo "❌ خطأ: الملف غير موجود: $1"
        exit 1
    fi
}

# دالة لمعالجة البارامترات
parse_params() {
    while [[ $# -gt 0 ]]; do
        case $1 in
            -h|--help)
                show_help
                exit 0
                ;;
            -v|--verbose)
                VERBOSE=true
                shift
                ;;
            -f|--file)
                INPUT_FILE="$2"
                shift 2
                ;;
            *)
                echo "❌ خيار غير معروف: $1"
                show_help
                exit 1
                ;;
        esac
    done
}
```

## 🔧 استكشاف الأخطاء

### الأخطاء الشائعة وحلولها

#### 1. خطأ الصلاحيات

```bash
# الخطأ: Permission denied
# الحل:
chmod +x script.sh
```

#### 2. خطأ الـ Shebang

```bash
# خطأ: bad interpreter
# السبب: shebang خاطئ
#!/bin/bash  # ✅ صحيح
#!/bin/bas   # ❌ خطأ إملائي
```

#### 3. مشاكل المتغيرات

```bash
# خطأ شائع: مسافات في التعيين
name = "Ahmed"     # ❌ خطأ
name="Ahmed"       # ✅ صحيح

# عدم استخدام علامات اقتباس
filename=my file.txt      # ❌ خطأ
filename="my file.txt"    # ✅ صحيح
```

#### 4. مشاكل المسارات

```bash
# مشكلة المسارات النسبية
./script.sh              # ✅ من المجلد الحالي
/full/path/script.sh     # ✅ مسار مطلق
script.sh                # ❌ قد لا يعمل
```

### أدوات التشخيص

#### 1. وضع التشخيص

```bash
# تشغيل مع تشخيص مفصل
bash -x script.sh

# أو إضافة في السكربت
#!/bin/bash
set -x  # تفعيل وضع التشخيص
```

#### 2. فحص بناء الجملة

```bash
# فحص الأخطاء النحوية بدون تشغيل
bash -n script.sh
```

#### 3. إضافة رسائل تشخيصية

```bash
#!/bin/bash
DEBUG=true

debug_msg() {
    if [ "$DEBUG" = true ]; then
        echo "🔍 DEBUG: $1" >&2
    fi
}

# استخدام الرسائل التشخيصية
debug_msg "بدء معالجة الملف: $filename"
```

## 📚 ملخص الأوامر السريع

### الأساسيات

| العنصر | الصيغة | مثال |
|---------|--------|-------|
| **Shebang** | `#!/path/to/interpreter` | `#!/bin/bash` |
| **متغير** | `var=value` | `name="Ahmed"` |
| **استخدام متغير** | `$var` أو `${var}` | `echo $name` |
| **قراءة إدخال** | `read var` | `read username` |

### الشروط

| الهيكل | المثال |
|--------|---------|
| **if بسيط** | `if [ condition ]; then ... fi` |
| **if-else** | `if [ condition ]; then ... else ... fi` |
| **if-elif-else** | `if [ condition1 ]; then ... elif [ condition2 ]; then ... else ... fi` |

### الحلقات

| النوع | الصيغة |
|-------|--------|
| **for list** | `for item in list; do ... done` |
| **for range** | `for i in {1..10}; do ... done` |
| **while** | `while [ condition ]; do ... done` |

### عمليات الفحص

| الفحص | المعنى |
|-------|--------|
| `[ -f file ]` | ملف موجود |
| `[ -d dir ]` | مجلد موجود |
| `[ "$a" = "$b" ]` | نصان متساويان |
| `[ $a -eq $b ]` | رقمان متساويان |
| `[ $a -gt $b ]` | a أكبر من b |

## 🔧 البرمجة المتقدمة في Shell

### الأدوات المتقدمة

#### 1. Pipes والـ Filters

**الـ Pipes** (`|`) تنقل مخرجات أمر كمدخلات لأمر آخر:

```bash
# البحث في ملف وترتيب النتائج
cat file.txt | grep "pattern" | sort | uniq

# تحويل النص لأحرف كبيرة
echo "linux scripting" | tr "[a-z]" "[A-Z]"

# استبدال الأحرف المتحركة
echo "Linux is awesome!" | tr "aeiou" "_"
```

#### 2. معالجة JSON والبيانات

```bash
# استخراج بيانات من JSON
cat data.json | grep -oE '"price"\s*:\s*[0-9]*\.?[0-9]*'

# تحليل بيانات من API
curl -s https://api.coindesk.com/v1/bpi/currentprice/BTC.json | \
grep -oE '"rate":"[0-9.,]+"'
```

### الخصائص المتقدمة في Shell

#### 1. Metacharacters - الرموز الخاصة

| الرمز | الوظيفة |
|-------|----------|
| `#` | تعليق |
| `;` | فصل الأوامر |
| `*` | أي عدد من الأحرف |
| `?` | حرف واحد |

```bash
# تنفيذ أوامر متعددة
echo "Hello"; echo "World"

# البحث بـ wildcards
ls *.txt
ls file?.sh
```

#### 2. Quoting - الاقتباسات

```bash
name="Ahmed"
echo "Hello $name"      # يفسر المتغير: Hello Ahmed
echo 'Hello $name'      # حرفي: Hello $name
echo \$5                # escape: $5
```

#### 3. I/O Redirection - إعادة التوجيه

```bash
# توجيه المخرجات
ls > files.txt          # كتابة جديدة
ls >> files.txt         # إضافة
ls 2> errors.txt        # أخطاء فقط
ls > output.txt 2>&1    # مخرجات وأخطاء معاً

# استخدام ملف كمدخل
sort < data.txt
```

#### 4. Command Substitution - استبدال الأوامر

```bash
# حفظ ناتج أمر في متغير
current_date=$(date)
current_dir=`pwd`

echo "Today is $current_date"
echo "Working in $current_dir"
```

### المفاهيم البرمجية المتقدمة

#### 1. العمليات الحسابية

```bash
# العمليات الأساسية
a=10
b=5
sum=$((a + b))          # 15
diff=$((a - b))         # 5
product=$((a * b))      # 50
quotient=$((a / b))     # 2
remainder=$((a % b))    # 0

echo "النتائج: $sum, $diff, $product, $quotient, $remainder"
```

#### 2. الشروط المتقدمة

```bash
# شروط مركبة
if [ $age -ge 18 ] && [ $age -le 65 ]; then
    echo "في سن العمل"
elif [ $age -lt 18 ]; then
    echo "قاصر"
else
    echo "متقاعد"
fi

# فحص متعدد الخيارات
case $choice in
    1) echo "الخيار الأول" ;;
    2) echo "الخيار الثاني" ;;
    *) echo "خيار غير صحيح" ;;
esac
```

#### 3. المصفوفات (Arrays)

```bash
# تعريف مصفوفة
fruits=("تفاح" "برتقال" "موز" "عنب")
numbers=(1 2 3 4 5)

# الوصول للعناصر
echo ${fruits[0]}       # أول عنصر
echo ${fruits[@]}       # جميع العناصر
echo ${#fruits[@]}      # عدد العناصر

# التكرار عبر المصفوفة
for fruit in "${fruits[@]}"; do
    echo "الفاكهة: $fruit"
done

# التكرار بالفهرس
for i in "${!fruits[@]}"; do
    echo "الفهرس $i: ${fruits[$i]}"
done
```

#### 4. الحلقات المتقدمة

```bash
# حلقة for بـ C-style
for ((i=1; i<=10; i++)); do
    echo "العدد: $i"
done

# حلقة while
counter=1
while [ $counter -le 5 ]; do
    echo "التكرار: $counter"
    counter=$((counter + 1))
done

# حلقة until
num=1
until [ $num -gt 5 ]; do
    echo "الرقم: $num"
    num=$((num + 1))
done
```

## ⏰ جدولة المهام مع Cron

### مقدمة عن Cron

**Cron** هو خدمة نظام لتشغيل المهام المجدولة تلقائياً.

#### المكونات:
- **cron**: الأداة العامة
- **crond**: الخدمة التي تعمل بالخلفية  
- **crontab**: ملف جدولة المهام

### صيغة Crontab

```
* * * * * command
│ │ │ │ │
│ │ │ │ └── يوم الأسبوع (0-7) (الأحد = 0 أو 7)
│ │ │ └──── الشهر (1-12)
│ │ └────── يوم الشهر (1-31)
│ └──────── الساعة (0-23)
└────────── الدقيقة (0-59)
```

### إدارة Crontab

```bash
# عرض المهام الحالية
crontab -l

# تعديل المهام
crontab -e

# حذف جميع المهام (احذر!)
crontab -r
```

### أمثلة عملية على Cron

#### 1. مهام يومية

```bash
# كل يوم الساعة 2 صباحاً
0 2 * * * /home/user/backup.sh

# كل يوم الساعة 9 مساءً
0 21 * * * echo "Welcome to cron" >> /tmp/echo.txt
```

#### 2. مهام أسبوعية

```bash
# كل أحد الساعة 3:30 مساءً
30 15 * * 0 /home/user/weekly_report.sh

# كل جمعة منتصف الليل
0 0 * * 5 /home/user/cleanup.sh
```

#### 3. مهام شهرية

```bash
# أول يوم في الشهر الساعة 1 صباحاً
0 1 1 * * /home/user/monthly_backup.sh
```

### سكربت النسخ الاحتياطي التلقائي

```bash
#!/bin/bash
# daily_backup.sh - نسخة احتياطية يومية

# الإعدادات
SOURCE_DIR="$HOME/Documents"
BACKUP_DIR="$HOME/backups"
DATE=$(date +%Y%m%d_%H%M%S)
LOG_FILE="$HOME/backup.log"

# دالة للكتابة في السجل
log_message() {
    echo "$(date '+%Y-%m-%d %H:%M:%S'): $1" >> "$LOG_FILE"
}

# إنشاء مجلد النسخ الاحتياطية
mkdir -p "$BACKUP_DIR"

# بدء النسخ الاحتياطي
log_message "بدء النسخ الاحتياطي"

if [ -d "$SOURCE_DIR" ]; then
    BACKUP_FILE="$BACKUP_DIR/documents_backup_$DATE.tar.gz"
    
    # إنشاء الأرشيف
    tar -czf "$BACKUP_FILE" -C "$HOME" Documents/ 2>/dev/null
    
    if [ $? -eq 0 ]; then
        SIZE=$(du -sh "$BACKUP_FILE" | cut -f1)
        log_message "نجح النسخ الاحتياطي - الحجم: $SIZE"
        echo "✅ تم إنشاء النسخة الاحتياطية: $BACKUP_FILE"
        
        # حذف النسخ الأقدم من أسبوع
        find "$BACKUP_DIR" -name "documents_backup_*.tar.gz" -mtime +7 -delete
        log_message "تم حذف النسخ القديمة"
    else
        log_message "فشل النسخ الاحتياطي"
        echo "❌ فشل في إنشاء النسخة الاحتياطية"
        exit 1
    fi
else
    log_message "المجلد المصدر غير موجود: $SOURCE_DIR"
    echo "❌ المجلد المصدر غير موجود"
    exit 1
fi
```

#### إضافة السكربت لـ Cron

```bash
# تعديل crontab
crontab -e

# إضافة مهمة يومية الساعة 2 صباحاً
0 2 * * * /home/user/daily_backup.sh >> /home/user/backup_cron.log 2>&1
```

### سكربت مراقبة النظام

```bash
#!/bin/bash
# system_monitor.sh - مراقبة النظام

REPORT_FILE="/tmp/system_report_$(date +%Y%m%d_%H%M%S).txt"

{
    echo "=== تقرير النظام - $(date) ==="
    echo ""
    
    echo "استخدام المعالج:"
    uptime
    echo ""
    
    echo "استخدام الذاكرة:"
    free -h
    echo ""
    
    echo "استخدام القرص:"
    df -h
    echo ""
    
    echo "العمليات النشطة (أكثر 5 استهلاكاً):"
    ps aux --sort=-%cpu | head -6
    echo ""
    
    # تحذيرات
    DISK_USAGE=$(df / | tail -1 | awk '{print $5}' | sed 's/%//')
    if [ $DISK_USAGE -gt 80 ]; then
        echo "⚠️ تحذير: مساحة القرص ممتلئة بنسبة $DISK_USAGE%"
    fi
    
    MEMORY_USAGE=$(free | grep Mem | awk '{printf("%.0f", $3/$2 * 100.0)}')
    if [ $MEMORY_USAGE -gt 80 ]; then
        echo "⚠️ تحذير: استخدام الذاكرة مرتفع: $MEMORY_USAGE%"
    fi
    
} > "$REPORT_FILE"

echo "تم إنشاء التقرير: $REPORT_FILE"
```

## 💻 مشاريع متقدمة

### مشروع: حاسبة المتوسط التفاعلية

```bash
#!/bin/bash
# average_calculator.sh - حاسبة متوسط الأعمار

echo "🧮 حاسبة متوسط الأعمار"
echo "======================"

# مصفوفة لتخزين الأعمار
ages=()

# قراءة عدد المستخدمين
while true; do
    read -p "كم عدد الأشخاص؟ " count
    if [[ $count =~ ^[0-9]+$ ]] && [ $count -gt 0 ]; then
        break
    else
        echo "❌ يجب إدخال رقم صحيح أكبر من صفر"
    fi
done

# قراءة الأعمار
for ((i=1; i<=count; i++)); do
    while true; do
        read -p "عمر الشخص رقم $i: " age
        if [[ $age =~ ^[0-9]+$ ]] && [ $age -gt 0 ] && [ $age -le 120 ]; then
            ages+=($age)
            break
        else
            echo "❌ يجب إدخال عمر صحيح (1-120)"
        fi
    done
done

# حساب المجموع والمتوسط
sum=0
for age in "${ages[@]}"; do
    sum=$((sum + age))
done

average=$((sum / count))

# عرض النتائج
echo ""
echo "📊 النتائج:"
echo "============"
echo "عدد الأشخاص: $count"
echo "مجموع الأعمار: $sum سنة"
echo "متوسط العمر: $average سنة"

# تصنيف الفئة العمرية
if [ $average -le 12 ]; then
    category="أطفال"
elif [ $average -le 19 ]; then
    category="مراهقون"
elif [ $average -le 59 ]; then
    category="بالغون"
else
    category="كبار السن"
fi

echo "الفئة العمرية: $category"

# إحصائيات إضافية
min_age=${ages[0]}
max_age=${ages[0]}

for age in "${ages[@]}"; do
    if [ $age -lt $min_age ]; then
        min_age=$age
    fi
    if [ $age -gt $max_age ]; then
        max_age=$age
    fi
done

echo ""
echo "📈 إحصائيات إضافية:"
echo "أصغر عمر: $min_age سنة"
echo "أكبر عمر: $max_age سنة"
echo "المدى العمري: $((max_age - min_age)) سنة"
```

### مشروع: مدير الملفات المتقدم

```bash
#!/bin/bash
# advanced_file_manager.sh - مدير ملفات متقدم

LOG_FILE="$HOME/file_manager.log"

# دالة للكتابة في السجل
log_action() {
    echo "$(date '+%Y-%m-%d %H:%M:%S'): $1" >> "$LOG_FILE"
}

# دالة عرض الاستخدام
show_usage() {
    echo "الاستخدام: $0 [options]"
    echo "Options:"
    echo "  -l, --list      عرض الملفات"
    echo "  -c, --create    إنشاء ملف"
    echo "  -d, --delete    حذف ملف"
    echo "  -s, --search    البحث عن ملف"
    echo "  -b, --backup    نسخة احتياطية"
    echo "  -h, --help      عرض المساعدة"
}

# دالة عرض الملفات مع التفاصيل
list_files() {
    echo "📁 الملفات في المجلد الحالي:"
    echo "================================"
    
    total_files=0
    total_size=0
    
    for file in *; do
        if [ -f "$file" ]; then
            size=$(du -h "$file" | cut -f1)
            perms=$(ls -l "$file" | awk '{print $1}')
            date=$(ls -l "$file" | awk '{print $6, $7, $8}')
            
            echo "📄 $file | $size | $perms | $date"
            total_files=$((total_files + 1))
        elif [ -d "$file" ]; then
            echo "📁 $file/ | مجلد"
        fi
    done
    
    echo "================================"
    echo "إجمالي الملفات: $total_files"
    log_action "تم عرض $total_files ملف"
}

# دالة إنشاء ملف مع محتوى
create_file() {
    read -p "اسم الملف الجديد: " filename
    
    if [ -z "$filename" ]; then
        echo "❌ يجب إدخال اسم الملف"
        return 1
    fi
    
    if [ -f "$filename" ]; then
        read -p "⚠️ الملف موجود. استبدال؟ (y/n): " replace
        if [ "$replace" != "y" ] && [ "$replace" != "Y" ]; then
            echo "تم إلغاء العملية"
            return 1
        fi
    fi
    
    echo "أدخل محتوى الملف (اضغط Ctrl+D للإنهاء):"
    cat > "$filename"
    
    if [ $? -eq 0 ]; then
        echo "✅ تم إنشاء الملف: $filename"
        log_action "تم إنشاء ملف: $filename"
    else
        echo "❌ فشل في إنشاء الملف"
        log_action "فشل في إنشاء ملف: $filename"
    fi
}

# دالة حذف ملف آمن
delete_file() {
    read -p "اسم الملف للحذف: " filename
    
    if [ ! -f "$filename" ]; then
        echo "❌ الملف غير موجود: $filename"
        return 1
    fi
    
    # عرض معلومات الملف
    echo "معلومات الملف:"
    ls -lh "$filename"
    
    read -p "هل أنت متأكد من حذف '$filename'؟ (yes/no): " confirm
    
    if [ "$confirm" = "yes" ]; then
        # نسخة احتياطية قبل الحذف
        backup_dir="$HOME/.deleted_files"
        mkdir -p "$backup_dir"
        cp "$filename" "$backup_dir/$(basename "$filename").$(date +%Y%m%d_%H%M%S).bak"
        
        rm "$filename"
        echo "✅ تم حذف الملف: $filename"
        echo "💾 نسخة احتياطية محفوظة في: $backup_dir"
        log_action "تم حذف ملف: $filename"
    else
        echo "تم إلغاء العملية"
    fi
}

# دالة البحث المتقدم
search_files() {
    read -p "نمط البحث (اسم الملف): " pattern
    
    if [ -z "$pattern" ]; then
        echo "❌ يجب إدخال نمط البحث"
        return 1
    fi
    
    echo "🔍 البحث عن: $pattern"
    echo "========================"
    
    # البحث في المجلد الحالي
    found_files=$(find . -name "*$pattern*" -type f 2>/dev/null)
    found_dirs=$(find . -name "*$pattern*" -type d 2>/dev/null)
    
    if [ ! -z "$found_files" ]; then
        echo "📄 ملفات موجودة:"
        echo "$found_files" | while read file; do
            size=$(du -h "$file" 2>/dev/null | cut -f1)
            echo "  $file ($size)"
        done
    fi
    
    if [ ! -z "$found_dirs" ]; then
        echo "📁 مجلدات موجودة:"
        echo "$found_dirs"
    fi
    
    if [ -z "$found_files" ] && [ -z "$found_dirs" ]; then
        echo "❌ لم يتم العثور على نتائج"
    fi
    
    log_action "بحث عن: $pattern"
}

# معالجة المعاملات
case "$1" in
    -l|--list)
        list_files
        ;;
    -c|--create)
        create_file
        ;;
    -d|--delete)
        delete_file
        ;;
    -s|--search)
        search_files
        ;;
    -h|--help)
        show_usage
        ;;
    "")
        # وضع تفاعلي
        while true; do
            echo ""
            echo "🗂️ مدير الملفات المتقدم"
            echo "======================="
            echo "1) عرض الملفات"
            echo "2) إنشاء ملف"
            echo "3) حذف ملف"
            echo "4) البحث"
            echo "5) عرض السجل"
            echo "6) خروج"
            echo ""
            
            read -p "اختيارك (1-6): " choice
            
            case $choice in
                1) list_files ;;
                2) create_file ;;
                3) delete_file ;;
                4) search_files ;;
                5) 
                    if [ -f "$LOG_FILE" ]; then
                        echo "📜 آخر 10 عمليات:"
                        tail -10 "$LOG_FILE"
                    else
                        echo "لا يوجد سجل متاح"
                    fi
                    ;;
                6) 
                    echo "👋 شكراً لاستخدام مدير الملفات!"
                    log_action "إنهاء البرنامج"
                    exit 0
                    ;;
                *) echo "❌ اختيار غير صحيح" ;;
            esac
        done
        ;;
    *)
        echo "❌ خيار غير معروف: $1"
        show_usage
        exit 1
        ;;
esac
```

## 🔗 الخطوات التالية

بعد إتقان البرمجة النصية المتقدمة:

1. **الدوال والوحدات** (functions and modules)
2. **معالجة إشارات النظام** (signal handling)
3. **البرمجة المتوازية** (parallel processing)
4. **تطوير أدوات CLI** احترافية
5. **التكامل مع قواعد البيانات**
6. **إدارة الخدمات والعمليات**

---

**📜 تذكر**: البرمجة النصية المتقدمة تفتح لك آفاق لا محدودة في أتمتة وإدارة أنظمة Linux. استمر في التطبيق والتطوير!
