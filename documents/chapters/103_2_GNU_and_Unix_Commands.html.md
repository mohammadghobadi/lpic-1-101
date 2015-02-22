---
layout: article
chapter: دستورات گنو و یونیکس
order: 7.2
title: پردازش جریان‌های داده باکمک فیلتر ها
---
**دستوراتی برای ادغام فایل‌ها**


بعضی وقتا ما نیاز داریم تا چند تا فایل را با هم ادغام کنیم



<div align="left" dir="ltr">**cat**</div>


این دستور خوب برای فایل‌هایی با مقدار نوشته کم بسیار کارا است که به فرم زیر استفاده می شود.

<pre>
cat [option] file1 file2 ... > file.natije
</pre>

اول یه مثال با هم ببینیم :


file1:
<pre>
Hello
</pre>
file2:
<pre>
  
   how are you
</pre>
file3:
<pre>



thanks very much.
</pre>


تمام مثال های این بخش با همین سه تا فایل خواهد بود.

دستور و نتیجه ما در خط فرمان به شرح زیر است :


<pre>
$ cat file1 file2 file3
Hello
  
   how are you



thanks very much
</pre>


همون طور که می بینید file1 را چاپ کرده ، به خط بعدی رفته و بعد file2 را چاپ می کند و به همین منوال file3.

هیچ چیزی مانند چند فاصله پشت سر هم یا خط‌های بدون نوشته حذف نمی شوند.

(من در اینجا از file.natije< استفاده نکردم تا نتیجه کد در خط فرمان نمایش داده شود ولی اگر به فرم


<pre>
 $ cat file1 file2 file3 > file.natije
</pre>


می نوشتم چیزی در خط فرمان نمایش داده نمی شد و به جای آن فایلی به نام file.natije ساخته شده و حاصل در آن ذخیره می شد)
 حال چند تا از 	option های مهم را با هم بررسی می کنیم

<pre>
1) -E یا --show-ends
</pre>

این option انتهای هر خط را (با کاراکتر $) مشخص می کند:
<pre>
$ cat -E file1 file2 file3
Hello$
  $
   how are you$
$
$
$
thanks very much$
</pre>

<pre>
2)-n یا --number
</pre>

خطوط را شماره گذاری‌ می‌کند.

<pre>
$ cat -n file1 file2 file3

     1	Hello
     2	  
     3	   how are you
     4	
     5	
     6	
     7	thanks very much
</pre>

3) -b یا --number-nonblank


خطوطی که در آن نوشته‌‌ای هست را شماره گذاری می کند.


<pre>
$ cat -b file1 file2 file3
     1	Hello
     2	  
     3	   how are you



     4	thanks very much
</pre>


نکته: همونطور که می بینید در خط ۲ نوشته ای وجود ندارد اما چند تا فاصله خورده. پس فاصله به تنهایی هم نوشته محسوب شده و شماره گذاری می‌شوند.



4) -s یا --squeeze-blank


چند تا خط خالی پشت سر هم را تبدیل به یک خط خالی می کند.


<pre>
$ cat -s file1 file2 file3
Hello
  
   how are you

thanks very much
</pre>

5) -T یا --show-tabsشماره گذاری


6) -v, --show-nonprinting

<div align="left" dir="ltr">**join**</span></div>


<pre>
join [OPTION]... FILE1 FILE2
</pre>

به صورت پیشفرض خط اول فایل اول را با خط اول فایل دوم مقایسه می کند، مشابه ها را یک بار چاپ می کند و نوشته های غیر تکراری فایل اول را چاپ کرده یک فاصله داده و نوشته های غیرتکراری فایل دوم را چاپ می کند. این کار را به ترتیب برای خط های بعدی نیز انجام می دهد.
برای نمونه این ما این دو فایل را داریم :
<pre>
file1 :
555-2397 Mohammad, Mansoory
555-5116 Omid, Golparvar
555-7929 Mohammad, Ghobady
555-9871 Mohammad, Kahfie
</pre>

<pre>
file2 :
555-2397 unlisted
555-5116 listed
555-7929 unlisted
555-9871 listed
</pre>

نتیجه دستور join به شرح زیر است :

<pre>
$ join file1 file2
555-2397 Mohammad, Mansoory unlisted
555-5116 Omid, Golparvar listed
555-7929 Mohammad, Ghobady unlisted
555-9871 Mohammad, Kahfie listed
</pre>

در صورتی که یکی از فایل ها شامل یک خط خالی باشد باز هم عملیات join انجام می شود ولی یک خطا می دهد (تعداد خطاها بستگی به تعداد خط های خالی دارد ولی عملیات ‌join صورت می گیرد). ولی اگر یک خط اضافی با محتوای متفاوت نیز وجود داشته باشد عملیات join صورت نمی گیرد و خطا می دهد حتی اگر چند خط اول هم با هم یکی باشند به هیچ عنوان عملیات join صورت نگرفته و خطا می دهد.

<div align="left" dir="ltr">**paste**</span></div>

<pre>
paste [OPTION]... [FILE]...
</pre>

خط اول فایل اول را چاپ کرده سپس از یک tab برای جداسازی استفاده می کند و خط اول فایل دوم را چاپ می کند و به همین صورت ادامه می دهد (پایان خط هر فایل را به طور پیشفرض enter مشخص می کند). سپس به خط دوم رفته و این کار را برای خط های بعدی انجام می هد.

file1 :

<pre>
555-2397 Mohammad, Mansoory
555-5116 Omid, Golparvar
555-7929 Mohammad, Ghobady
555-9871 Mohammad, Kahfie
</pre>

file2 :

<pre>
555-2397 unlisted
555-5116 listed
555-7929 unlisted
555-9871 listed
</pre>

و نتیجه عملیات :
<pre>
555-2397 Mohammad, Mansoory	555-2397 unlisted
555-5116 Omid, Golparvar	555-5116 listed
555-7929 Mohammad, Ghobady	555-7929 unlisted
555-9871 Mohammad, Kahfie	555-9871 listed
</pre>

دستورات تبدیل محتوای متن

بعضی وقت ها نیاز داریم که در محتوای متن، تبدیل هایی را انجام دهیم، مانند تبدیل tab های داخل متن به فاصله یا بالعکس.

<div align="left" dir="ltr">**expand**</span></div>

<pre>
expand [OPTION]... [FILE]...
</pre>

وظیفه تبدیل tab های داخل متن به فاصله را بر عهده دارد.

حال یک option مهم این دستور را با هم بررسی می کنیم


1) -t num یا --tabs=num


به طور پیشفرض tab شامل هشت کاراکتر فاصله است اما شما می توانید با قرار دادن عدد مورد نظرتون به جای num در فرم بالا این تعداد را تغییر دهید

<div align="left" dir="ltr">**unexpand**</span></div>

<pre>
unexpand [OPTION]... [FILE]...
</pre>

وظیفه تبدیل فاصله های داخل متن به tab را بر عهده دارد.

حال یک option مهم این دستور را با هم بررسی می کنیم

1) -t num یا --tabs=num

به طور پیشفرض tab شامل هشت کاراکتر فاصله است اما شما می توانید با قرار دادن عدد مورد نظرتون به جای num در فرم بالا این تعداد را تغییر دهید


<div align="left" dir="ltr">**od**</span></div>

<pre>
od [OPTION]... [FILE]...
</pre>

فایل‌های شما را به مبنای 8 می‌برد ( تعداد فایل ها مهم نیست و نتیجه تمام فایل ها پشت سر هم چاپ می‌شود ) 

file1:

<pre>
1
2
3
4
5
6
7
8
9
10
11
12
13
14
15
16
17
18
19
20
</pre>

در نتیجه می بینیم :

<pre>
$ od file1
0000000 005061 005062 005063 005064 005065 005066 005067 005070
0000020 005071 030061 030412 005061 031061 030412 005063 032061
0000040 030412 005065 033061 030412 005067 034061 030412 005071
0000060 030062 000012
0000063
</pre>

<div align="left" dir="ltr">**sort**</span></div>

<pre>
sort [OPTION]... [FILE]...
</pre>

وظیفه مرتب کردن خط های فایل ها را به صورت صعودی و به کمک کد اسکی به عهده دارد.

file1:

<pre>
555-2397 Mohammad, Mansoory
555-5116 Omid, Golparvar
555-7929 Mohammad, Ghobady
555-9871 Mohammad, Kahfie
</pre>

file2:

<pre>
555-2397 unlisted
555-5116 listed
555-7929 unlisted
555-9871 listed
</pre>

زمانی که دستور زیر را اجرا می‌کنیم

<pre>
$ sort file1 file2
</pre>

ابتدا سیستم دو فایل را یکی می‌کند، به صورت زیر :

<pre>
555-2397 Mohammad, Mansoory
555-5116 Omid, Golparvar
555-7929 Mohammad, Ghobady
555-9871 Mohammad, Kahfie
555-2397 unlisted
555-5116 listed
555-7929 unlisted
555-9871 listed
</pre>

و سپس آن را مرتب می‌کند و به صورت زیر نمایش می دهد :

<pre>
555-2397 Mohammad, Mansoory
555-2397 unlisted
555-5116 listed
555-5116 Omid, Golparvar
555-7929 Mohammad, Ghobady
555-7929 unlisted
555-9871 listed
555-9871 Mohammad, Kahfie
</pre>
حال چند تا از 	option های مهم را با هم بررسی می کنیم


1) -f یا --ignore-case

کد اسکی حروف کوچک و بزرگ را یکی در نظر می گیرد (مثلا کد اسکی A و a را یکی در نظر می‌گیرد)


2) -M یا --month-sort

مقایسه بر اساس ماه‌های سال و صورت زیر صورت می‌گیرد

هر چیزی <'JAN'<...<'DEC'


3) -n یا --numeric-sort

بذارید روی مثال توضیح بدم

file1:

<pre>
1
2
3
4
5
6
7
8
9
10
11
12
13
14
15
16
17
18
19
20
</pre>

اگر به صورت عادی مرتب سازی را انجام دهیم حاصل به صورت زیر می باشد :

<pre>
$ sort file1
1
10
11
12
13
14
15
16
17
18
19
2
20
3
4
5
6
7
8
9
</pre>

همانطور که ملاحظه می کنید اول اعدادی که رقم اول سمت چپشان عدد ۱ است چاپ می شود.

حال برای اینکه به ترتیب عددی مرتب کنیم از option -n استفاده می‌کنیم و حاصل به شرح زیر است :

<pre>
$ sort -n file1
1
2
3
4
5
6
7
8
9
10
11
12
13
14
15
16
17
18
19
20
</pre>

نکته: البته اگر در فایل ، خطی شامل حروف باشد در مرتب سازی اول آنها قرار داده می شوند بعد سراغ اعداد می رویم

به عنوان نمونه :


file1:

<pre>
a1
2
3
4s
4
5
6
7
8
9
10
11
12
13
as14
15
c16
17
18
19
20
</pre>

و در نتیجه :

<pre>
$ sort -n file1
a1
as14
c16
2
3
4
4s
5
6
7
8
9
10
11
12
13
15
17
18
19
20
</pre>


4) -r یا --reverse

برعکس و یه صورت نزولی مرتب می‌کند

file1:

<pre>
555-2397 Mohammad, Mansoory
555-5116 Omid, Golparvar
555-7929 Mohammad, Ghobady
555-9871 Mohammad, Kahfie
</pre>
و در نتیجه :

<pre>
$ sort -r file1
555-9871 Mohammad, Kahfie
555-7929 Mohammad, Ghobady
555-5116 Omid, Golparvar
555-2397 Mohammad, Mansoory
</pre>


5) -k field یا --key=field

اگر بخواهیم مثلا بر اساس ستون دوم فایل مرتب سازی صورت پذیرد باید به جای field عدد ۲ را جایگزین کنیم

file1:

<pre>
555-2397 Mohammad, Mansoory
555-5116 Omid, Golparvar
555-7929 Mohammad, Ghobady
555-9871 Mohammad, Kahfie
</pre>

و در نتیجه :

<pre>
$ sort  -k 2 file1
555-7929 Mohammad, Ghobady
555-9871 Mohammad, Kahfie
555-2397 Mohammad, Mansoory
555-5116 Omid, Golparvar
</pre>

<div align="left" dir="ltr">**split**</span></div>

<pre>
split [OPTION]... [INPUT [PREFIX]]
</pre>

فایل ورودی را به چند تکه تقسیم می کند. به طور پیشفرض هر ۱۰۰۰ خط را را تکه می کند.

حال چند تا از 	option های مهم را با هم بررسی می کنیم.

1) -b SIZE یا --bytes=SIZE

بر اساس سایزی که شما به آن می‌دهید تقسیم می‌شود

نکنه: دقت داشته باشید که این کار ممکن است کلمه آخر را دو تکه کرده و نصف آن در آخر فایل اول و نصف دیگر آن در اول فایل دوم قرار دهد و طبیعتا ممکن است به فایل شما صدمه بزند.


2) -C SIZE یا --line-bytes=SIZE

بر اساس سایزی که شما به آن می‌دهید فایل را تقسیم می‌کند با این خصوصیت که تا زمانی که به پایان خط نرسد تقسیم بندی انجام نمی شود.


3) -l NUMBER یا --lines=NUMBER

بر اساس تعداد خطی که به آن می دهیم تقسیم می کند. مثلا شما به جای NUMBER عدد ۵ را قرار می دهید به این ترتیت مثلا فایل ۳۰ خطی شما به ۶ فایل ۵ خطی تقسیم می‌شود.

<div align="left" dir="ltr">**tr**</span></div>

<pre>
tr [OPTION] string1 string2
</pre>


<div align="left" dir="ltr">**uniq**</span></div>


<pre>
uniq [OPTION]... [INPUT [OUTPUT]]
</pre>

اگر در فایل دو یا چند خط پشت سر هم دقیقا یکی باشند همه را پاک کرده و یکی از آنها را باقی می‌گذارد.


file1:

<pre>
hello
 hello
thanks very much
thanks very much
hello
</pre>

و نتیجه دستور :

<pre>
$ uniq file1 
hello
 hello
thanks very much
hello
</pre>

حال اگر دستور را به شکل زیر بنویسیم
<pre>
$ uniq file1 file2
</pre>

دستور روی file1 اجرا شده و نتیجه آن در file2 ذخیره می شود و در خط فرمان چیزی نمایش داده نمی شود.


دستوراتی برای تغییر قالب فایل‌ها


<div><span dir="ltr">**fmt**</span></div>


<pre>
fmt [-WIDTH] [OPTION]... [FILE]...
</pre>

واقعا توضیح دادنش برام خیلی سخت برای همین یه مثال می زنم روی اون توضیح می‌دم.


file1:

<pre>
hello
 hello
 how are you ?



thanks very much
thanks very much
 hello
  vaaaaaaaaaaaaaaaaaaaay
</pre>

حالا دستور را اجرا می‌کنیم

<pre>
$ fmt file1
hello
 hello how are you ?



thanks very much thanks very much
 hello
  vaaaaaaaaaaaaaaaaaaaay
</pre>

۱- خوب همونطور که ملاحظه می‌کنید فاصله بین کلمات و خط های خالی فایل حفظ شده‌اند.

۲- اگر دقت کنید خط های ۲ و ۳ با هم ادغام شده‌اند همینطور خط های ۷و ۸ ولی برای بقیه اتفاقی نیفتاده حالا چرا ؟

اساسا کار دستور fmt ادغام کردن خطوط و قرار دادن در یک خط است. این ادغام تا ۷۵ کاراکتر جلو رفته و بعد از آن به خط بعدی در خروجی رفته و ادغام را دوباره شروع می‌کند.

اما فقط خط‌هایی با هم ادغام می‌شوند که دارای تعداد یکسانی از فاصله های اول خط داشته باشند مثلا اول خط دوم و سوم داری یک فاصله است پس با هم ادغام می‌شوند و یا خطوط هفتم و هشتم که که بدون فاصله آغاز شده و بنابراین با هم ادغام می‌شوند ولی خط‌های نهم و دهم که یکی با یک فاصله و دیگری با دو فاصله آغاز شده‌اند به هیچ عنوان با هم ادغام نمی شوند.
