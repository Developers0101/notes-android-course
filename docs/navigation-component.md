---
layout: default
title: 5- نویگیشن کامپونینت
nav_order: 5
---
# 5- استفاده از navigation component
قسمت 16:

زمانی از navigation component استفاده میکنیم که بخوایم با fragment ها کار کنیم.

` `فرگمنت back نداره.

![My image](https://github.com/Developers0101/notes-android-course/raw/main/images/%D9%86%D9%88%DB%8C%DA%AF%DB%8C%D8%B4%D9%86%20%DA%A9%D8%A7%D9%85%D9%BE%D9%88%D9%86%D9%86%D8%AA_files/image001.png)

![My image](https://github.com/Developers0101/notes-android-course/raw/main/images/%D9%86%D9%88%DB%8C%DA%AF%DB%8C%D8%B4%D9%86%20%DA%A9%D8%A7%D9%85%D9%BE%D9%88%D9%86%D9%86%D8%AA_files/image002.png)

safe args حالتی از navigation component هست که به ما اجازه میده که خیلی راحت اطلاعات رو بین فرگمنت هامون پاس بدیم و در قالب آرگومان هست.

![My image](https://github.com/Developers0101/notes-android-course/raw/main/images/%D9%86%D9%88%DB%8C%DA%AF%DB%8C%D8%B4%D9%86%20%DA%A9%D8%A7%D9%85%D9%BE%D9%88%D9%86%D9%86%D8%AA_files/image003.png)

این دوتا هم navigation رو برای ما میسازن.

وقتی میخوایم از navigation component استفاده کنیم حتماً باید تو پوشه res پوشه navigation بسازیم:

![My image](https://github.com/Developers0101/notes-android-course/raw/main/images/%D9%86%D9%88%DB%8C%DA%AF%DB%8C%D8%B4%D9%86%20%DA%A9%D8%A7%D9%85%D9%BE%D9%88%D9%86%D9%86%D8%AA_files/image004.png)

هم میتونیم از قسمت Resource Manger اینکارو انجام بدیم هم از طریق:

![My image](https://github.com/Developers0101/notes-android-course/raw/main/images/%D9%86%D9%88%DB%8C%DA%AF%DB%8C%D8%B4%D9%86%20%DA%A9%D8%A7%D9%85%D9%BE%D9%88%D9%86%D9%86%D8%AA_files/image005.jpg)

![My image](https://github.com/Developers0101/notes-android-course/raw/main/images/%D9%86%D9%88%DB%8C%DA%AF%DB%8C%D8%B4%D9%86%20%DA%A9%D8%A7%D9%85%D9%BE%D9%88%D9%86%D9%86%D8%AA_files/image006.png)

حتماً باید directory name روی navigation باشه.

![My image](https://github.com/Developers0101/notes-android-course/raw/main/images/%D9%86%D9%88%DB%8C%DA%AF%DB%8C%D8%B4%D9%86%20%DA%A9%D8%A7%D9%85%D9%BE%D9%88%D9%86%D9%86%D8%AA_files/image007.jpg)

حالا اگه روی navigation راست کلیک کنیم new بعد navigation resource file اضافه میشه.

![My image](https://github.com/Developers0101/notes-android-course/raw/main/images/%D9%86%D9%88%DB%8C%DA%AF%DB%8C%D8%B4%D9%86%20%DA%A9%D8%A7%D9%85%D9%BE%D9%88%D9%86%D9%86%D8%AA_files/image008.png)

چون از نوع navigation هست اول اسمش رو nav میزاریم و چون میخوایم تو صفحه main کار کنیم اسمشو nav\_main میزاریم.

قسمت 17

نویگیشن کامپوننت برای اینه که بتونیم با فرگمنت ها کار کنیم و حالت های مختلفی داره مثل bottom navigation که توی اینستاگرام هست و یا چندین فرگمنت در کنار هم که دکمه ی a رو میزنیم به فرگمنت b میره و بعد c و ... .

action پلی ارتباطی بین فرگمنت هاست.

![My image](https://github.com/Developers0101/notes-android-course/raw/main/images/%D9%86%D9%88%DB%8C%DA%AF%DB%8C%D8%B4%D9%86%20%DA%A9%D8%A7%D9%85%D9%BE%D9%88%D9%86%D9%86%D8%AA_files/image009.png)

اینجا آرگومان ها و چیزهای که قرار بین فرگمنت ها ارسال بشه رو مشخص میکنیم.

![My image](https://github.com/Developers0101/notes-android-course/raw/main/images/%D9%86%D9%88%DB%8C%DA%AF%DB%8C%D8%B4%D9%86%20%DA%A9%D8%A7%D9%85%D9%BE%D9%88%D9%86%D9%86%D8%AA_files/image010.png)

برای این قسمت میتونیم حالت انیمیشن برای بستن یا باز کردن فرگمنت ها فعال کنیم.

برای اینکه بتونیم به navigation component فرگمنت اضافه کنیم 2 راه داریم:

یا مستقیماً یه فرگمنت بسازیم یا با new destination یه فرگمنت بسازیم:

![My image](https://github.com/Developers0101/notes-android-course/raw/main/images/%D9%86%D9%88%DB%8C%DA%AF%DB%8C%D8%B4%D9%86%20%DA%A9%D8%A7%D9%85%D9%BE%D9%88%D9%86%D9%86%D8%AA_files/image011.png)

![My image](https://github.com/Developers0101/notes-android-course/raw/main/images/%D9%86%D9%88%DB%8C%DA%AF%DB%8C%D8%B4%D9%86%20%DA%A9%D8%A7%D9%85%D9%BE%D9%88%D9%86%D9%86%D8%AA_files/image012.png)

و بعد فرگمنت رو یا از create new destination بسازیم و اضافه کنیم یا فرگمنتی که ازقبل داشتیم رو از لیست اضافه کنیم.

حالت کدی navigation :

![My image](https://github.com/Developers0101/notes-android-course/raw/main/images/%D9%86%D9%88%DB%8C%DA%AF%DB%8C%D8%B4%D9%86%20%DA%A9%D8%A7%D9%85%D9%BE%D9%88%D9%86%D9%86%D8%AA_files/image013.jpg)

Strat destination که فرگمنت اول یا شروعمون هست.

name که میاد به کلاس خود فرگمنتمون اشاره میکنه.

label به اسم یا title فرگمنت اشاره میکنه.

Layout هم اسم لایه xml فرگمنتمون رو نشون میده و اشاره میکنه.

![My image](https://github.com/Developers0101/notes-android-course/raw/main/images/%D9%86%D9%88%DB%8C%DA%AF%DB%8C%D8%B4%D9%86%20%DA%A9%D8%A7%D9%85%D9%BE%D9%88%D9%86%D9%86%D8%AA_files/image014.jpg)

به فلش هایی که دوتا فرگمنت رو بهم وصل میکنه میگن اکشن.

هرکدوم از action ها تنظیمات مخصوص به خودشونو دارن و میتونیم بصورت جدا و اختصاصی براشون تنظیمات ست کنیم.

![My image](https://github.com/Developers0101/notes-android-course/raw/main/images/%D9%86%D9%88%DB%8C%DA%AF%DB%8C%D8%B4%D9%86%20%DA%A9%D8%A7%D9%85%D9%BE%D9%88%D9%86%D9%86%D8%AA_files/image015.png)

رو هر فرگمنتی که اکشن داره بریم id اون action و مقصدش  که destination میشه رو نشون میده.

نام گذاری id action هم به این صورت هست که میاد اولش action میزاره بعد اسم فرگمنت اول بعد میگه to یعنی بره به بعد اسم فرگمنت دوم که میتونیم تغییرش بدیم:

![My image](https://github.com/Developers0101/notes-android-course/raw/main/images/%D9%86%D9%88%DB%8C%DA%AF%DB%8C%D8%B4%D9%86%20%DA%A9%D8%A7%D9%85%D9%BE%D9%88%D9%86%D9%86%D8%AA_files/image016.png)

![My image](https://github.com/Developers0101/notes-android-course/raw/main/images/%D9%86%D9%88%DB%8C%DA%AF%DB%8C%D8%B4%D9%86%20%DA%A9%D8%A7%D9%85%D9%BE%D9%88%D9%86%D9%86%D8%AA_files/image017.png)

انیمیشن هایی که میشه روی action اعمال کرد.

قسمت 18

![My image](https://github.com/Developers0101/notes-android-course/raw/main/images/%D9%86%D9%88%DB%8C%DA%AF%DB%8C%D8%B4%D9%86%20%DA%A9%D8%A7%D9%85%D9%BE%D9%88%D9%86%D9%86%D8%AA_files/image018.png)

برای اینکه بتونیم از navigation استفاده کنیم به لایه main xml میریم بعد nav رو سرچ میکنیم و چون میخوایم با nav host کار کنیم اونو انتخاب میکنیم و بعد از قسمت navigation میایم و nav مورد نظرو اضافه میکنیم یا میتونیم دستی اضافه کنیم:

![My image](https://github.com/Developers0101/notes-android-course/raw/main/images/%D9%86%D9%88%DB%8C%DA%AF%DB%8C%D8%B4%D9%86%20%DA%A9%D8%A7%D9%85%D9%BE%D9%88%D9%86%D9%86%D8%AA_files/image019.png)

از Fragment Container View استفاده شده.

اگه بخوایم دستی کد بزنیم باید عین خود name رو حتماً وارد کنیم.

براش default Nav Host یا nav پیشفرض رو true در نظر میگیریم.

بعد nav Graph میایم و nav\_main یا اون nav یی که ساختیم رو بهش میدیم.

![My image](https://github.com/Developers0101/notes-android-course/raw/main/images/%D9%86%D9%88%DB%8C%DA%AF%DB%8C%D8%B4%D9%86%20%DA%A9%D8%A7%D9%85%D9%BE%D9%88%D9%86%D9%86%D8%AA_files/image020.png)

برای دسترسی به navigation و فرگمنت هامون، از nav controller استفاده میکنیم، مثلاً اجرای back یا اینکه بیایم و با توجه به تغییر صفحات فرگمنت title صفحه رو عوض کنیم و ... باید navigation رو در صفحه main activity تعریف کنیم.

![My image](https://github.com/Developers0101/notes-android-course/raw/main/images/%D9%86%D9%88%DB%8C%DA%AF%DB%8C%D8%B4%D9%86%20%DA%A9%D8%A7%D9%85%D9%BE%D9%88%D9%86%D9%86%D8%AA_files/image021.png)

![My image](https://github.com/Developers0101/notes-android-course/raw/main/images/%D9%86%D9%88%DB%8C%DA%AF%DB%8C%D8%B4%D9%86%20%DA%A9%D8%A7%D9%85%D9%BE%D9%88%D9%86%D9%86%D8%AA_files/image022.png)

بعد برای دسترسی به navigation میایم اونو با find nav Controller مقدار دهی میکنیم و id fragment container view که داخل xml main تعریف کرده بودیم رو بهش میدیم.

![My image](https://github.com/Developers0101/notes-android-course/raw/main/images/%D9%86%D9%88%DB%8C%DA%AF%DB%8C%D8%B4%D9%86%20%DA%A9%D8%A7%D9%85%D9%BE%D9%88%D9%86%D9%86%D8%AA_files/image023.png)

برای اینکه بتونیم back رو هندل کنیم میایم و خارج از on create متد on navigation up که از متدهای خود navigation هست رو اضافه میکنیم و nav controller رومون رو توش قرار میدیم و با navigate up میتونیم back رو هرچندتا صفحه که باشه هندل کنیم و بعدش از علامت || استفاده میکنیم.

![My image](https://github.com/Developers0101/notes-android-course/raw/main/images/%D9%86%D9%88%DB%8C%DA%AF%DB%8C%D8%B4%D9%86%20%DA%A9%D8%A7%D9%85%D9%BE%D9%88%D9%86%D9%86%D8%AA_files/image024.png)

ولی موقعه ایی که برنامه رو اجرا میکنیم کرش میکنه چون میگه زمانی که میخوایم با find nav controller نمیتونه id nav host که مربوط به fragment container view میشه رو پیدا کنه.

![My image](https://github.com/Developers0101/notes-android-course/raw/main/images/%D9%86%D9%88%DB%8C%DA%AF%DB%8C%D8%B4%D9%86%20%DA%A9%D8%A7%D9%85%D9%BE%D9%88%D9%86%D9%86%D8%AA_files/image025.png)

و اگه ما بیایم و fragment container view رو به fragment تغییر بدیم اوکی میشه و دیگه کرش نمیکنه.

![My image](https://github.com/Developers0101/notes-android-course/raw/main/images/%D9%86%D9%88%DB%8C%DA%AF%DB%8C%D8%B4%D9%86%20%DA%A9%D8%A7%D9%85%D9%BE%D9%88%D9%86%D9%86%D8%AA_files/image026.png)

برای اینکه بتونیم داخل action bar بجای اسم app بیاد اسم هر صفحه رو بنویسیم باید از app bar configuration استفاده کنیم  که توسط این میتونیم به action bar دسترسی داشته باشیم.

![My image](https://github.com/Developers0101/notes-android-course/raw/main/images/%D9%86%D9%88%DB%8C%DA%AF%DB%8C%D8%B4%D9%86%20%DA%A9%D8%A7%D9%85%D9%BE%D9%88%D9%86%D9%86%D8%AA_files/image027.jpg)

بعد میایم و هرتعداد که فرگمنت داریم رو بهش میدیم.

set of جز collection های کاتلین بحساب میاد و داخلش مجموعه فرگمنت هامونو مینویسیم.

![My image](https://github.com/Developers0101/notes-android-course/raw/main/images/%D9%86%D9%88%DB%8C%DA%AF%DB%8C%D8%B4%D9%86%20%DA%A9%D8%A7%D9%85%D9%BE%D9%88%D9%86%D9%86%D8%AA_files/image028.png)

بعد میایم تنظیمات یا configuration مون رو با setup Action Bar With Nav Controller به action bar مون میدیم که جزء متدهای خود navigation بحساب میاد و از ما 2تا ورودی میخواد که ورودی اول از ما nav controller میخواد و ورودی دوم از ما app bar configuration میخواد.

![My image](https://github.com/Developers0101/notes-android-course/raw/main/images/%D9%86%D9%88%DB%8C%DA%AF%DB%8C%D8%B4%D9%86%20%DA%A9%D8%A7%D9%85%D9%BE%D9%88%D9%86%D9%86%D8%AA_files/image029.jpg)

وقتی برنامه رو اجرا میکنیم توی اکشن بار اسم فرگمنت رو نشون میده:

![My image](https://github.com/Developers0101/notes-android-course/raw/main/images/%D9%86%D9%88%DB%8C%DA%AF%DB%8C%D8%B4%D9%86%20%DA%A9%D8%A7%D9%85%D9%BE%D9%88%D9%86%D9%86%D8%AA_files/image030.png)

ولی اسم lablel که تو nav main بود:

![My image](https://github.com/Developers0101/notes-android-course/raw/main/images/%D9%86%D9%88%DB%8C%DA%AF%DB%8C%D8%B4%D9%86%20%DA%A9%D8%A7%D9%85%D9%BE%D9%88%D9%86%D9%86%D8%AA_files/image031.png)

که میایم و تغییرش میدیم:

![My image](https://github.com/Developers0101/notes-android-course/raw/main/images/%D9%86%D9%88%DB%8C%DA%AF%DB%8C%D8%B4%D9%86%20%DA%A9%D8%A7%D9%85%D9%BE%D9%88%D9%86%D9%86%D8%AA_files/image032.png)

![My image](https://github.com/Developers0101/notes-android-course/raw/main/images/%D9%86%D9%88%DB%8C%DA%AF%DB%8C%D8%B4%D9%86%20%DA%A9%D8%A7%D9%85%D9%BE%D9%88%D9%86%D9%86%D8%AA_files/image033.png)

![My image](https://github.com/Developers0101/notes-android-course/raw/main/images/%D9%86%D9%88%DB%8C%DA%AF%DB%8C%D8%B4%D9%86%20%DA%A9%D8%A7%D9%85%D9%BE%D9%88%D9%86%D9%86%D8%AA_files/image034.png)

میخوایم بواسطه کلیک روی دکمه send از فرگمنت home به detail بریم که برای اینکار از find nav controller و navigate استفاده میکنیم.

navigate از ما id میخواد که میایم و id همون action که تعریف کرده بودیم و گفته بودیم از home برو به detail رو میدیم.

براحتی back هم ساپورت میشه و میتونیم از فرگمنت detail برگردیم به home.

قسمت 19

برای ارسال اطلاعات بین فرگمنت ها مثلاً a به b میریم روی فرگمنت مقصد یا b :

![My image](https://github.com/Developers0101/notes-android-course/raw/main/images/%D9%86%D9%88%DB%8C%DA%AF%DB%8C%D8%B4%D9%86%20%DA%A9%D8%A7%D9%85%D9%BE%D9%88%D9%86%D9%86%D8%AA_files/image035.png)

روی + یا add argument داخل arguments مربوط به detail fragment یا فرگمنت مقصدمون میزنیم.

![My image](https://github.com/Developers0101/notes-android-course/raw/main/images/%D9%86%D9%88%DB%8C%DA%AF%DB%8C%D8%B4%D9%86%20%DA%A9%D8%A7%D9%85%D9%BE%D9%88%D9%86%D9%86%D8%AA_files/image036.png)

داخل قسمت name میگه اون کلیدی که میخوایم اطلاعات صفحه a رو به b بفرستیم بگیم مثل bundle در activity .

داخل قسمت type میایم و نوعشو مشخص میکنیم مثلاً int, string و ... .
اگه از نوع آرایه باشه تیک Array رو میزنیم.

اگه میخوایم null پذیر باشه تیک Nullable رو میزنیم.

میتونیم براش مقدار پیشفرض هم set کنیم یا خالی بزاریم داخل قسمت default value و بعد add رو میزنیم.

![My image](https://github.com/Developers0101/notes-android-course/raw/main/images/%D9%86%D9%88%DB%8C%DA%AF%DB%8C%D8%B4%D9%86%20%DA%A9%D8%A7%D9%85%D9%BE%D9%88%D9%86%D9%86%D8%AA_files/image037.png)

تو قسمت arguments توی فرگمنت مقصد اضافه میشه.

![My image](https://github.com/Developers0101/notes-android-course/raw/main/images/%D9%86%D9%88%DB%8C%DA%AF%DB%8C%D8%B4%D9%86%20%DA%A9%D8%A7%D9%85%D9%BE%D9%88%D9%86%D9%86%D8%AA_files/image038.png)

اگه روی خود action ش هم بریم به ما argument و اطلاعاتی که میخواد بفرسته رو نشون میده.

![My image](https://github.com/Developers0101/notes-android-course/raw/main/images/%D9%86%D9%88%DB%8C%DA%AF%DB%8C%D8%B4%D9%86%20%DA%A9%D8%A7%D9%85%D9%BE%D9%88%D9%86%D9%86%D8%AA_files/image039.png)

اگه داخل کد هم بریم به ما argument رو نشون میده.

بهتر هروقت از argument ها استفاده کردیم پروژه رو اول clean و بعد rebuild کنیم که خیالمون راحت باشه که کلاس Directions, Args ساخته میشه.

![My image](https://github.com/Developers0101/notes-android-course/raw/main/images/%D9%86%D9%88%DB%8C%DA%AF%DB%8C%D8%B4%D9%86%20%DA%A9%D8%A7%D9%85%D9%BE%D9%88%D9%86%D9%86%D8%AA_files/image040.png)

برای ارسال اطلاعات بین فرگمنت ها میتونیم هر اسمی روش بزاریم ولی اکثراً اسمشو action یا direction میزارن و میریم به کلاس مبداً و اونجا direction تعریف میکنیم.

وقتی برای مقصد یک action میایم و یک argument یی ست میکنیم، برای مبداًش میایم و یک کلاس direction درست میکنیم.

کلاس مبداًمون home fragment بود و کلاس انتقالی برای ارسال اطلاعات میشه، 

` `home fragment direction و اگه ما argument یی set نکرده باشیم کلاس home fragment direction رو برای ما نمیسازه، بخاطر همین اگه یه موقعی درست نکرده باشه با clean, rebuild دیگه خیالمون راحت میشه که درست میکنه این کلاس هارو.

![My image](https://github.com/Developers0101/notes-android-course/raw/main/images/%D9%86%D9%88%DB%8C%DA%AF%DB%8C%D8%B4%D9%86%20%DA%A9%D8%A7%D9%85%D9%BE%D9%88%D9%86%D9%86%D8%AA_files/image041.jpg)

بعد میایم و action مون رو بهش پاس میدیم که دو حالت داره یکی خود action مون و یکی دیگه کلاسش که ما از خود action مون استفاده میکنیم نه کلاسش.

![My image](https://github.com/Developers0101/notes-android-course/raw/main/images/%D9%86%D9%88%DB%8C%DA%AF%DB%8C%D8%B4%D9%86%20%DA%A9%D8%A7%D9%85%D9%BE%D9%88%D9%86%D9%86%D8%AA_files/image042.png)

![My image](https://github.com/Developers0101/notes-android-course/raw/main/images/%D9%86%D9%88%DB%8C%DA%AF%DB%8C%D8%B4%D9%86%20%DA%A9%D8%A7%D9%85%D9%BE%D9%88%D9%86%D9%86%D8%AA_files/image043.png)

از ما اون argument یی که تعریف کرده بودیم و از نوع string بود رو میخواد که ما میخوایم از

` `edit text مون string بگیریم و اون بفرستیم و به این صورت bundle رو میفرستیم.

![My image](https://github.com/Developers0101/notes-android-course/raw/main/images/%D9%86%D9%88%DB%8C%DA%AF%DB%8C%D8%B4%D9%86%20%DA%A9%D8%A7%D9%85%D9%BE%D9%88%D9%86%D9%86%D8%AA_files/image044.jpg)

بعد میایم موقع رفتن به فرگمنت بعدی داخل navigate از direction استفاده میکنیم که هم bundle رو داریم و هم action رو و به همین راحتی اطلاعات ارسال شد.

وقتی ما یک arguments جدید اضافه میکنیم، همونطوری که برای مبداً یک کلاس direction میسازه برای مقصد هم یک کلاس args درست میکنه که مخفف arguments هست.

اطلاعات توسط direction ارسال و توسط args دریافت میشه.

وقتی از comment other استفاده میکنیم یعنی تمام چیزهای general رو اون قسمت قرار میدیم.

![My image](https://github.com/Developers0101/notes-android-course/raw/main/images/%D9%86%D9%88%DB%8C%DA%AF%DB%8C%D8%B4%D9%86%20%DA%A9%D8%A7%D9%85%D9%BE%D9%88%D9%86%D9%86%D8%AA_files/image045.png)

توسط nav Args میایم و initialize میکنیم و کلاس مقصدمون که detail fregament args هست رو برای args مون قرار میدیم.

![My image](https://github.com/Developers0101/notes-android-course/raw/main/images/%D9%86%D9%88%DB%8C%DA%AF%DB%8C%D8%B4%D9%86%20%DA%A9%D8%A7%D9%85%D9%BE%D9%88%D9%86%D9%86%D8%AA_files/image046.png)

` `یه متغییر دیگه هم تعریف میکنیم که text یی که از bundle برای ما فرستاده میشه رو بصورت مستقیم استفاده نکنیم و بعد این متغییرو هرجا که خواستیم و داخل هر view که خواستیم بتونیم ازش استفاده کنیم.

![My image](https://github.com/Developers0101/notes-android-course/raw/main/images/%D9%86%D9%88%DB%8C%DA%AF%DB%8C%D8%B4%D9%86%20%DA%A9%D8%A7%D9%85%D9%BE%D9%88%D9%86%D9%86%D8%AA_files/image047.png)

![My image](https://github.com/Developers0101/notes-android-course/raw/main/images/%D9%86%D9%88%DB%8C%DA%AF%DB%8C%D8%B4%D9%86%20%DA%A9%D8%A7%D9%85%D9%BE%D9%88%D9%86%D9%86%D8%AA_files/image048.png)

حالا توسط args به bundle info یی که داخل arguments مون تعریف کرده بودیم دسترسی داریم و باهاش اطلاعات فرستاده شده رو دریافت میکنیم.

![My image](https://github.com/Developers0101/notes-android-course/raw/main/images/%D9%86%D9%88%DB%8C%DA%AF%DB%8C%D8%B4%D9%86%20%DA%A9%D8%A7%D9%85%D9%BE%D9%88%D9%86%D9%86%D8%AA_files/image049.png)

به همین راحتی اطلاعاتی که فرستادیم رو دریافت میکنیم.

یه روش دیگه ایی هم برای ارسال اطلاعات داره که ما میخوایم کلاسی از اطلاعات رو بفرستیم مثلاً 20 یا بیشتر و دیگه 1 دونه اطلاعات نیست که با استفاده از parselable (مطمئن نیستم :دی) اینکارو انجام میدیم.

قسمت 20

بعضی وقتها ممکن وقتی فرگمنت هامونو توی navigation اضافه کردیم ولی لایه اش رو نشون نده:

![My image](https://github.com/Developers0101/notes-android-course/raw/main/images/%D9%86%D9%88%DB%8C%DA%AF%DB%8C%D8%B4%D9%86%20%DA%A9%D8%A7%D9%85%D9%BE%D9%88%D9%86%D9%86%D8%AA_files/image050.png)

که میریم و tools و اون layout مورد نظرمونو اضافه میکنیم و اوکی میشه.

در bottom navigation برای اینکه بین این فرگمنت هامون جابجا بشیم نیازی به action نداریم چون جابجایی بینشون توسط menu که در پایین صفحه قرار داره، اتفاق میفته و سوییچ میشن و به این منو میگن bottom navigation که یه attribute داره به اسم menu و از ما منو میگیره.

برای اینکه بتونیم از bottom navigation استفاده کنیم نیاز به یه فایل دیگه توی پوشه res داریم:

![My image](https://github.com/Developers0101/notes-android-course/raw/main/images/%D9%86%D9%88%DB%8C%DA%AF%DB%8C%D8%B4%D9%86%20%DA%A9%D8%A7%D9%85%D9%BE%D9%88%D9%86%D9%86%D8%AA_files/image051.jpg)

![My image](https://github.com/Developers0101/notes-android-course/raw/main/images/%D9%86%D9%88%DB%8C%DA%AF%DB%8C%D8%B4%D9%86%20%DA%A9%D8%A7%D9%85%D9%BE%D9%88%D9%86%D9%86%D8%AA_files/image052.png)

حتماً باید directory name, resource type از نوع menu باشه.

![My image](https://github.com/Developers0101/notes-android-course/raw/main/images/%D9%86%D9%88%DB%8C%DA%AF%DB%8C%D8%B4%D9%86%20%DA%A9%D8%A7%D9%85%D9%BE%D9%88%D9%86%D9%86%D8%AA_files/image053.jpg)

حالا میریم داخل پوشه menu بعد new و بعد menu resource file رو انتخاب میکنیم و بعد :

![My image](https://github.com/Developers0101/notes-android-course/raw/main/images/%D9%86%D9%88%DB%8C%DA%AF%DB%8C%D8%B4%D9%86%20%DA%A9%D8%A7%D9%85%D9%BE%D9%88%D9%86%D9%86%D8%AA_files/image054.png)

چون از نوع menu هست اول اسمش رو menu میزاریم و مربوط به صفحه home میشه میگیم menu home .

![My image](https://github.com/Developers0101/notes-android-course/raw/main/images/%D9%86%D9%88%DB%8C%DA%AF%DB%8C%D8%B4%D9%86%20%DA%A9%D8%A7%D9%85%D9%BE%D9%88%D9%86%D9%86%D8%AA_files/image055.png)

هرچیزی که در menu وجود داره در قالب آیتم در نظر گرفته میشه.

Item باید حتماً id داشته باشه.

باید حتماً id که برای فرگمنت هامون داخل navigation در نظر میگیریم با id یی که داخل menu در نظر میگیریم یکی باشه:

![My image](https://github.com/Developers0101/notes-android-course/raw/main/images/%D9%86%D9%88%DB%8C%DA%AF%DB%8C%D8%B4%D9%86%20%DA%A9%D8%A7%D9%85%D9%BE%D9%88%D9%86%D9%86%D8%AA_files/image056.png)

![My image](https://github.com/Developers0101/notes-android-course/raw/main/images/%D9%86%D9%88%DB%8C%DA%AF%DB%8C%D8%B4%D9%86%20%DA%A9%D8%A7%D9%85%D9%BE%D9%88%D9%86%D9%86%D8%AA_files/image057.png)

item از ما title و icon هم میگیره که id و title اجباری هستن و حتماً باید باشن وگرنه error میده ولی icon اختیاری هست.

و میایم برای اون تعداد فرگمنتی که در منو در نظر گرفتیم که بیشتر از 5 تا نباید در bottom navigation قرار داد براشون item تعریف میکنیم و آیدی، تایتل و آیکون بهشون اضافه میکنیم.

![My image](https://github.com/Developers0101/notes-android-course/raw/main/images/%D9%86%D9%88%DB%8C%DA%AF%DB%8C%D8%B4%D9%86%20%DA%A9%D8%A7%D9%85%D9%BE%D9%88%D9%86%D9%86%D8%AA_files/image058.png)

بعد میریم تو لایه activity main xml مون و bottom navigation رو اضافه میکنیم.

![My image](https://github.com/Developers0101/notes-android-course/raw/main/images/%D9%86%D9%88%DB%8C%DA%AF%DB%8C%D8%B4%D9%86%20%DA%A9%D8%A7%D9%85%D9%BE%D9%88%D9%86%D9%86%D8%AA_files/image059.jpg)

براش یه id در نظر میگیریم و یه اتریبیوتی به اسم menu داره که باید براش منویی که تو res- menu ساخته بودیم رو بهش بدیم.


![My image](https://github.com/Developers0101/notes-android-course/raw/main/images/%D9%86%D9%88%DB%8C%DA%AF%DB%8C%D8%B4%D9%86%20%DA%A9%D8%A7%D9%85%D9%BE%D9%88%D9%86%D9%86%D8%AA_files/image060.png)

برای استفاده از bottom navigation میریم توی Main activity و با استفاده از setup with navcontroller ، bottom navigation و navigation مون رو بهم وصل میکنیم و به

` `bottom navigation اجازه میدیم به ازای کلیک روی هرکدوم از منوهای پایین، فرگمنت هامونم تغییر کنه.

![My image](https://github.com/Developers0101/notes-android-course/raw/main/images/%D9%86%D9%88%DB%8C%DA%AF%DB%8C%D8%B4%D9%86%20%DA%A9%D8%A7%D9%85%D9%BE%D9%88%D9%86%D9%86%D8%AA_files/image061.jpg)

![My image](https://github.com/Developers0101/notes-android-course/raw/main/images/%D9%86%D9%88%DB%8C%DA%AF%DB%8C%D8%B4%D9%86%20%DA%A9%D8%A7%D9%85%D9%BE%D9%88%D9%86%D9%86%D8%AA_files/image062.png)

` `با استفاده از lable visibility mode میتونیم حالت نمایش bottom navigation رو تغییر بدیم.

auto براساس سایز و اینجور چیزا ست میکنه.

labeled بصورت پیشفرض هم روی labeled هست و میاد نوشته هارو پایین نشون میده و فقط میاد رنگ اون آیتمی که انتخاب شده رو تغییر میده.

selected یعنی آیتمی که انتخاب شده رو با اسم نشون بده.

unlabeled یعنی کلاً هیچ اسمی رو نشون نده و فقط با آیکون ها بالا پایین میشه.

قسمت 21

Deep link : مثلاً وقتی وارد اپ یا سایت دیجی کالا میشیم و لینک اون صفحه رو میگیریم و در واتساپ یا تلگرام برای یه نفر میفرستیم و اون شخص وقتی اون لینک رو باز میکنه، میتونه علاوه بر مرورگر اون رو بصورت اپلیکیشن هم باز کنه که بهش میگن deep link و برای رفتن به یک صفحه و لینک و یک چیز خاص.

![My image](https://github.com/Developers0101/notes-android-course/raw/main/images/%D9%86%D9%88%DB%8C%DA%AF%DB%8C%D8%B4%D9%86%20%DA%A9%D8%A7%D9%85%D9%BE%D9%88%D9%86%D9%86%D8%AA_files/image063.png)

وقتی رو + deep link بزنیم در صفحه باز شده:

Uri داره که همون url هست و اون url که بواسطه اون میخوایم برنامه شناسونده بشه رو میفرستیم مثلاً ما میایم از url دیجی کالا [www.digikala.com/product](http://www.digikala.com/product) رو قرار میدیم و حالا بعد product هرچی اضافه بشه بعد کاربر این لینک رو توی اپ های دیگه مثل اینستا، تلگرام، sms یا هرجای دیگه باز کنه تو قسمت پیشنهادی یا suggested میاره که با اپ بازش کنه ولی اگه توی لینک بجای product از person یا هرچیز دیگه ایی استفاده کنه دیگه تو suggested نمیاره چون تو داخل قسمت url مشخص نکرده بودیم و فقط product رو نشون میده.

به ازای هر deep link که به app مون اضافه میکنیم چه برای یک صفحه یا صفحات مختلف، به ازای همون url ها میاد و app مارو نشون میده و وارد همون صفحه میشه.

MIME حالت های مختلفی رو میاره، مثلاً text باشه یا عکس باشه و ... .

action شبیه همون action هایی هست که توی intent بود و حالت send ، edit و view داشته باشه.

![My image](https://github.com/Developers0101/notes-android-course/raw/main/images/%D9%86%D9%88%DB%8C%DA%AF%DB%8C%D8%B4%D9%86%20%DA%A9%D8%A7%D9%85%D9%BE%D9%88%D9%86%D9%86%D8%AA_files/image064.png)

زمانی که بخوایم علاوه بر deep link از argument هم استفاده کنیم و اطلاعات رو بگیریم باید کلید اون argument رو داخل deep link قرار بدیم.

زمانی نیاز پیدا میکنیم به گرفتن اطلاعات که بخوایم مثلاً id یه محصول رو در صفحه جزئیات ببینیم که اون موقع باید داخل deep link بیایم و argument رو قرار بدیم.

زمانی که میخوایم از deep link استفاده کنیم حتماً باید داخل manifest هم اونو تعریف کنیم.

![My image](https://github.com/Developers0101/notes-android-course/raw/main/images/%D9%86%D9%88%DB%8C%DA%AF%DB%8C%D8%B4%D9%86%20%DA%A9%D8%A7%D9%85%D9%BE%D9%88%D9%86%D9%86%D8%AA_files/image065.png)

میایم و داخل خود تگ activity و از تگ nav-graph استفاده میکنیم.

![My image](https://github.com/Developers0101/notes-android-course/raw/main/images/%D9%86%D9%88%DB%8C%DA%AF%DB%8C%D8%B4%D9%86%20%DA%A9%D8%A7%D9%85%D9%BE%D9%88%D9%86%D9%86%D8%AA_files/image066.png)

بعد از ما یه value میخواد که میایم navigation مورد نظرمونو بهش میدیم و تگ رو میبندیم.

