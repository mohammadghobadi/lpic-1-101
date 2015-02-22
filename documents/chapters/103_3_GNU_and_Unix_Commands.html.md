---
layout: article
chapter: دستورات گنو و یونیکس
order: 7.3
title: مدیریت فایل‌ها - مقدماتی
---

##فایل‌های پیکر بندی درbash 

می‌دانیم کلیه متغیرهای محلی و alias ها با هر بار خاموش کردن سیستم از بین می‌روند. برای اینکه تغییرات در این متغیرها با هر بار ورود به سیستم تعریف شوند؛آنها را در یکی از فایل‌های پیکربندی bash وارد و ذخیره می‌کنند.

فایل /etc/profile

فایل /etc/bashrc یا /etc/bash.bashrc

فایل ~/.bash.profile بعد از /etc/profile اجرا می‌شود.

فایل ~.bash_login در صورتی که فایل بالا نباشد اجرا می‌شود .

فایل ~/.bashrc


##دستورات اولیه کار با خط فرمان

دستور ls : گرفتن لیستی از پوشه یا فایل
<pre>
  $ ls /home/user
  Desktop      Download    ls    Pictures    Templates
  Documents    Music     Public     Videos
</pre>

دستور touch : ساخت فایل و تغییر زمان

دستور mkdir : ساخت پوشه

دستور rmdir : حذف پوشه خالی 

دستور rm : حذف فایل وپوشه

دستور mv : انتقال فایل و پوشه

دستور cp : کپی کردن فایل و پوشه

دستور cd: تغییر شاخه

دستور pwd : نمایش شاخه جاری




##wildcards یا file globbing 



<table align="center" border="1" style="text-align:center">
<tr> <td> کاراکتر</td> <td> مفهوم </td> </tr>
<tr> <td> * </td> <td> هر تعداد کاراکتر و یا هیچ </td> </tr>
<tr> <td> ? </td> <td> دقیقاً یک کاراکتر </td> </tr>
<tr> <td> [characters] </td> <td> دقیقا یکی از حروف؛ در مجموعه وجود داشته باشد</td> </tr>
<tr> <td> [characters!] </td> <td> دقیقاً یکی از حروف؛ در مجموعه وجود نداشته باشد </td> </tr>
<tr> <td> [a-z] [1-9] </td> <td> یکی از حروف یا اعداد موجود در این رنج؛ در مجموعه وجود داشته باشد </td> </tr>
<tr> <td>[a-z!] [!1-9] </td> <td> یکی از حروف یا اعداد موجود در این رنج؛ در مجموعه وجود نداشته باشد </td> </tr>
<tr> <td>{string1,string2...} </td> <td> یک رشته که در مجموعه باشد </td> </tr>
</table>





مثال:

نمایش لیستی از فایل‌هایی که با کلمه test شروع می‌شوند: 
<pre>

  $ ls test *
</pre>

کپی فایل‌های test1 و test2 و test3 از شاخه جاری به شاخه خانگی:
<pre>
  $ cp test[1-3] /home/lpi
</pre>

کپی فایل test به شاخه خانگی lpi و linux :
<pre>
  $ cp test /home/{lpi,linux}
</pre>

این دستور پیغام خطا می‌دهد:
<pre>
  $ cp: omiting directory 'lpi'
</pre>

زیرا دستور cp تنها یک مسیر (که آخرین مسیر است) را به عنوان مقصد قبول می‌کند و بقیه را به عنوان مبدأ در نظر می‌گیرد.  


 	 
در ادامه به معرفی چند دستور دیگر می‌پردازیم:

دستور gzip : جهت فشرده‌سازی
<pre>
  gzip[options] file1 file2 …
</pre>

این دستور فشرده‌سازی را به صورت مجزا انجام می‌دهد ودر مقابل هر فایل؛ یک فایل با پسوند gz ایجاد کرده و سپس فایل اصلی پاک می‌شود.با گزینه های ۱- و ۹- می‌توان میزان فشرده‌سازی را مشخص کرد.

برای خروج از حالت فشرده می‌توان از گزینه -d استفاده کرد که معادل دستور gunzip است.
<pre>
  $ gzip -9 debian-cd-i386.iso
</pre>

  
دستور bzip2 : جهت فشرده‌سازی 
<pre>
  bzip2[options] file1 file2 …
</pre>

این دستور نیز فشرده‌سازی را به صورت مجزا نجام می‌دهد و در مقابل هر فایل؛ یک فایل با پسوند bz ایجاد کرده و سپس فایل اصلی را پاک می‌کند.که برای جلوگیری از پاک شدن فایل اصلی از گزینه -k استفاده می‌شود.همچنین با گزینه های ۱- تا ۹- می‌توان میزان فشرده‌سازی را مشخص کرد.برای خروج از حالت فشرده‌سازی از گزینه -d استفاده می‌شود.
<pre>
  $ bzip2 -9 debian-cd-i386.iso
</pre>
   
دستور tar : جهت تهیه آرشیو 
<pre>
  tar[options] [archivefile] [file and directories]
</pre>

از این دستور جهت full backup و incremental backup استفاده می‌شود.که از گزینه های زیر می‌توان استفاده کرد:


<table align="center" border="1" style="text-align:center">
<tr> <td> گزینه</td> <td> توضیحات </td> </tr>
<tr> <td> c </td> <td> ساختن آرشیو </td> </tr>
<tr> <td> x </td> <td> باز کردن آرشیو </td> </tr>
<tr> <td> v</td> <td> حالت verbos</td> </tr>
<tr> <td> f </td> <td> معرفی فایل آرشیو </td> </tr>
<tr> <td> p </td> <td>  حفظ permission ها </td> </tr>
<tr> <td>-newer </td> <td> انتخاب فایل جدیدتر از تاریخ داده شده  </td> </tr>
<tr> <td>j </td> <td> فشرده‌سازی با فرمت bz2</td> </tr>
<tr> <td>z </td> <td> فشرده‌سازی با فرمت gunzip یا همان gz
 bz2</td> </tr>
</table>





جهت گرفتن full bachup:
<pre>
  $ sd /home
  $ tar -cvpf lpi_home.tar lpi
</pre>

جهت گرفتن incremental backup :
<pre>
  $ tar –newer “ 2013-02-17 23:59:00” -cvf lpi_home_18.tar lpi
</pre>

جهت فشرده‌سازی آرشیو:
<pre>
  $ tar -cvjpf lpi_home.tar.bz2 lpi
  $ tar -cvzpf lpi_home.tar.gz lpi
</pre>

در مثال اول بعد از تهیه آرشیو؛ فایل به صورت bz2 و در مثال دوم به صورت gz فشرده می‌شود.

جهت باز کردن آرشیو:

در مسیری که می‌خواهیم فایل را از حالت آرشیو خارج کنیم وارد شده و سپس دستورات زیر را استفاده می‌کنیم:
<pre>
  $ tar -xvjpf lpi_home.tar.bz2
  $ tar -xvzpf lpi_home.tar.gz
</pre>



دستور gunzip : جهت خارج کردن از حالت فشرده

می‌توان آرشیو را بدون باز کردن از حالت فشرده خارج کرد:
<pre>
  $ gunzip lpi_home.tar.gz
  $ ls
  lpi_home.tar
</pre>

<pre>
  $ bunzip -d lpi_home.tar.bz2
  $ ls
  lpi_home.tar
</pre>

دستور file : جهت تعیین نوع فایل
<pre>
  file <filename>
</pre>

این دستور نوع فایل را نمایش می‌دهد.که گزینه -z نوع فایل داخل zip را مشخص می‌کند.
<pre>
  $ file filename.gz
  filename.gz: gzip compressed data,was “filename.gz”,from unix,last modified:web feb 22 17:38:11 2013, max compression
</pre>



دستور cpio : جهت تهیه آرشیو
<pre>
  cpio -o > filename.cpio
  cpio -i < ilename.cpio
</pre>

این دستور امکان فشرده‌سازی ندارد وبرای این کار باید از دستورات gzip و bzip2 استفاده کرد.
<pre>
  $ find -name *.txt | cpio -ov > text.cpio
  $ cpio -iduv < text.cpio
</pre>

دستور dd : جهت گزارش خطوط تکراری
<pre>
  dd[options]
</pre>

این دستور جهت کپی کردن فایل استفاده می‌شود.به کمک گزینه bs اندازه بلاک داده که در هر دفعه خوانده می‌شود ؛ با گزینه count تعداد بلاک داده که کپی می‌کند و با گزینه skip تعداد بلاک داده که در ابتدا رد می‌کند ؛ مشخص می‌شود .
<pre>
  $ dd if=/dev/scdo of=dvdname.iso
  $ dd bs=512 count=1 if=/dev/sda of=mbr.img
</pre>
skip

