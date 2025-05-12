# linux-toturial

<div dir="rtl">

# دستورات `pwd` و `cd`

## دایرکتوری چیست؟

دایرکتوری (Directory) یک پوشه است که حاوی لیستی از فایل‌ها و/یا دایرکتوری‌های دیگر است. این فایل‌ها ممکن است عکس، فیلم، متن و یا حتی دایرکتوری دیگری باشند. در واقع دایرکتوری یک ساختار برای سازمان‌دهی فایل‌ها در کامپیوتر است.

</div>

```
Project
├── GitLab.jpg
├── Intro.txt
├── Linux
│   ├── Manjaro
│   └── Ubuntu.png
└── video.mp4

3 directories, 4 files
```
<div dir="rtl">

**توضیحات :**

* `.` شاخص دایرکتوری فعلی (Current Directory)
* `..` شاخص دایرکتوری سطح بالاتر (Parent Directory)
* Subdirectoryها زیرشاخه‌های دایرکتوری محسوب می‌شوند.

## دستور `pwd`

این دستور (Print Working Directory) مسیر کامل دایرکتوری فعلی را نمایش می‌دهد:

</div>

```terminal
user@Machine:~$ pwd
/home/user
user@Machine:~$
```
<div dir="rtl">

## دستور `cd`

این دستور (Change Directory) برای جابجایی بین دایرکتوری‌های مختلف استفاده می‌شود:

### ۱. وارد کردن آدرس مقصد بصورت کامل

آدرس کامل (Absolute Path) همیشه از ریشه (`/`) شروع می‌شود:

</div>

```terminal
user@Machine:~$ cd /home/USERNAME/Desktop
```

<div dir="rtl">

### ۲. آدرس نسبی (Relative Path)

مسیر نسبی نسبت به دایرکتوری فعلی تعیین می‌شود. برای مثال اگر در `/home/user` باشید:

</div>

```terminal
# وارد پوشه Desktop درون دایرکتوری فعلی
user@Machine:~$ cd Desktop
user@Machine:~/Desktop$
```

<div dir="rtl">

### ۳. بازگشت به دایرکتوری سطح بالاتر

با استفاده از `..` می‌توان به دایرکتوری مادر (Parent) بازگشت:

</div>

```terminal
user@Machine:~/Desktop$ cd ..
user@Machine:~$
```
<div dir="rtl">

### ۴. رفتن به دایرکتوری خانه کاربر

استفاده از `cd` بدون آرگومان یا `cd ~` کاربر را به پوشه خانگی‌اش برمی‌گرداند:

</div>

```terminal
user@Machine:~/Downloads$ cd
user@Machine:~$
```
<div dir="rtl">

### ۵. استفاده از `-` برای بازگشت به دایرکتوری قبلی

</div>

```terminal
user@Machine:~/Projects$ cd ~/Downloads
user@Machine:~/Downloads$ cd -
/home/user/Projects
user@Machine:~/Projects$
```


<div dir="rtl">

# دستور `ls`

این دستور برای مشاهدهٔ محتویات فایل‌ها و دایرکتوری‌ها در لینوکس استفاده می‌شود. در صورت استفاده از این دستور در بخش فرمان (Terminal)، نام فایل‌ها و دایرکتوری‌های موجود در دایرکتوری فعلی نمایش پیدا می‌کنند.

## مثال

</div>

```terminal
user@machine:~/ls-commands$ ls
linux.jpg my_folder photos tasks.txt
```

<div dir="rtl">

## لیست فایل‌ها بر اساس زمان (time) یا حجم (size)

برای مرتب‌سازی فایل‌ها بر اساس تاریخ (time) یا حجم (size) می‌توان از آپشن `-t` یا `-S` استفاده کرد.

### مرتب‌سازی بر اساس زمان (جدیدترین اول)

</div>

```terminal
user@machine:~/ls-commands$ ls -t
linux.jpg  photos  my_folder  tasks.txt
```

<div dir="rtl">

### مرتب‌سازی بر اساس حجم (بزرگ‌ترین اول)

</div>

```terminal
user@machine:~/ls-commands$ ls -S
linux.jpg  photos  my_folder  tasks.txt
```

<div dir="rtl">

## نمایش جزئیات (Long Listing)

آپشن `-l`:

</div>

```terminal
user@machine:~/ls-commands$ ls -l
total 200
drwxrwxr-x 2 user user  4096 Aug 10 10:54 linux.jpg
drwxr-xr-x 4 user user  4096 Aug 10 11:03 my_folder
-rw-r--r-- 1 user user  4096 Aug 10 15:09 tasks.txt
```

<div dir="rtl">

**توضیحات خروجی:**

* ستون اول نوع فایل و مجوزها (Permission).
* ستون دوم تعداد لینک‌های سخت (Hard Links).
* ستون سوم و چهارم مالک (Owner) و گروه (Group).
* ستون پنجم حجم فایل به بایت.
* ستون ششم تاریخ و زمان آخرین تغییرات (Modification Time).
* ستون هفتم نام فایل یا دایرکتوری.

## نمایش فایل جدید در یک مسیر دلخواه

برای ایجاد فایل جدید و مشاهدهٔ محتویات آن:

</div>


```bash
# ساخت فایل جدید
> echo "Hello World" > /tmp/new_hello
# نمایش دستور ls برای مسیر جدید
user@machine:~/ls-commands$ ls -l /tmp/new_hello
-rw-r--r-- 1 user user   12 Aug 10 15:09 /tmp/new_hello
# نمایش محتوای فایل
user@machine:~/ls-commands$ cat /tmp/new_hello
Hello World
```

<div dir="rtl">

ستون سوم و چهارم مالک و گروه فایل هستند.

نکته: اگر حجم فایل در صفر کیلوبایت باشد، نشان‌دهندهٔ خالی بودن فایل است. همچنین زمان آخرین تغییر در دایرکتوری مربوطه نیاز به دقت دارد زیرا زمان آخرین تغییر در دایرکتوری به معنی اضافه/حذف فایل‌ها است.

## استفاده از آپشن‌ها به همراه نام دایرکتوری

</div>

```terminal
user@machine:~/ls-commands$ ls -a
.  ..  linux.jpg  my_folder  photos  tasks.txt
```

<div dir="rtl">

مشاهدهٔ همهٔ فایل‌ها شامل فایل‌های مخفی (`.` و `..`) و دیگر فایل‌ها.

</div>

```terminal
user@machine:~/ls-commands$ cd ..
user@machine:~/another-directory$ ls -l
# خروجی مشابه با قبل، فقط در دایرکتوری دیگر نمایش داده می‌شود.
```

<div dir="rtl">

## مشاهدهٔ فقط فایل‌ها یا دایرکتوری‌ها

* آپشن `-d`: فقط دایرکتوری‌ها را نمایش دهد.
* آپشن `-F`: در انتهای نام دایرکتوری‌ها `/` اضافه می‌کند.

</div>

```terminal
user@machine:~/ls-commands$ ls -F
linux.jpg  my_folder/  photos/  tasks.txt
```

<div dir="rtl">

## ترکیب چند آپشن در یک دستور

می‌توان چند آپشن را به صورت ترکیبی استفاده کرد. معمولاً ابتدا `-l` و پس از آن سایر آپشن‌ها می‌آیند. ترتیب آپشن‌ها تأثیری در خروجی ندارد.

</div>

```terminal
user@machine:~/ls-commands$ ls -ltr
total 200
drwxr-xr-x 4 user user  4096 Aug 10 11:03 my_folder
-rw-r--r-- 1 user user  4096 Aug 10 15:09 tasks.txt
-rw-r--r-- 1 user user  18041 Aug 10 10:54 linux.jpg
```

<div dir="rtl">

### توضیح آپشن‌ها در ترکیب:

* `-l`: نمایش جزئیات.
* `-t`: مرتب‌سازی بر اساس زمان آخرین تغییر.
* `-r`: معکوس کردن ترتیب (قدیمی‌ترین اول).
* `-h`: خواناتر کردن حجم فایل به کیلوبایت/مگابایت.

</div>



```terminal
user@machine:~/ls-commands$ ls -lh
total 200K
-rw-r--r-- 1 user user  4.0K Aug 10 15:09 tasks.txt
-rw-r--r-- 1 user user 12K   Aug 10 10:54 linux.jpg
drwxr-xr-x 4 user user  4.0K Aug 10 11:03 my_folder
```


<div dir="rtl">

> با ترکیب آپشن‌های `-l`, `-h`, `-t`, و `-r` می‌توانید خروجی مناسبی از دستور `ls` داشته باشید که به صورت خوانا و مرتب شده نمایش داده می‌شود.

</div>


## خلاصه دستورات

| دستور       | عملکرد                                        | مثال                                            |
|-------------|-----------------------------------------------|-------------------------------------------------|
| `pwd`       | نمایش مسیر کامل دایرکتوری جاری               | `$ pwd` → `/home/querа`                         |
| `cd /مسیر`  | جابجایی به دایرکتوری با مسیر مطلق            | `$ cd /home/querа/Desktop`                      |
| `cd نام_پوشه` | جابجایی به زیرپوشه (مسیریابی نسبی)           | `$ cd Desktop`                                  |
| `cd ..`     | رفتن به دایرکتوری والد (یک سطح بالاتر)       | `$ cd ..`                                       |
| `cd`        | بازگشت به پوشهٔ خانه (`~`)                    | `$ cd` → `/home/querа`                          |
| `cd -`      | بازگشت به دایرکتوری قبلی                     | `$ cd -`                                        |




| دستور     | عملکرد                                      | مثال واضح‌تر                                                           |
| --------- | ------------------------------------------- | ---------------------------------------------------------------------- |
| `ls`      | نمایش فایل‌ها و پوشه‌های دایرکتوری جاری     | `$ ls` → `linux.jpg  task.txt`                                         |
| `ls -t`   | مرتب‌سازی بر اساس زمان آخرین تغییر          | `$ ls -t` → `task.txt  linux.jpg`                                      |
| `ls -l`   | نمایش اطلاعات کامل فایل‌ها                  | `$ ls -l` → `-rw-r--r-- 1 user user  1054 Aug 10 10:52 task.txt`     |
| `ls -lt`  | اطلاعات کامل + مرتب‌سازی زمانی              | `$ ls -lt` → (task.txt اول، بعد linux.jpg با جزئیات)                   |
| `ls -a`   | نمایش فایل‌های مخفی                         | `$ ls -a` → `.  ..  .hidden_file  linux.jpg`                           |
| `ls -la`  | فایل‌های مخفی + اطلاعات کامل                | `$ ls -la` → `-rw-r--r-- 1 user user 1024 Aug 10 10:52 .hidden_file` |
| `ls -lS`  | مرتب‌سازی بر اساس اندازه فایل (بزرگ‌تر اول) | `$ ls -lS` → (بزرگ‌ترین فایل در خط اول)                                |
| `ls -ltr` | نمایش کامل + مرتب‌سازی زمانی معکوس          | `$ ls -ltr` → (قدیمی‌ترین فایل اول، جدیدترین آخر)                      |
| `ls -lh`  | نمایش اندازه‌ها به‌صورت خوانا               | `$ ls -lh` → `1.1K task.txt  512K linux.jpg`                           |
| `ls -lth` | ترکیب اطلاعات کامل، خوانایی اندازه، و زمان  | `$ ls -lth` → (همه‌ی اطلاعات با حجم قابل خواندن و زمان مرتب)           |


