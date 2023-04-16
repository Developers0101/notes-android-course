---
layout: default
title: 8- ویو مدل
nav_order: 3
---
# 8- ویو مدل
قسمت 43

ویومدل یک از مباحث معماری mvvm بحساب میاد.


![My image](https://github.com/Developers0101/notes-android-course/raw/main/images/%D9%88%DB%8C%D9%88%20%D9%85%D8%AF%D9%84_files/image001.jpg)

یکی از عمده مشکلاتی که توی برنامه اندروید وجود داره اینه که، وقتی که اکتیویتی یا فرگمنت و اون صفحه ایی که داریم باهاش کار میکنیم recreate میشه.

مثلاً زمانی که داریم با اپلیکشن کار میکنیم اون رو از حالت عمودی به افقی یا landscape یا عریض تغییر بدیم و بخوایم کار کنیم، همه چیز بهم میریزه و ui دوباره از اول ساخته میشه و همه ی مواردی که ذخیره کردیم، همشون از اول ساخته میشن، مثلاً کاربر حین کار کردن با گوشی داشته آیتم30 یه recycler view رو می دیده، بعد گوشی رو rotate کنه، همه ی اطلاعات میره و از اول درخواست زده میشه و کاربرو میبره به اول اون صفحه و باید دوباره اسکرول کنه، و عملاً ux بهم میریزه و اصلاً مناسب نیست.

اینجور مواقع اکثراً از on save instance state استفاده میکردن و اون وضعیت رو نگهداری میکردن یا اون اطلاعات رو ذخیره میکردن، ولی این متد اصلاً برای نگهداری اطلاعات سنگین و بزرگ مناسب نبود و اپلیکیشن رو سنگین میکرد.

بخاطر همین اومدن یه سری component هارو در قالب jetpack component اضافه کردن که view model هم جزء اون هاست.

View model میاد و در برابر اون recreate شدن مقاومت میکنه، یعنی وقتی اون صفحه ی اکتیویتی یا فرگمنت داره recreate میشه، دیگه اطلاعات رو از اول نمیسازه و ادامه همونو میزاره تا کاربر بتونه ازش استفاده کنه.

مثلاً اگه کاربر در لیست 50 باشه و rotate کنه میتونه ادامه لیست رو ببینه نه از اول، یا کاربر داشت محاسبات ریاضی انجام میداد که اگه rotate میشد از بین میرفت ولی با view model میتونه ادامه محاسبات رو بعد rotate انجام بده.

برای ذخیره شدن وضعیت در view model نیازی به دیتابیس یا shared preferences نیست و خودش کاملاً خودکار اینکارو انجام میده.

 ویومدل یکی کلاسی که برای جدا کردن اطلاعات ui از فرگمنت و اکیتیوتی مورد استفاده قرار میگیره و از همه مهمتر در برابر recreate شدن مقاوم هست.

![My image](https://github.com/Developers0101/notes-android-course/raw/main/images/%D9%88%DB%8C%D9%88%20%D9%85%D8%AF%D9%84_files/image002.jpg)

اکتیوتی و فرگمنت خیلی سنگین هستن مخصوصاً اکتیویتی که یه component خیلی سنگین و نباید داخل view model از فرگمنت، اکتیویتی و context استفاده کرد، یعنی نباید کلشو داخل view model ذخیره کرد که به یکسری از آیتم هاش دسترسی داشته باشیم.

برای استفاده از context داخل view model میتونیم از hilt استفاده کنیم و خودش تامین میکنه و نیاز نیست که کل context رو توی view model ذخیره کنیم، یا میتونیم از application context استفاده کنیم.

Application context به lifecycle اون صفحه کاملاً آگاه، و وقتی که داریم اون صفحه یا اپلیکشن رو از بین میبریم، میفهمه که از بین رفته و یکسری از دسترسی هایی که به context داره رو از بین میبره، چون application context به اون چرخه ی حیات آگاه، برای همین میتونه همچین کاری بکنه، ولی خود context همچین قابلیتی نداره و ما باید دستی اونو هندل کنیم.

View model یه متدی داره به اسم on cleared که جزء چرخه ی حیات view model هست و کاملاً به lifecycle یا چرخه ی حیات اون صفحه کاملاً آگاه هست(کلاً view model به چرخه ی حیات اون صفحه آگاه)، وقتی application کلاً بسته میشه یا اون صفحه بسته میشه on cleared صدا زده میشه.

بیشتر مواقع برای استفاده از on cleared نیازی به کارهای خاصی توی این متد نیست، ولی بعضی مواقع نیاز، مثل زمانی که میخوایم از timer ها استفاده کنیم، و اگه توی on cleared timer رو stop نکنیم میاد و همینطور میشمره.

در اکثر موارد view model خودش میاد و همه ی کارهارو هندل میکنه، مثلاً اطلاعاتی که داره رو پاک میکنه، و فضای خالی رو در اختیار RAM قرار میده تا بتونه ازش استفاده کنه و ... .

ولی بعضی مواقع که از چیزهایی خاصی استفاده میکنیم باید حواسمون باشه که وقتی صفحه رو میبندیم، این چیزی که داریم استفاده میکنیم، بیایم و صفحه رو کنسل کنیم یا null ش کنیم یا پاکش کنیم، که توسط متد on cleared میتونیم این کارهارو انجام بدیم و تقریباً شبیه on destroy فرگمنت و اکتیویتی هست.

![My image](https://github.com/Developers0101/notes-android-course/raw/main/images/%D9%88%DB%8C%D9%88%20%D9%85%D8%AF%D9%84_files/image003.jpg)

چرخه حیات یا lifecycle view model :

زمانی که activity داره شروع به کار میکنه :

![My image](https://github.com/Developers0101/notes-android-course/raw/main/images/%D9%88%DB%8C%D9%88%20%D9%85%D8%AF%D9%84_files/image004.png)

این 3 تا متد همزمان با هم و به ترتیب صدا زده میشن.

وقتی هم که بسته میشه:

![My image](https://github.com/Developers0101/notes-android-course/raw/main/images/%D9%88%DB%8C%D9%88%20%D9%85%D8%AF%D9%84_files/image005.png)

این 3تا متد به ترتیب و باهم صدا زده میشن.

وقتی که اپلیکیشن یا activity داره rotate میشه، در هردو حالت عمودی و افقی:

![My image](https://github.com/Developers0101/notes-android-course/raw/main/images/%D9%88%DB%8C%D9%88%20%D9%85%D8%AF%D9%84_files/image006.png)

این متدها همزمان و به ترتیب صدا زده میشن، در واقع اول اون صفحه رو از بین میبره و بعد دوباره on create میشه و چون قبل on create اومده و on destroy شده، همه ی اطلاعات از بین میره و پاک شده و دوباره داره همه ی اون اطلاعات رو میسازه.

اما view model از ابتدای on create :

![My image](https://github.com/Developers0101/notes-android-course/raw/main/images/%D9%88%DB%8C%D9%88%20%D9%85%D8%AF%D9%84_files/image007.png)

تا انتهای چرخه ی حیات اون صفحه یا اپلیکیشن :

![My image](https://github.com/Developers0101/notes-android-course/raw/main/images/%D9%88%DB%8C%D9%88%20%D9%85%D8%AF%D9%84_files/image008.png)

و زمانی که اپلیکیشن یا صفحه on destroy میشه، view model کاملاً میدونه، آگاه و مقاومت داره، و زمانی که داره اون صفحه rotate میشه وضعیت و اطلاعات رو بصورت موقت توی خودش ذخیره میکنه و نگه میداره تا از بین نره.

در نهایت زمانی که خواستیم صفحه رو ببندیم یا کنسل کنیم یا اپلیکیشن مون رو ببندیم و زمانی که view model هم داره بسته میشه، on cleared رو در اختیار ما قرار میده، و اگه از شرایط خاص مثل timer استفاده کردیم میتونیم بیام و اینجا کنسلش کنیم.

View model حالتیه که میاد برای ما زمانی که activity یا fragment مون rotate میشه، اون اطلاعاتی که میخوایم رو برای ما ذخیره میکنه، که بتونیم ازشون استفاده کنیم و دوباره نسازیمشون که یه حالت ux خیلی بدی رو به کاربر بده.

قسمت 44

خود view model بصورت پیشفرض نیازه نداره که ما یه dependency جدیدی رو به gradle مون اضافه کنیم، ولی چون ما میخوایم از یه حالتش استفاده کنیم، view model خودش یک کلاس، و موقع استفاده باید initialize بشه، که جدیدترین، بهترین و مدرترین روش برای initialize کردن view model ، استفاده از kotlin delegate هست.

![My image](https://github.com/Developers0101/notes-android-course/raw/main/images/%D9%88%DB%8C%D9%88%20%D9%85%D8%AF%D9%84_files/image009.png)

برای استفاده از kotlin delegate ما این کتابخونه رو به gradle اضافه میکنیم.

مثالمون اینه که یه دکمه داریم که وقتی روش میزنیم یه دونه به عددمون اضافه میشه وقتی که صفحه رو rotate میکنیم عدد دوباره برمیگرده از اول و 0 میشه برای جلوگیری از اینکار از view model استفاده میکنیم:

![My image](https://github.com/Developers0101/notes-android-course/raw/main/images/%D9%88%DB%8C%D9%88%20%D9%85%D8%AF%D9%84_files/image010.png)

وقتی برنامه رو اجرا میگیرم و روی اعداد میزنیم مثلاً 10 بعد که گوشی رو rotate میکنیم عدد برمیگرده از اول و 0 میشه یعنی اپلیکیشن یا activity مون recreate میشه و طبق اون عکس lifecycle و اون 6 موردش که گفتیم، اکتیویتی بسته میشه و دوباره از اول ساخته میشه.

برای حل این مشکل از کلاس view model استفاده میکنیم.

![My image](https://github.com/Developers0101/notes-android-course/raw/main/images/%D9%88%DB%8C%D9%88%20%D9%85%D8%AF%D9%84_files/image011.png)

میایم و از کلاس view model که مربوط به androidx lifecycle میشه استفاده میکنیم.

![My image](https://github.com/Developers0101/notes-android-course/raw/main/images/%D9%88%DB%8C%D9%88%20%D9%85%D8%AF%D9%84_files/image012.png)

میایم و عملیات مون رو داخل کلاس view model مون مینویسیم چون view model باعث میشه اطلاعات ما ذخیره بشه، بخاطر همین عملیات اصلی رو توش مینویسیم.

![My image](https://github.com/Developers0101/notes-android-course/raw/main/images/%D9%88%DB%8C%D9%88%20%D9%85%D8%AF%D9%84_files/image013.png)

میایم و از view model مون یه object درست میکنیم و اگه از روش های قدیمی استفاده کنیم، دارن از view model provider ها استفاده میکنن که این روش ها دیگه deprecate شدن، و بهترین روش استفاده از kotlin delegate هست.

![My image](https://github.com/Developers0101/notes-android-course/raw/main/images/%D9%88%DB%8C%D9%88%20%D9%85%D8%AF%D9%84_files/image014.jpg)

برای استفاد از kotlin delegate میایم با استفاده از by میایم و initialize ش میکنیم.

![My image](https://github.com/Developers0101/notes-android-course/raw/main/images/%D9%88%DB%8C%D9%88%20%D9%85%D8%AF%D9%84_files/image015.png)

میایم و علامت <> view models رو حذف میکنیم و الان initialize شده و ما میتونیم ازش استفاده کنیم.

![My image](https://github.com/Developers0101/notes-android-course/raw/main/images/%D9%88%DB%8C%D9%88%20%D9%85%D8%AF%D9%84_files/image016.png)

این view models  که توی activity استفاده کردیم، مربوط به همون کتابخونه ایی که به gradle اضافه کرده بودیم میشه.

![My image](https://github.com/Developers0101/notes-android-course/raw/main/images/%D9%88%DB%8C%D9%88%20%D9%85%D8%AF%D9%84_files/image017.png)

الان اومدیم وعملیات ذخیره سازی رو انجام دادیم.

![My image](https://github.com/Developers0101/notes-android-course/raw/main/images/%D9%88%DB%8C%D9%88%20%D9%85%D8%AF%D9%84_files/image018.png)

++ میاد و یه دونه یه دونه اضافه میکنه -- یه دونه یه دونه کم میکنه و با بقیه موارد و تغییر اعداد میشه بقیه ی عملیات های ریاضی رو انجام داد.

الان وقتی برنامه رو اجرا کنیم و مثلاً دکمه رو بزنیم و عدد 10 بشه، بعد گوشی رو rotate کنیم عدد 0 رو نشون میده ولی اگه دوباره دکمه رو بزنیم، عدد از ادامه و 11 رو نشون میده.

![My image](https://github.com/Developers0101/notes-android-course/raw/main/images/%D9%88%DB%8C%D9%88%20%D9%85%D8%AF%D9%84_files/image019.png)

این اتفاق بخاطر این افتاد که ما گفتیم بواسطه ی کلیک کردن بیاد و عدد رو نشون بده و اگه نمایش عدد رو علاوه بر اینکه داخل set on click مینویسیم، بیرون هم بنویسیم و بگیم همون اول که اپلیکیشن داره اجرا میشه یا داره rotate میشه عدد رو از counter بگیر، باگمون برطرف میشه.

قسمت 45

میخوایم از view model توی recycler view استفاده کنیم وقتی rotate کردیم موقعیت آیتم ها تغییر نکنه.

![My image](https://github.com/Developers0101/notes-android-course/raw/main/images/%D9%88%DB%8C%D9%88%20%D9%85%D8%AF%D9%84_files/image020.png)

یه مدل و adapter واسه recycler view درست میکنیم.

دیتای که میخوایم داخل recycler view قرار بدیم رو بصورت یک کلاس یا فایل میسازیم، که بصورت general قرار میدیم تا بتونیم توسط هر کلاس، فرگمنت یا اکتیویتی که خواستیم بهش دسترسی داشته باشیم.

یه object به اسم utils میسازیم و چیزهایی که عمومی، کاربردی و general هستن رو توش مینویسیم.

` `![My image](https://github.com/Developers0101/notes-android-course/raw/main/images/%D9%88%DB%8C%D9%88%20%D9%85%D8%AF%D9%84_files/image021.png)

میخوایم item رو مستقیما و با متد get itmes پرکنیم و نوع متد رو با مقدار بازگشتی و ازنوع mutable list ی از کلاس مدلمون درنظر میگیریم، تا آیتم هایی که پر میشن بتونیم توی recycler view, adapter و هرجایی که نیاز داریم دسترسی داشته باشیم و بتونیم استفاده کنیم.

![My image](https://github.com/Developers0101/notes-android-course/raw/main/images/%D9%88%DB%8C%D9%88%20%D9%85%D8%AF%D9%84_files/image022.png)

بعد یه متغییر جدید درست میکنیم تا آیتم هامونو داخلش بتونیم add کنیم و با mutable list of() میایم و initialize ش میکنیم و بعد پر کردن لیست itmes رو return میکنیم.

![My image](https://github.com/Developers0101/notes-android-course/raw/main/images/%D9%88%DB%8C%D9%88%20%D9%85%D8%AF%D9%84_files/image023.png)

میایم و با یه حلقه for لیستمون رو پر میکنیمو itmes هامونو داخلش add میکنیم و بهش item model مون رو میدیم و لیستمون رو پر میکنیم.

![My image](https://github.com/Developers0101/notes-android-course/raw/main/images/%D9%88%DB%8C%D9%88%20%D9%85%D8%AF%D9%84_files/image024.png)

یه کلاس view model تعریف میکنیم، چون باید اطلاعاتمون اونجا نگهداشته بشه تا زمانی که rotate میشه اطلاعاتمون بهم نریزه.

بعد یه متغییر تعریف میکنیم و اطلاعاتی که توی object utils و در متد get items داشتیم رو بهش میدیم(اگه اطلاعاتمون از سرور میومد، اینجا بهش مدلمون رو میدادیم).

توی view model اطلاعاتمون رو اگه از room بیاد یا retrofit یا هرجایی که میاد رو بهش میدیم و set میکنیم.

![My image](https://github.com/Developers0101/notes-android-course/raw/main/images/%D9%88%DB%8C%D9%88%20%D9%85%D8%AF%D9%84_files/image025.png)

بعد میایم داخل اکتیویتی مون و adapter, view model رو تعریف میکنیم.

![My image](https://github.com/Developers0101/notes-android-course/raw/main/images/%D9%88%DB%8C%D9%88%20%D9%85%D8%AF%D9%84_files/image026.jpg)

میایم adapter مون رو با view model پر میکنیم و بعد توی recycler view نشون میدیم.

وقتی اجرا میگیریم و گوشی رو rotate کنیم برای دیتا هیچ مشکلی پیش نمیاد و بدرستی آیتم هارو از ادامه نشون میده و view model بدرستی state هارو برای ما ذخیره کرد.
ویومدل خیلی سبک و کمترین فشارو، روی سخت افزار میاره.

