---
layout: default
title:  3- دیتابیس روم
nav_order: 7
---

# 3- دیتابیس روم
قسمت 4:

کلاس entity یا کلاس مدل.

دیتابیس روم اطلاعات رو در قالب table و جدول ها ذخیره میکنه و بالای اسم کلاس entity مون از @Entity استفاده میکنیم و اسم جدولمون یا table name رو بصورت ثابت یا const براش در نظر میگیریم.

داخل پوشه utils چیزهای عمومی و کاربردی رو قرار میدیم، مثل ثابت ها یا constants .

![My image](https://github.com/Developers0101/notes-android-course/raw/main/images/%D8%AF%DB%8C%D8%AA%D8%A7%D8%A8%DB%8C%D8%B3%20%D8%B1%D9%88%D9%85_files/image001.jpg)

داخل کلاس دیتابیس میایم از یک چیز یونیک و خاص مثل id استفاده میکنیم چون برای هرکاربر منحصربفرد، و تکراری نیست.

کلاس مدلمون یا entity رو بصورت data کلاس مینویسیم.

از اونجایی که id خاص و unique هست میایم و بصورت primary key تعریفش میکنیم و حتماً باید primary key استفاده کنیم و اجباری هست.

auto generate برای آپدیتش شدن اتوماتیک هست که به ازای هر کاربر یا کار جدید خودش یه دونه اضافه میکنه.

![My image](https://github.com/Developers0101/notes-android-course/raw/main/images/%D8%AF%DB%8C%D8%AA%D8%A7%D8%A8%DB%8C%D8%B3%20%D8%B1%D9%88%D9%85_files/image002.jpg)

با دستور @columnInfo میتونیم اسمی که داخل مدلمون قرار دادیم رو توی دیتابیس با یک اسم دیگه ذخیره کنیم.

قسمت 5:

دیتابیس روم 3 تا کلاس اصلی داره، که کلاس اول، کلاس مدل یا entity هست و کلاس دوم، کلاس dao که مربوط به query هست.

Query : هر عملیاتی که ما در دیتابیس مینویسیم و میتونیم از اون عملیاتها استفاده کنیم در قالب query هست مثل گرفتن یا آپدیت و دیلیت کردن اطلاعات و ... .

Dao : برای نوشتن query از interface استفاده میکنیم که dao مخفف data access object هست.

Query insert برای ذخیره کردن اطلاعات هست.

![My image](https://github.com/Developers0101/notes-android-course/raw/main/images/%D8%AF%DB%8C%D8%AA%D8%A7%D8%A8%DB%8C%D8%B3%20%D8%B1%D9%88%D9%85_files/image003.jpg)

برای اینکه در insert اگه اطلاعات کاربرا شبیه هم باشه برنامه بتونه ذخیره کنه و کرش نکنه از دستور onconflict استفاده میکنیم.

![My image](https://github.com/Developers0101/notes-android-course/raw/main/images/%D8%AF%DB%8C%D8%AA%D8%A7%D8%A8%DB%8C%D8%B3%20%D8%B1%D9%88%D9%85_files/image004.jpg)

برای نوشتن custom query ها باید از @Query استفاده کنیم.

چون میخوایم اطلاعات همه ی کاربرهارو دریافت کنیم بخاطر همین بصورت لیست مینویسیم.

هر موقعه توی دیتابیس از \* استفاده کنیم یعنی همه.

دیتابیس به این صورت که اطلاعات توی table ها ذخیره میشن و table ها میرن توی database ذخیره میشن.

نوشتن query برای برگردوندن یک چیز خاص:

![My image](https://github.com/Developers0101/notes-android-course/raw/main/images/%D8%AF%DB%8C%D8%AA%D8%A7%D8%A8%DB%8C%D8%B3%20%D8%B1%D9%88%D9%85_files/image005.jpg)

میگیم همه رو(\*) از جدول user table انتخاب کن(SELECT) جایی که(WHERE) این user id شبیه(LIKE) به این :id بود و این id رو در متد get user تعریف کردیم که با استفاده از id کل اطلاعات یک کاربرو برمیگردونه.

یعنی همه ی اطلاعات یک کاربرو باتوجه به id که بهت میدیم برگردون.

حتماً باید : رو قبل id یا هرچیزی که میزاریم باید قرار بدیم.

قسمت 6

کلاس سومی که در دیتابیس روم استفاده میکنیم، کلاس database که پایگاه داده ما هست.

کار کلاس دیتابیس این هست که میاد entity, dao رو میگیره و عملیاتی که انجام میشه رو ذخیره میکنه.

کلاس دیتابیس از ما ورودی در قالب entity میخواد که بصورت لیست میدیم و version هم میخواد.

وقتی کوچکترین تغییری هم در کلاس entity اتفاق بیفته باید حتماً یه دونه version رو ارتقا بدیم وگرنه برنامه crash میکنه، مگر اینکه تغییرات کلاس entity قبل از اولین نصب باشه که هرچی درش تغییر ایجاد کنیم مشکلی نداره:

![My image](https://github.com/Developers0101/notes-android-course/raw/main/images/%D8%AF%DB%8C%D8%AA%D8%A7%D8%A8%DB%8C%D8%B3%20%D8%B1%D9%88%D9%85_files/image006.jpg)

حتماً کلاس database باید از نوع abstract باشه.

Abstract یه جور حالت قرار داد داره، یعنی میدونیم میخوایم از این کلاس استفاده کنیم ولی نمیدونیم کجا و به چه شکلی میخوایم پرش کنیم و استفاده کنیم.

![My image](https://github.com/Developers0101/notes-android-course/raw/main/images/%D8%AF%DB%8C%D8%AA%D8%A7%D8%A8%DB%8C%D8%B3%20%D8%B1%D9%88%D9%85_files/image007.png)

میایم از کلاس room database ارث بری میکنیم.

کلاسی که abstract هست، مواردی که داخل خودش داره رو هم abstract در نظر میگیریم.

` `ما entity رو به database دادیم و بعد میایم dao رو هم بهش میدیم و  متد dao رو تعریف میکنیم و از کلاس dao ارث بری میکنیم و با استفاده از database و dao میتونیم کلیه عملیات های دیتابیس مثل ذخیره، آپدیت، دیلیت و ... رو هندل کنیم.

کلاس database میاد entity و dao رو بهم وصل میکنه.



قسمت 7

وقتی میخوایم از دیتابیس داخل کلاس هامون استفاده کنیم و اونو مقدار دهی کنیم، database builder از ما 3 تا ورودی میخواد:

![My image](https://github.com/Developers0101/notes-android-course/raw/main/images/%D8%AF%DB%8C%D8%AA%D8%A7%D8%A8%DB%8C%D8%B3%20%D8%B1%D9%88%D9%85_files/image008.jpg)

ورودی اول context ، ورودی دوم کلاس database و ورودی سوم اسم database رو میخواد که براش یه اسم داخل constants تعریف میکنیم همونطوری که برای table یا جدولمون اسم تعریف کردیم.

روم میاد اطلاعات رو در ترد بک گراند یا io انجام میده، بخاطر اینکه کاربر برای ذخیره سازی اطلاعات معطل نشه، ولی چون ما تغییرات ظاهری داریم و نیاز داریم که این اطلاعات به کاربر نشون داده بشه بهش مگیم که اجازه بده که روی ترد اصلی main یا ui هم اجرا بشه.

![My image](https://github.com/Developers0101/notes-android-course/raw/main/images/%D8%AF%DB%8C%D8%AA%D8%A7%D8%A8%DB%8C%D8%B3%20%D8%B1%D9%88%D9%85_files/image009.png)

برای اجرا شدنش روی ترد اصلی از allow main thread queries استفاده میکنیم که query های که داخل کلاس dao نوشتیم روی ترد اصلی اجرا بشه.

![My image](https://github.com/Developers0101/notes-android-course/raw/main/images/%D8%AF%DB%8C%D8%AA%D8%A7%D8%A8%DB%8C%D8%B3%20%D8%B1%D9%88%D9%85_files/image010.png)

دستور Migration برای اینکه وقتی دیتابیسمون ورژنش رو تغییر میدیم و برای اینکه وقتی، یه دیتابیس با ورژن های مختلف داریم به conflict نخوره از fallbackToDestructiveMigration استفاده میکنیم و حتی برای سمت سرور هم برای آپدیت کردن ازش استفاده میکنیم.

![My image](https://github.com/Developers0101/notes-android-course/raw/main/images/%D8%AF%DB%8C%D8%AA%D8%A7%D8%A8%DB%8C%D8%B3%20%D8%B1%D9%88%D9%85_files/image011.jpg)


چون نیاز به کلاس entity داریم میایم و اونو تعریف میکنیم برای استفاده کردن:

![My image](https://github.com/Developers0101/notes-android-course/raw/main/images/%D8%AF%DB%8C%D8%AA%D8%A7%D8%A8%DB%8C%D8%B3%20%D8%B1%D9%88%D9%85_files/image012.jpg)

وقتی از snack bar استفاده میکنیم از ما 3 تا ورودی میخواد که ورودی اول view هست دومی پیام و سومی هم زمان نمایش هست:

![My image](https://github.com/Developers0101/notes-android-course/raw/main/images/%D8%AF%DB%8C%D8%AA%D8%A7%D8%A8%DB%8C%D8%B3%20%D8%B1%D9%88%D9%85_files/image013.jpg)

وقتی میخوایم از دیتابیسمون استفاده کنیم و ورودی از entity بگیریم باید همیشه id رو برابر با 0 قرار بدیم، چون خودش auto generate هست و میاد دونه دونه اضافه میکنه و تنظیم میکنه:

![My image](https://github.com/Developers0101/notes-android-course/raw/main/images/%D8%AF%DB%8C%D8%AA%D8%A7%D8%A8%DB%8C%D8%B3%20%D8%B1%D9%88%D9%85_files/image014.png)

وقتی ورودی هامون رو از entity گرفتیم باید اونو بریزیم توی دیتابیس، که بوسیله dao به query هامون دسترسی داریم:

![My image](https://github.com/Developers0101/notes-android-course/raw/main/images/%D8%AF%DB%8C%D8%AA%D8%A7%D8%A8%DB%8C%D8%B3%20%D8%B1%D9%88%D9%85_files/image015.png)

میایم داخل query مربوط به insert اون entity رو مینویسیم.

برای بستن صفحه داخل activity از finish استفاده میکنیم.

![My image](https://github.com/Developers0101/notes-android-course/raw/main/images/%D8%AF%DB%8C%D8%AA%D8%A7%D8%A8%DB%8C%D8%B3%20%D8%B1%D9%88%D9%85_files/image016.png)


قسمت 8

وقتی داریم از lazy استفاده میکنیم میایم و بصورت مستقیم مینویسیم:

![My image](https://github.com/Developers0101/notes-android-course/raw/main/images/%D8%AF%DB%8C%D8%AA%D8%A7%D8%A8%DB%8C%D8%B3%20%D8%B1%D9%88%D9%85_files/image017.png)

و نیازی نیست که به این صورت بنویسیم و دوباره تعریفش کنیم:

![My image](https://github.com/Developers0101/notes-android-course/raw/main/images/%D8%AF%DB%8C%D8%AA%D8%A7%D8%A8%DB%8C%D8%B3%20%D8%B1%D9%88%D9%85_files/image018.png)

وقتی برنامه رو اجرا میکنیم و اطلاعات جدید وارد میکنیم، موقع نمایش تا برنامه رو نبندیم و دوباره باز نکنیم نشون نمیده، چون کدها در on create نوشته شده:

![My image](https://github.com/Developers0101/notes-android-course/raw/main/images/%D8%AF%DB%8C%D8%AA%D8%A7%D8%A8%DB%8C%D8%B3%20%D8%B1%D9%88%D9%85_files/image019.png)

و از اونجایی که on create فقط یکبار صدا زده میشه، کدهارو نشون نمیده، بخاطر همین میایم و کدرو داخل on resume مینویسیم:

![My image](https://github.com/Developers0101/notes-android-course/raw/main/images/%D8%AF%DB%8C%D8%AA%D8%A7%D8%A8%DB%8C%D8%B3%20%D8%B1%D9%88%D9%85_files/image020.png)

ولی روش بهینه استفاده از live data هست.

برای اینکه وقتی اطلاعات نمایش داده میشه نحوه نمایش آیتم هارو تغییر بدیم، داخل کلاس dao از order استفاده میکنیم:

![My image](https://github.com/Developers0101/notes-android-course/raw/main/images/%D8%AF%DB%8C%D8%AA%D8%A7%D8%A8%DB%8C%D8%B3%20%D8%B1%D9%88%D9%85_files/image021.jpg)

DESC یعنی بر اساس آخرین item یا جدیدترین آیتم نشون بده.

![My image](https://github.com/Developers0101/notes-android-course/raw/main/images/%D8%AF%DB%8C%D8%AA%D8%A7%D8%A8%DB%8C%D8%B3%20%D8%B1%D9%88%D9%85_files/image022.png)

بصورت پیشفرض روی ASC قرار داره که یعنی از اولین یا قدیمی ترین آیتم نمایش بده که نیازی به نوشتنش نیست.

قسمت 9

برای کلیک کردن روی آیتم های ریسایکلرویو میشه هم از کلیک روی خود adapter استفاده کرد و هم از interface.

![My image](https://github.com/Developers0101/notes-android-course/raw/main/images/%D8%AF%DB%8C%D8%AA%D8%A7%D8%A8%DB%8C%D8%B3%20%D8%B1%D9%88%D9%85_files/image023.png)

چون تو adapter ، start activity رو نداره میایم از context استفاده میکنیم.

چون توی dao از id استفاده کردیم و بواسطه id به کلیه اطلاعات کاربر دسترسی داریم id رو هم همراه intent میفرستیم.

Ctrl + shift + u برای بزرگ و کوچیک کردن کلمات هست.

برای دریافت اطلاعات با intent از extras استفاده میکنیم و با ؟ و let یعنی مطمئن میشیم که چیزی که دریافت میکنیم خالی نیست:

![My image](https://github.com/Developers0101/notes-android-course/raw/main/images/%D8%AF%DB%8C%D8%AA%D8%A7%D8%A8%DB%8C%D8%B3%20%D8%B1%D9%88%D9%85_files/image024.png)

Let برای چک کردن null .

الان ما id رو داریم و میتونیم توی query های مربوط به خودش ازش استفاده کنیم.

برای اینکه id که انتخاب شده در لیستمون از قبل مقداری داره و اون مقادیرو به کاربر نشون بدیم 2 تا متغییر تعریف میکنیم و بواسطه id از database اون مقادیرو میگیریم و نشون میدیم:

![My image](https://github.com/Developers0101/notes-android-course/raw/main/images/%D8%AF%DB%8C%D8%AA%D8%A7%D8%A8%DB%8C%D8%B3%20%D8%B1%D9%88%D9%85_files/image025.png)

![My image](https://github.com/Developers0101/notes-android-course/raw/main/images/%D8%AF%DB%8C%D8%AA%D8%A7%D8%A8%DB%8C%D8%B3%20%D8%B1%D9%88%D9%85_files/image026.png)

ما برای text view از text استفاده میکنیم و برای edit text حتماً باید از set text استفاده کنیم چون از نوع editable هست و خودش نیاز به یکسری تغییرات داره،که set text انجام میده:

![My image](https://github.com/Developers0101/notes-android-course/raw/main/images/%D8%AF%DB%8C%D8%AA%D8%A7%D8%A8%DB%8C%D8%B3%20%D8%B1%D9%88%D9%85_files/image027.png)

حالا مقادیر گرفته شده رو در edit text نشون میدیم و میتونیم آپدیت یا حذفش کنیم:

![My image](https://github.com/Developers0101/notes-android-course/raw/main/images/%D8%AF%DB%8C%D8%AA%D8%A7%D8%A8%DB%8C%D8%B3%20%D8%B1%D9%88%D9%85_files/image028.png)

از finish استفاده میکنیم چون وقتی کاربر اطلاعات رو پاک میکنه دیگه اون اطلاعات در database نیست و اگه صفحه بسته نشه و کاربر دوباره چیزی وارد کنه برنامه کرش میکنه.

![My image](https://github.com/Developers0101/notes-android-course/raw/main/images/%D8%AF%DB%8C%D8%AA%D8%A7%D8%A8%DB%8C%D8%B3%20%D8%B1%D9%88%D9%85_files/image029.jpg)

نحوه آپدیت کردن اطلاعات.



