---
layout: article
chapter: راهنمای استفاده از Docpad
order: 10.1
title: نصب و راه اندازی اولیه
---

### نصب بسته های اولیه
محیط آزمایشی ما سیستم عامل دبیان است. برای نصب بسته های مورد نیاز docpad باید مخازن backports را به سیستم خود اضافه کنید.

````
# echo "deb http://ftp.de.debian.org/debian wheezy-backports main" >> /etc/apt/sources.list
# apt-get update; apt-get install nodejs-legacy
````


#### نصب package manager مربوط به Nodejs
ابتدا package manager مربوط به nodejs را نصب می کنیم و بقیه ابزارهای مورد نیاز را توسط npm نصب خواهیم کرد.

````
npm install -g npm; npm install -g docpad@6.69
npm install -f docpad docpad-plugin-partials docpad-plugin-text
````


#### شروع یک پروژه
برای آنکه یک پروژه جدید را شروع کنید نیاز است که تعدای پوشه و فایل ساخته شود. نیاز نیست آنها را دستی بسازید کافی است دستور زیر بزنید.

<pre>
# mkdir newbook; cd newbook
# docpad init
</pre>

بعد از این دستور فایل‌ها و پوشه های زیر ساخته می شود

````
# ls
docpad.coffee  node_modules  package.json  README.md  src
````

برای شروع کار، باید با پیکربندی docpad.coffee کار را آغاز کنید و بعد مستندات خود را در پوشه src قرار دهید


#### پیکربندی docpad
برای پیکربندی  پروژه کافی است فایل docpad.coffee را به صورت زیر تغییر دهید.

<pre>
docpadConfig = {
        templateData:
                site:  
                        title: "راهنمای مطالعه LPIC-1"
				url: 'http://www.cvak.ir/book/101/'
}

# Export the DocPad Configuration
module.exports = docpadConfig
</pre>

#### تکمیل پروژه
برای ادامه کار لازم است،‌که بخش های مرتبط با صفحه بندی (css) را نیز ویرایش کنید.

نیازی نیست همه کار را از ابتدا انجام دهید، می توانید پروژه ای مشابه را دریافت کنید و محتوای آن را تغییر دهید. برای نمونه همین سایت با ویرایش پروژه [justforfun](http://jadi.net) جادی تهیه شده است. شما نیز می توانید همین کار را بکنید.

### تغییرات اولیه
در صورتی که قصد دارید در ظاهر اولیه، منوها و فوتر سایت تغییر ایجاد کنید به پوشه های src/layouts و src/partials وارد شوید و فایل‌های موجود را ویرایش کنید.
برای اطلاع از نحوه ویرایش و تهیه مستندات به فصل بعد مراجعه کنید.



