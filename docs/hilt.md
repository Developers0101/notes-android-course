---
layout: default
title: 7- دگر-هیلت
nav_order: 8
--- 

# 7- استفاده از Dagger-Hilt

قسمت 31

Hilt : هیلت جزء یکی از کتابخونه های android بحساب میاد که کارهای تزریق وابستگی رو برای ما انجام میده و نسخه ی ارتقا پیدا کرده ی dagger هست.

تزریق وابستگی یا Dependency Injection یا بصورت مخفف DI : کتابخونه hilt بهترین کتابخونه در زمینه تزریق وابستگی هست.

تزریق وابستگی یعنی اینکه چیزهای که بهم وابسته هستن، مثل متغییرها، متدها، کلاس ها، سازنده ها، و ... که بهم وابسته هستن، بیایم و یک طوری وابستگی هاشونو تامین بکنیم، بدون اینکه خودمون دستی همه ی اونارو وارد کلاس بکنیم.

مثلاً یک کلاس user داریم که قرار اطلاعات یوزرو بگیره و اطلاعات و لیست پست هاشو ذخیره کنه، مثل صفحه ی پروفایل اینستاگرام که شامل اطلاعات، عکس، پست و فالوور و ... هست، این صفحه به یک مدلی نیاز داره که در قالب این مدل، اطلاعات مربوط به اون user فرستاده میشه که این اطلاعات شامل مثلاً عکس، اسم، پست و فالوور و ... هست، برای اینکه ما بتونیم در صفحه ی پروفایل اطلاعات کاربرو نشون بدیم، به چند چیز وابسته هستیم که این وابستگی شامل:1- کلاسی که میاد و اطلاعات رو برای ما میفرسته 2- ارتباط با اینترنت، که از طریق اینترنت اطلاعات برای ما فرستاده بشه 3- دیتابیس.

که ما در اینجا به بخش های مختلف و چیزهای مختلف وابستگی داریم، اگه ما بخوایم همه ی این وابستگی هارو خودمون تامین بکنیم و دستی همه چیز رو قرار بدیم، و مثلاً یکی از کلاس هایی که داریم استفاده میکنیم بیاد و یه فیلدی اضافه بکنه و یه تغییر ایجاد بکنه، مجبوریم همه ی جاهایی که از این کلاس استفاده کردیم بیایم و نشون بدیم و اعمال کنیم یا مثلاً:

` `نیاز داریم که کیف پول کاربرو در صفحه ی پروفایل، صفحه ی اول، صفحه ی سبد خرید، و تو مرحله ی نهایی نشون بدیم، که نیاز به یه چیزی داریم که توی چندین صفحه اطلاعات مارو تامین میکنه، و اگه مدلی که داریم تغییر کنه مجبوریم توی همه ی کلاس ها، بیایم و اون تغییرات رو اعمال کنیم، که برنامه نویسی اصولی نیست.

وابستگی یعنی اینکه برای نشون دادن یا انجام دادن یکسری اطلاعاتی نیاز داریم که یکسری چیزهارو تامین کنیم، که این اطلاعات از یک کلاس دیگه تامین میشه، که این یعنی وابسته شدن بهم دیگه.

از تزریق وابستگی استفاده میکنیم تا کدها منظم تر، مرتب تر و وابستگی ها بهم کمتر باشه، وهر تغییراتی که میخوایم، یک کلاس بیاد انجام بده و با این تغییرات، در کلاس های دیگه که ازش استفاده میکنن اوکی بشه.

یه مثال از دنیای واقعی برای تزریق وابستگی: مثلاً یه کارخونه ماشین داریم که همه چیز رو از 0 تا 100 خودش میزنه و همه ی کارهارو یک جا و در یک فضا انجام میده، اگه یه قسمت از کارخونه دچار مشکل و آتش سوزی بشه کل کارخونه نابود میشه چون همه چیز بهم وابسته هستن، ولی اگه هرکدوم از قسمت های کارخونه مجزا از هم باشه، اگه واسه ی یه قسمت مشکلی پیش بیاد، به بقیه ی قسمت ها آسیبی نمیرسه.

` `تزریق وابستگی هم دقیقاً به همین صورت هست و ما میایم و کلاس ها و هرچیزی که بهش وابستگی داره، مثلاً اون صفحه یا پروژه یا اون بخشی که میخوایم داخلش کدمون رو بزنیم و تو جاهای مختلف تعریف میکنیم، میایم و با روش های تزریق وابستگی تزریقشون میکنیم به اون صفحه ی مورد نظرمون یا پروژه مون، و وقتی این کلاس رو تغییر بدیم دیگه نیازی نیست همه جاهایی که داریم از این کلاس استفاده میکنیم بیایم و تغییرش بدیم و خودش بصورت اتوماتیک اعمال میشه.

بطور کلی ما 2 نوع تزریق وابستگی داریم: 1- دستی: که بایه همه ی عملیات هارو خودمون بیایم و دستی تزریق کنیم و تامین کنیم وابستگی هارو، که فوق العاده سخت و پیچیده و زمانبر و باعث شلوغ شدن کدها میشه و کلی کلاس اضافی بوجود میاره برای تامین وابستگی و نیاز به دیزاین پترن های مختلف مثل factory ، observe و adapter و چیزهای مختلف دیگه ایی رو کامل بدونیم که بتونیم دستی وابستگی هارو تزریق کنیم  2- اتوماتیک: که توسط یکسری کتابخونه های میتونیم استفاده کنیم.

معروفترین کتابخونه های تزریق وابستگی : 1- dagger 2- coin 3- kodein 4- dagger-hilt 

Dagger : dagger یکی از بزرگترین، سخت ترین و واقعاً پیچیده ترین کتابخونه های مربوط به dependency injection یا تزریق وابستگی توی اندروید هست و معروف به سرطان اندروید.

Kodein : کودئین مربوط به kotlin و توی java نمیشه استفاده کرد و کمتر از 10% مورد استفاده قرار میگیره.

Koin : کوین هم مثل کودئین مربوط به kotlin و توی java نمیشه ازش استفاده کرد ولی از kodein بهتر.

Koin و kodein وابستگی رو برای ما تزریق میکنن ولی برای ما 100% عملیات تزریق وابستگی رو برای ما انجام نمیدن و تقریباً شبه تزریق وابستگی رو انجام میدن، ولی این شبه تزریق رو ما برنامه نویس ها یا کاربرا لمس نمیکنیم و توی خود عملیات اپلیکیشن هست، ولی dagger و hilt تزریق وابستگی رو بصورت 100% برای ما انجام میدن.

Hilt آخرین تکنولوژی که برای dependency injection اومده و مربوط به خود گوگل.

Hilt خودش به تنهایی یه تزریق وابستگی نیست و عین koin یه چیز مجزا نیست، و نسخه ی ارتقا یافته ی dagger هست و خیلی سبک، قدرتمند و سرعت خیلی بالایی داره، و  dagger در  واقع parent هیلت بحساب میاد.

سازوکار و کارکرد کلی hilt : هیلت وابستگی هارو با Annotation ها یا حاشیه نویسی انجام میده.

و اونهایی که درشون از علامت @ استفاده میکنیم میشه annotation یا حاشیه نویسی که در رتروفیت مثل @GET یا @Post استفاده میکردیم.

` `بصورت کلی باید hilt رو داخل کلاس application معرفی کنیم، که application بطور کلی hilt رو وارد سازوکار application کنه.

Hilt رو باید در قالب یکسری گراف ها درنظر بگیریم، که با این کار، اون گراف ها و چیزهایی که دارن باهم کار میکنن رو وارد application مون میکنیم، که اپلیکیشن مون با اون تزریق وابستگی هایی که hilt داره باهاش کار میکنه، کاملاً سازگاری پیدا کنه.

و درنهایت برای اون کاری که میخوایم انجام بدیم، مثلاً برای متغییر، متد، کلاس، context ، و برای هرچیزی که وابسته هستیم بهش که بتونیم یکسری از کارهامونو انجام بدیم، توسط annotation هایی که بالای اون بخش(متغییر، متد، کلاس و ...) قرار میدیم و بصورت کاملاً اتوماتیک میره اون گراف رو تکمیل میکنه.

گراف: گراف های یکسری نمودارهای خاصی که بهم مرتبط هستن:

![My image](https://github.com/Developers0101/notes-android-course/raw/main/images/%D9%87%DB%8C%D9%84%D8%AA_files1/image001.jpg) ![My image](https://github.com/Developers0101/notes-android-course/raw/main/images/%D9%87%DB%8C%D9%84%D8%AA_files1/image002.png)

Hilt کارهارو در حالت گراف، بصورت منظم انجام میده وشکل میده و set میکنه برامون.



قسمت 32

Hilt به کمک Annotation ها میاد برای ما تزریق وابستگی هارو انجام میده.

انواع Annotation یا حاشیه نویسی در هیلت:

![My image](https://github.com/Developers0101/notes-android-course/raw/main/images/%D9%87%DB%8C%D9%84%D8%AA_files1/image003.jpg)

1- Hilt Android App 2- Android Entry Point 3- inject 4- View Model inject (که نیاز به کتابخونه های مربوط به view model داره) 5- Module 6- install in 7- Scops 8- Provides   9- Binds 10- Context (که شامل Application Context – Activity Context میشه)           12- Qualifier (و Named)

![My image](https://github.com/Developers0101/notes-android-course/raw/main/images/%D9%87%DB%8C%D9%84%D8%AA_files1/image004.jpg)

Hilt android app : برای اینکه پروژه بتونه hilt رو بشناسه و داخل اون گراف hilt قرار بگیره و کارهارو انجام بده، باید به کلاس application مون اضافه بشه.

![My image](https://github.com/Developers0101/notes-android-course/raw/main/images/%D9%87%DB%8C%D9%84%D8%AA_files1/image005.png)

باید این annotation رو به کلاس application اضافه کنیم و حتماً باید کلاس application مون رو توی فایل manifest مون تعریف کنیم.

![My image](https://github.com/Developers0101/notes-android-course/raw/main/images/%D9%87%DB%8C%D9%84%D8%AA_files1/image006.jpg)

Android entry point : باید بالای activity یا فرگمنت مون قرار بدیم، تا بتونیم وابستگی هارو توسط hilt بهش تزریق کنیم.

![My image](https://github.com/Developers0101/notes-android-course/raw/main/images/%D9%87%DB%8C%D9%84%D8%AA_files1/image007.png)

![My image](https://github.com/Developers0101/notes-android-course/raw/main/images/%D9%87%DB%8C%D9%84%D8%AA_files1/image008.jpg)

Inject : بوسیله ی inject میتونیم وابستگی های مختلف رو تزریق کنیم، که انواع مختلفش: میتونیم داخل سازنده کلاس یا متغییر ازش استفاده کنیم.

![My image](https://github.com/Developers0101/notes-android-course/raw/main/images/%D9%87%DB%8C%D9%84%D8%AA_files1/image009.png)

نحوه استفاده از inject بعنوان سازنده کلاس یا constructor .

هروقت میخوایم در هر کلاسی از injection ها و تزریق وابستگی استفاده کنیم، حتماً حتماً باید constructor یا سازنده داشته باشه و قبل خود constructor میایم و چیزهای مربوط به تزریق وابستگی رو استفاده میکنیم و قرار میدیم.

![My image](https://github.com/Developers0101/notes-android-course/raw/main/images/%D9%87%DB%8C%D9%84%D8%AA_files1/image010.png)

نحوه استفاده از inject بعنوان متغییر که یه نمونه از adapter ساختیم.

وقتی از inject توی متغییرها استفاده میکنیم به هیچ عنوان نباید بصورت private تعریف بشن وگرنه نمیتونن وابستگی رو برای ما تزریق کنن.

![My image](https://github.com/Developers0101/notes-android-course/raw/main/images/%D9%87%DB%8C%D9%84%D8%AA_files1/image011.jpg)

Module : ماژول درواقع یک فایله، که ما میتونیم وابستگی های مختلفی که نیاز داریم رو توش، "قرار بدیم provide  یا مهیا" کنیم.

مثلاً یه وابستگی داریم که میخوایم داخلش اطلاعات کاربرو نگهداریم، یه فایل دیگه داریم که وابستگی های مربوط به اینترنت مثل رتروفیت و ok http داخلش قرار داره و یه وابستگی دیگه داریم که مربوط به کارهای دیتابیس میشه و میاد دیتابیس رو تعریف میکنه(مثلاً، بجای تعریف کردن چندباره database که تو قسمت آموزش دیتابیس، 3 بار تعریفش کرده بودیم و اصولی نبود، واگه نیاز به تغییر داشت باید همه ی جاها کدرو تغییر میدادیم).

ما وابستگی هارو در قالب module ها میایم تامین میکنیم و یه فایلی درست میکنیم به اسم module و وابستگی های مختلف رو داخل اون درست میکنیم یا مهیا یا provide میکنیم.

![My image](https://github.com/Developers0101/notes-android-course/raw/main/images/%D9%87%DB%8C%D9%84%D8%AA_files1/image012.png)

و میایم و بالای اون کلاس یا فایلی که داریم از @Module استفاده میکنیم.

![My image](https://github.com/Developers0101/notes-android-course/raw/main/images/%D9%87%DB%8C%D9%84%D8%AA_files1/image013.jpg)

Install in : میاد محدوده اجرا شدن اون ماژول (Module) رو برای ما مشخص میکنه که این ماژول میتونه singleton باشه.

![My image](https://github.com/Developers0101/notes-android-course/raw/main/images/%D9%87%DB%8C%D9%84%D8%AA_files1/image014.png)

ما singleton رو یکبار تعریف میکنیم و در طول چرخه ی حیات اپلیکیشن تعریف میشه و میتونیم مدام ازش استفاده کنیم و تند تند و پشت هم تعریف نمیشه.

و یا میتونیم install in رو در قالب lifecycle activity تعریف کنیم ، و بگیم تا زمانی که اکتیویتی ما موجود هست و بسته نشده، کنسل و stop یا destroy نشده، اون ماژول هایی که قرار دادیم کارایی دارن و اگه اکتیوتی ما بسته شد و یه اکتیویتی دیگه باز شد این ماژول ما از بین میره و یکبار دیگه ساخته میشه.

install in برای ما محدوده ی اجرا شدن ماژول مون رو مشخص میکنه که lifecycle ش تو چه محدوده ایی کاربرد داره و میتونه آیتم هامون رو برامون بسازه و در اختیار دیگر کلاس ها یا فایل ها یا هرچیزی که داریم قرار بده.

![My image](https://github.com/Developers0101/notes-android-course/raw/main/images/%D9%87%DB%8C%D9%84%D8%AA_files1/image015.jpg)

Scops : scops برای ما اون محدوده ی اجرا شدن رو برای ما مشخص میکنه، مثلاً میگه این کلاسی که داریم باید در این محدوده اجرا بشه، مثلاً میگیم چیزهایی که میخواد تزریق بشه بصورت singleton باشه، در قالب اکتیویتی باشه، در قالب view باشه یا در محدوده ی fragment باشه یا هرچیز دیگه ایی.

ما بوسیله ی scops میتونیم اون چیزهایی که میخوایم به تنهایی provide یا مهیاشون کنیم برای وابستگی ها، میتونیم بگیم:

Install in برای کل ماژول بود و بازه یا محدوده ی اجرا شونده کل ماژول(Module) رو برای ما مشخص میکنه و scops به تنهایی محدوده ی اون یه دونه المان یا چیزی که در قالب ماژول استفاده کردیم رو مشخص میکنه، مثلاً اون چیزی که تعریف کردیم در محدوده ی اکتیویتی یا فرگمنت باید کار بکنه و اگه چرخه ی حیاتشون تموم شد بیاد و این رو هم از بین ببره و اگه یه اکتیویتی دیگه بوجود اومد دوباره از اول شروعش کن.

![My image](https://github.com/Developers0101/notes-android-course/raw/main/images/%D9%87%DB%8C%D9%84%D8%AA_files1/image016.png)

در واقع این fun provide user info در داخل ماژول قرار گرفته چون همه ی چیزهایی که میخوایم تامین کنیم در داخل Module قرار میگیرن.

![My image](https://github.com/Developers0101/notes-android-course/raw/main/images/%D9%87%DB%8C%D9%84%D8%AA_files1/image017.jpg)

انواع Scope ها: ترتیب قرار گیری scop ها به این صورت هست و این ترتیب مهم.

![My image](https://github.com/Developers0101/notes-android-course/raw/main/images/%D9%87%DB%8C%D9%84%D8%AA_files1/image018.png)

چیزهایی که توی این جدول component دارن مثل  singleton component یا Activity Retained component یا service component و بقیه موارد:

![My image](https://github.com/Developers0101/notes-android-course/raw/main/images/%D9%87%DB%8C%D9%84%D8%AA_files1/image019.png)

مربوط میشن به install in .

![My image](https://github.com/Developers0101/notes-android-course/raw/main/images/%D9%87%DB%8C%D9%84%D8%AA_files1/image020.png)

چیزهایی که component ندارن و تنهایی هستن مثل @Singleton ، @Service Scoped یا @Activity Retained Scoped و بقیه مواردش:

![My image](https://github.com/Developers0101/notes-android-course/raw/main/images/%D9%87%DB%8C%D9%84%D8%AA_files1/image021.png)

مربوط میشن به چیزهایی که ما در قالب ماژول داریم ازشون استفاده میکنیم و اینا مربوط میشن به scope یی که داخل فایل ماژول میخوایم ازشون استفاده کنیم. 

![My image](https://github.com/Developers0101/notes-android-course/raw/main/images/%D9%87%DB%8C%D9%84%D8%AA_files1/image022.png)

اگه میخوایم از singleton برای ماژولمون استفاده کنیم باید از @Singletone استفاده کنیم و اگه بخوایم برای install in استفاده کنیم باید بصورت singleton component باشه.

سرویس ها: وقتی یه سرویسی رو اجرا کردیم و اون service داره توی پسزمینه یه سری کارهای مربوط به خودشو انجام میده و service که destroy شد این وابستگی ها هم destroy میشه، و همینطور میشه برای activity یا view model استفاده کرد.

حتی میشه وابستگی رو در قالب یک view درست کنیم و وقتی که اون view از بین رفت، وابستگی ما هم از بین بره و وقتی دوباره view ساخته شد وابستگی مارو تامین کنه.

![My image](https://github.com/Developers0101/notes-android-course/raw/main/images/%D9%87%DB%8C%D9%84%D8%AA_files1/image023.jpg)


Provides : وابستگی های مارو برامون مهیا میکنه، تامین میکنه.

مثلاً توی رتروفیت که استفاده کرده بودیم اومدیم از base url ، client برای تنظیمات اختصاصی و از gson برای تبدیل کردن json استفاده کردیم که رتروفیت ما 3 تا وابستگی داشت: 1- base url 2- gson 3- client ، که ما توسط provides میتونیم این وابستگی هارو مهیا و تامین کنیم، برای چیزی که میخواد ازشون استفاده کنه.

![My image](https://github.com/Developers0101/notes-android-course/raw/main/images/%D9%87%DB%8C%D9%84%D8%AA_files1/image024.jpg)

Binds : بایندز هم از نظر سازوکار عین provides هست، با این تفاوت که provides مقدار میگیره ولی binds بصورت abstract هست و همون اول مقدار نمیگیره:

![My image](https://github.com/Developers0101/notes-android-course/raw/main/images/%D9%87%DB%8C%D9%84%D8%AA_files1/image025.png)



داخل provides میتونیم از =(initialize کردن) استفاده کنیم یا حتی میتونیم از { } بسته استفاده کنیم و return کنیم، و provides برای اینجور مواقع استفاده میشه که اون چیز داره تعریف میشه.

![My image](https://github.com/Developers0101/notes-android-course/raw/main/images/%D9%87%DB%8C%D9%84%D8%AA_files1/image026.png)

ولی بعضی وقتها ما میخوایم از interface ها استفاده کنیم یا از abstract class ها استفاده کنیم، چون الان نمیدونم به چه صورت میخوایم استفاده کنیم، و بعد در موقعی که نیاز شد میاد و تعریف میشه.

در اینجور مواقع که ما اون رو کامل تعریف نمیکنیم، و میخوایم در قالب abstract استفاده کنیم میایم و از @Binds استفاده میکنیم.

![My image](https://github.com/Developers0101/notes-android-course/raw/main/images/%D9%87%DB%8C%D9%84%D8%AA_files1/image027.jpg)

Qualifier و Named : مثلاً ما 2 string داریم یه جا به اسم Mohammad و جای دیگه به اسم Mp و میخوایم اینارو به کلاسمون تزریق کنیم، زمانی که میخوایم تزریق کنیم نمیدونه که کدوم string رو باید بگیره، میره در کل پروژه و میبینه کجا یه string در قالب dependency injection یا تزریق وابستگی تامین شده، مثلاً string Mohammad و بعد اونو به ما میده ولی ما string Mp رو میخواستیم که از Qualifier یا Named استفاده میکنیم.

![My image](https://github.com/Developers0101/notes-android-course/raw/main/images/%D9%87%DB%8C%D9%84%D8%AA_files1/image028.jpg)

یا مثلاً برای retrofit ، ممکن 2تا تنظیمات مختلف برای رتروفیت داشته باشیم، چون پیش میاد و ما از جاهای مختلف api میگیریم، نیاز داریم که چیزهای مختلفی هم برای رتروفیت داشته باشیم و 2 تا تنظیمات برای api client در رتروفیت داشته باشیم توسط Qualifier یا Named میایم و برای اون وابستگی که میخوایم تزریقش کنیم یک اسم بخصوص درنظر میگیریم و هرجا که میخوایم استفاده کنیم توسط همین اسم میاد و وابستگی رو برای ما تزریق میکنه.

مثلاً رتروفیتی داریم که داخلش 2 تا api داریم یکی برای فیلم و یکی برای آب و هوا که میایم به هرکدوم یه اسم میدیم و با این اسم میتونیم وابستگی مورد نظرمون روتزریق کنیم.

از اسمی که استفاده میکنیم باید unique منحصربفرد و خاص باشه چون در غیر اینصورت اگه 2تا چیز مشابه هم تعریف بشه موقع تزریق وابستگی به مشکل میخوریم.



قسمت 33

![My image](https://github.com/Developers0101/notes-android-course/raw/main/images/%D9%87%DB%8C%D9%84%D8%AA_files1/image029.png)

برای اینکه بتونیم از hilt استفاده کنیم این 2تا کتابخونه رو به قسمت dependency های gradle module اضافه میکنیم.

![My image](https://github.com/Developers0101/notes-android-course/raw/main/images/%D9%87%DB%8C%D9%84%D8%AA_files1/image030.png)

چون توی dependency از kapt استفاده کردیم میایم و توی plugin هم kotlin kapt رو قرار میدیم و باید hilt رو هم به plugin اضافه کنیم.

![My image](https://github.com/Developers0101/notes-android-course/raw/main/images/%D9%87%DB%8C%D9%84%D8%AA_files1/image031.jpg)

بعد این خط کد رو هم میایم و به gradle project یا اصلی مون اضافه میکنیم.

ما کلاً 2 تا gradle داریم که یکی در قالب ماژول که میشه gradle module  که همه ی کتابخونه ها و dependency هارو بهش اضافه میکنیم و دومی هم میشه gradle project که هرچیزی که مربوط به کل پروژه میشه رو اضافه میکنیم.

![My image](https://github.com/Developers0101/notes-android-course/raw/main/images/%D9%87%DB%8C%D9%84%D8%AA_files1/image032.png)

ما اینجا چندین gradle module داریم ولی کلاً فقط یه gradle project داریم.

وقتی میخوایم از hilt استفاده کنیم باید اونو تو کلاس application تعریف کنیم.

کلاس application کلاسی هست که ما میتونیم داخلش یکسری تنظیمات کلی تر، عمومی تر و general تر که مربوط به این اپلیکیشن ما میشه رو توش قرار میدیم و روی کل اپلیکیشنمون اعمال میشه و اسمش رو My App گذاشتیم که میتونیم هر اسم دلخواه که خواستیم روش بزاریم.

مثلاً برای اعمال فونت روی کل پروژه میتونیم از calligraphy توی کلاس application استفاده کنیم و روی کل پروژه اعمال میشه، یا بخوایم از firebase ها استفاده کنیم و یا ... رو تو کلاس application تعریف میکنیم.

![My image](https://github.com/Developers0101/notes-android-course/raw/main/images/%D9%87%DB%8C%D9%84%D8%AA_files1/image033.png)

میایم و کلاس My app مون از کلاس Application مون ارث بری میکنیم.

با @Hilt Android App میاد و hilt رو به کل اپلیکیشن ما میشناسونه.

![My image](https://github.com/Developers0101/notes-android-course/raw/main/images/%D9%87%DB%8C%D9%84%D8%AA_files1/image034.png)

بعد از این که کلاس application رو ساختیم باید اونو توی manifest اونو تعریف کنیم.

و داخل تگ application با name میایم و کلاس application مون رو بهش میدیم و با name هرچندتا که کلاس application داشته باشه رو نشون میده.

![My image](https://github.com/Developers0101/notes-android-course/raw/main/images/%D9%87%DB%8C%D9%84%D8%AA_files1/image035.png)

بعد اینکار کلاس application ما جزء تنظیمات عمومی کل اپلیکیشن شده و hilt رو هم میشناسه.

![My image](https://github.com/Developers0101/notes-android-course/raw/main/images/%D9%87%DB%8C%D9%84%D8%AA_files1/image036.png)

اگه داخل set content view از binding. root استفاده نکنیم، هر view ایی که ست کنیم، مثلاً بواسطه ی کلیک روی یک دکمه هیچ اتفاقی نمیفته و عملاً view ها کار نمیکنن.

کاری که میخوایم انجام بدیم اینه که، یک text view داریم که میخوایم داخل این text view یه string رو نشون بدیم، پس ما یه وابستگی داریم و این text view باید یه string یی رو بیاره و این string توی یه کلاس دیگه ایی هست، مثلاً یه کلاس user که قرار اطلاعات از اونجا بیاد، پس ما یه وابستگی داریم که باید string رو از یه کلاس دیگه بگیریم و توی این text view نشون بدیم.

ما میایم و وابستگی هارو توی یه کلاس یا فایل به اسم module مینویسیم.

![My image](https://github.com/Developers0101/notes-android-course/raw/main/images/%D9%87%DB%8C%D9%84%D8%AA_files1/image037.png)


و یه پوشه درست میکنیم به اسم di که مخفف dependency injection هست و ما ممکن تو یه پروژه کلی di های مختلف داشته باشیم بخاطر همین بهتر براش یه پوشه بسازیم و هرچقدر که ماژول داریم رو داخل این پوشه di قرار بدیم تا یک کلاس منسجم و جامع باشه.

ما نیاز به module داریم، ماژول میاد چیزهایی که provide(provide میومد وابستگی هارو برای ما مهیا میکرد) هستن رو، میاد وابستگی هاش رو برای ما تامین میکنه و هرچیزی که میخوایم وابستگی هارو برای ما provide یا مهیا کنه رو داخلش مینویسیم، پس نیاز داریم به یک ماژولی که این وابستگی که ما داریم و میخواد یک اسمی رو برای ما بفرسته رو مهیا یا provide کنیم، که اینکار توسط یک ماژول به هر اسم دلخواهی که خواستیم انجام میشه.

![My image](https://github.com/Developers0101/notes-android-course/raw/main/images/%D9%87%DB%8C%D9%84%D8%AA_files1/image038.png)

میایم و داخل پوشه di و یه Object به اسم (Main Module) دلخواه میسازیم.

![My image](https://github.com/Developers0101/notes-android-course/raw/main/images/%D9%87%DB%8C%D9%84%D8%AA_files1/image039.png)

با استفاده از @Module کلاس یا فایل ما تبدیل میشه به ماژول و بهتر که از نوع object باشه.

![My image](https://github.com/Developers0101/notes-android-course/raw/main/images/%D9%87%DB%8C%D9%84%D8%AA_files1/image040.png)

زمانی که میخوایم از module استفاده کنیم باید محدوده ی اجرایی ماژول رو هم مشخص کنیم، که میایم از @install in استفاده میکنیم و بعد داخلش محدوده ماژول رو با sigletone مشخص میکنیم.

Singleton یعنی تا زمانی که این اپلیکیشن ما اجراست یکبار تعریفش کن و یک object یی ازش بساز و همش اونو به ما بده و کلاً یکبار تو رم تعریف میشه.

الان object Main module ما در قالب singleton برای ما ساخته میشه.

فایل main module وابستگی هارو برای ما تامین میکنه.

ما یه وابستگی داریم که میخوایم اسممون رو توش نشون بدیم.


![My image](https://github.com/Developers0101/notes-android-course/raw/main/images/%D9%87%DB%8C%D9%84%D8%AA_files1/image041.png)

میایم و براش یه function میسازیم، و اکثراً چون مهیا یا provide میکنه، چیزهایی که توی module مینویسن با provide شروع میشه، ولی در کل نامگذاری متدش دلخواه.

چون از نوع provide هست بهش مقدار دادیم وگرنه اگه نوعش رو نمیدونستیم و بصورت abstract تعریف میشد و مقدار نداشت باید از نوع bind تعریف میکردیم.

مثلاً رتروفیت یا روم چون میدونیم به چه صورتی میخوایم تعریف کنیم بصورت provide مینویسیم.

![My image](https://github.com/Developers0101/notes-android-course/raw/main/images/%D9%87%DB%8C%D9%84%D8%AA_files1/image042.png)

هرچیزی که میخوایم ماژول برامون مهیا کنه از @Provides استفاده میکنیم.

این الان برامون مهیا شده و ما میتونیم همه جا ازش استفاده کنیم.

خیلی راحت و دیگه نیازی به تعریفش نیست ولی اگه از حالت عادی وبدون تزریق وابستگی استفاده میکردیم، باید میومدیم و یک کلاسی رو تعریف میکردیم، بعد داخل کلاس اون متغییر مون(Mohammad Mp) یا متد یا هرچیز دیگه ایی رو مقداردهی میکردیم، بعد باید توی اکتیویتی یا فرگمنت اون کلاسمون رو تعریف میکردیم، و بعد مقداردهی یا initialize ش میکردیم و بعدش میتونستیم بهش دسترسی داشته باشیم، حالا به هردلیلی ورودی های کلاسمون تغییر میکرد، باید میومدیم و توی قسمتی که ازش استفاده کردیم و initialize ش کردیم، تغییرش میدادیم.

الان provides در دسترسمون هست ولی هنوز نمیتونیم ازش استفاده کنیم.

ما علاوه بر اینکه میتونیم محدوده ی اجرایی ماژول رو مشخص کنیم، محدوده ی اجرایی اون چیزی هم که داره تزریق میشه رو هم میشه مشخص کنیم، و اگه نیاز string ما توی کل اپلیکیشن ما یکبار اجرا بشه یا نه، یا به ازای هر اکتیویتی، هر view model یا هر فرگمنت ، یا به ازای هر service ، این string ما یکبار ساخته بشه یا نه، مثلاً توی صفحه ی main به این string مون نیاز داریم و دسترسی داریم آیا اگه به صفحه ی detail بریم هم نیاز داریم به این string دسترسی داشته باشیم.

مثلاً retrofit رو یکبار تعریف میکنیم برای کل اون زمانی که اپلیکیشن مون اجراست و دیگه براش تنظیمات مختلف تعریف نمیکنیم.

مثلا توی متد provide user name اسمی که داریم تغیییر نمیکنه و یکبار مینویسیم، ولی زمانی میخوایم تغییر کنه و مجدداً ازش ساخته بشه که، دیگه نمیخوایم به object قبلیش دسترسی داشته باشیم، مثلاً یکسری اطلاعات جدید رو داریم میسازیم روش و میخوایم این object یکبار دیگه از اول ساخته بشه، وقتی میخوایم یکبار دیگه از اول برای صفحه ی خاصی ساخته بشه، مثلاً میایم میگیم این object provide user name ، توی activity main یه بار ساخته بشه، زمانی که میریم توی detail ، یکبار دیگه هم اونجا ساخته بشه حالا با یکسری چیزهای دیگه.

برای همین وقتی میخوایم محدوده اجرایی یک متغییر یا متد رو میخوایم مشخص کنیم باید ببینیم همیشگی و توی کل اپلیکیشن مون نیاز یا به ازای هر فرگمنت یا view model یا activity یا چیزهای دیگه ساخته بشه یا نه.

و یا کلاً میتونیم برای متدمون اصلاً محدوده ایی مشخص نکنیم.

![My image](https://github.com/Developers0101/notes-android-course/raw/main/images/%D9%87%DB%8C%D9%84%D8%AA_files1/image043.png)

Singleton component بالا برای @install in و با @singleton پایین که برای @provides هست فرق داره.

ما اومدیم یه ماژول درست کردیم، که براش یه متد درست کردیم و بعد @provides کردیم که بتونیم تزریقش کنیم، بعد بهش @singleton دادیم که کلاً یکبار اجرا بشه، تا اون زمانی که اپلیکیشن ما داره اجرا میشه، و حتی میتونیم @singleton رو برداریم و براش محدوده مشخص نکنیم.



قسمت 34

` `![My image](https://github.com/Developers0101/notes-android-course/raw/main/images/%D9%87%DB%8C%D9%84%D8%AA_files1/image044.png)

برای اینکه activity یا fragment بتونه از گراف هایی hilt پشتیبانی کنه مثلاً بتونه inject, qualifier, named رو بشناسه، باید بالای اون فرگمنت یا اکتیویتی از @Android Entry point استفاده کنیم.

الان اکتیویتی ما دیگه کلیات مربوط به hilt رو میشناسه.

![My image](https://github.com/Developers0101/notes-android-course/raw/main/images/%D9%87%DB%8C%D9%84%D8%AA_files1/image045.png)

ما چیزی که @provide شده رو با @inject میتونیم تزریق کنیم به activity مون.

![My image](https://github.com/Developers0101/notes-android-course/raw/main/images/%D9%87%DB%8C%D9%84%D8%AA_files1/image046.png)

حتماً باید چیزهایی که در قالب متغییر استفاده میکنیم بصورت lateinit باشه و اگه val باشه error میده، و هیچ کدوم از چیزها نباید بصورت private تعریف بشه.

که میایم و یه متغییر بصورت string تعریف میکنیم.

` `![My image](https://github.com/Developers0101/notes-android-course/raw/main/images/%D9%87%DB%8C%D9%84%D8%AA_files1/image047.png)

وقتی از این متد provides شده، با inject توی اکتیویتی استفاده کردیم همچین علامتی ![My image](https://github.com/Developers0101/notes-android-course/raw/main/images/%D9%87%DB%8C%D9%84%D8%AA_files1/image048.png) کنارش میاد که یعنی استفاده شد.

![My image](https://github.com/Developers0101/notes-android-course/raw/main/images/%D9%87%DB%8C%D9%84%D8%AA_files1/image049.png)

اگه val کنیم error میده بخاطر همین حتماً باید lateinit تعریف کنیم، که خودش که داره inject میکنه، میاد و مقداردهی میکنه و بهمون میده و میتونیم ازش استفاده کنیم.

Inject از طریق نوع data type که از نوع string هست تونست تشخیص بده که این متغییر username ما همون متد provide username هست که داخل ماژولمون تعریف کرده بودیم.

![My image](https://github.com/Developers0101/notes-android-course/raw/main/images/%D9%87%DB%8C%D9%84%D8%AA_files1/image050.png)

میگه این متد provide username ما همون string هست و مقدار بازگشتیش از نوع string هست.

در واقع این متد بالا که به صورت تک خطی تعریف کرده بودیم به اینصورت هست و از نوع string هست و داره string رو برمیگردونه.

![My image](https://github.com/Developers0101/notes-android-course/raw/main/images/%D9%87%DB%8C%D9%84%D8%AA_files1/image051.png)

وقتی این متد رو به این صورت نوشتیم.

![My image](https://github.com/Developers0101/notes-android-course/raw/main/images/%D9%87%DB%8C%D9%84%D8%AA_files1/image052.png)

توی inject همچین علامتی میاد چون توی provide username نوعش رو مشخص کرده بودیم که string هست و با نوع inject که string هست یکی هست میاد و اون رو نشون میده و اگه به حالت اول برگردونیم که نوع متد provide مشخص نیست این علامت هم از بین میره که چیز مهمی نیست و مشکلی نداره.



![My image](https://github.com/Developers0101/notes-android-course/raw/main/images/%D9%87%DB%8C%D9%84%D8%AA_files1/image053.png)

به این صورت میتونیم ازش استفاده کنیم و username رو set میکنیم.

ما برای اینکه اطلاعات username رو نشون بدیم، object main module رو تعریف نکردیم در صورتی که اگه از تزریق وابستگی استفاده نمیکردیم باید میومدیم ماژول main رو تعریف میکردیم و initialize میکردیم و بعد مقدار دهیش میکردیم، مثل کاری که قبلاً برای قسمت دیتابیس انجام داده بودیم:

![My image](https://github.com/Developers0101/notes-android-course/raw/main/images/%D9%87%DB%8C%D9%84%D8%AA_files1/image054.jpg)

که اول کلاس مدل یا entity مون رو اینجا تعریف کردیم:

![My image](https://github.com/Developers0101/notes-android-course/raw/main/images/%D9%87%DB%8C%D9%84%D8%AA_files1/image055.png)

و بعد اومدیم initialize و مقداردهیش کردیم.

ولی با تزریق وابستگی دیگه نیاز به این کارها نبود و مستقیماً ازشون استفاده نکردیم و هرموقع که بخوایم میتونیم داخل ماژولمون بیایم و براحتی مقدارشو تغییر بدیم بدون اینکه داخل اکتیویتیمون نیازی به تغییر دادن چیزی باشه.

![My image](https://github.com/Developers0101/notes-android-course/raw/main/images/%D9%87%DB%8C%D9%84%D8%AA_files1/image056.png)

تو ماژول main یه متد دیگه تعریف میکنه که از نوع string هست و براش scope یا محدوده اجرا شونده در نظر نگرفتیم و متد رو به حالت دوم که return داره تعریف کردیم که هیچ فرقی نداره، چون در هردو حالت string داره return میشه.

وقتی رو علامت ![My image](https://github.com/Developers0101/notes-android-course/raw/main/images/%D9%87%DB%8C%D9%84%D8%AA_files1/image048.png) استفاده شده متدهامون میزنیم هردو علامت مارو به متغییر username که در کلاس activity مون تعریف کرده بودیم میبرن که دوتا متد از نوع string داریم با یه متغییر:

![My image](https://github.com/Developers0101/notes-android-course/raw/main/images/%D9%87%DB%8C%D9%84%D8%AA_files1/image058.png)

وقتی اجرا میگیریم برنامه کرش میکنه:

![My image](https://github.com/Developers0101/notes-android-course/raw/main/images/%D9%87%DB%8C%D9%84%D8%AA_files1/image059.png)

bound multiple times یعنی از یه چیزی چندتا دونه پیدا کرده.

![My image](https://github.com/Developers0101/notes-android-course/raw/main/images/%D9%87%DB%8C%D9%84%D8%AA_files1/image060.png)

که میگه از provide nick name و provide user name رو پیدا کرده:

![My image](https://github.com/Developers0101/notes-android-course/raw/main/images/%D9%87%DB%8C%D9%84%D8%AA_files1/image061.png)

که ما میخوایم توی username بیایم و inject کنیم ولی میخوایم کدوم رو inject کنیم و تزریق کنیم.

خطای bound multiple times یعنی از یه چیزی چندتا پیدا کرده.

برای فیکس کردن این خطا و این حالت ها ما میتونیم از Qualifiers یا Named استفاد کنیم.

Qualifiers یکمی روشش طولانی تر و زمانبرتر هست وبیشتر در dagger اصلی که parent hilt بحساب میاد کاربرد داشت، ولی بهترین، راحتترین و سریعترین روشش Named هست.

Qualifiers : یعنی درسته که 2 یا چندتا چیز داریم ولی میایم و محدودش میکنیم که میایم و محدوده اش رو مشخص میکنیم، مثلاً اگه 2تا محمد داشته باشیم یکی نوری یکی محمدپور مشخص میکنیم که با کدومشون کار داریم که با Qualifiers محدوده اش رو مشخص میکنیم.

چون مربوط به dependency injection میشه میایم و توی پوشه ی di و یه پوشه ی جدید به اسم Qualifiers درست میکنیم چون ممکن چندین Qualifiers داشته باشیم.

![My image](https://github.com/Developers0101/notes-android-course/raw/main/images/%D9%87%DB%8C%D9%84%D8%AA_files1/image062.png)

بعد داخل پوشه Qualifier میایم و یک Annotation کلاس درست میکنیم چون باید در قالب یک Annotation استفاده کنیم.

با Qualifier میایم میگیم که هرجا که string یی خواستیم که nickname مد نظرمون بود همون nickname رو به ما بده.

![My image](https://github.com/Developers0101/notes-android-course/raw/main/images/%D9%87%DB%8C%D9%84%D8%AA_files1/image063.jpg)

همچین کلاسی ساخته میشه که داخلش با Qualifier میایم و به hilt میشناسونیمش.

![My image](https://github.com/Developers0101/notes-android-course/raw/main/images/%D9%87%DB%8C%D9%84%D8%AA_files1/image064.png)

بعد میایم و نحوه ی اجرا شدن Qualifier رو هم میگیم که زمانی که میخواد کامپایل بشه چطور این اتفاق بیفته که از @Retention ها استفاده میکنیم.

که میتونیم نحوه کامپایل شدنش رو مشخص کنیم که به چه صورتی باشه :

![My image](https://github.com/Developers0101/notes-android-course/raw/main/images/%D9%87%DB%8C%D9%84%D8%AA_files1/image065.png)

BINARY که بصورت حالت باینری اجرا میکنه و تبدیلش میکنه به باینری.

RUNTIME که به حالت ران تایم اجراش میکنه.

![My image](https://github.com/Developers0101/notes-android-course/raw/main/images/%D9%87%DB%8C%D9%84%D8%AA_files1/image066.png)

میایم و بصورت باینری رو انتخاب میکنیم.

![My image](https://github.com/Developers0101/notes-android-course/raw/main/images/%D9%87%DB%8C%D9%84%D8%AA_files1/image067.png)

میایم داخل فایل ماژولمون و اون کلاس Annotation (@nickname) که ساخته بودیم رو به متد موردنظرمون اضافه میکنیم که دیگه علامت ![My image](https://github.com/Developers0101/notes-android-course/raw/main/images/%D9%87%DB%8C%D9%84%D8%AA_files1/image068.png) از بین میره و خودش تشخیص میده.

![My image](https://github.com/Developers0101/notes-android-course/raw/main/images/%D9%87%DB%8C%D9%84%D8%AA_files1/image069.png) 

که بعد میایم و از Annotation مون توی کلاس activity مون هم استفاده میکنیم و به اون متغییری که inject کردیم میدیم.

وقتی برنامه رو اجرا میگیریم به درستی اجرا میشه و nick name رو نشون میده چون محدوده اش رو با Annotation مشخص کردیم و اگه هرتعداد هم که string میداشتیم بازم هیچ مشکلی نبود و میومد و nickname مارو نشون میداد.

اگه زمان استفاده داخل کلاس main activity بیایم و @NickName رو برداریم inject به متد username داخل فایل ماژول اشاره میکنه و اجرا میکنه.



قسمت 35

![My image](https://github.com/Developers0101/notes-android-course/raw/main/images/%D9%87%DB%8C%D9%84%D8%AA_files1/image070.png)

Named : بجای Qualifiers میتونیم از Named استفاده کنیم که خیلی راحت هست و از نوع inject هست.

![My image](https://github.com/Developers0101/notes-android-course/raw/main/images/%D9%87%DB%8C%D9%84%D8%AA_files1/image071.png)

و فقط داخلش میایم و کلید مورد نظرو قرار میدیم.

![My image](https://github.com/Developers0101/notes-android-course/raw/main/images/%D9%87%DB%8C%D9%84%D8%AA_files1/image072.png)

چون کلید های Named بصورت ثابت هستن، بهتر ، استاندارتر، اصولی تر و حرفه ایی تر اینه که بیایم و بصورت ثابت داخل constants تعریفش کنیم.

![My image](https://github.com/Developers0101/notes-android-course/raw/main/images/%D9%87%DB%8C%D9%84%D8%AA_files1/image073.png)

به این صورت و در ثابت ها میایم برای هرکدوم یه اسم انتخاب میکنیم.

![My image](https://github.com/Developers0101/notes-android-course/raw/main/images/%D9%87%DB%8C%D9%84%D8%AA_files1/image074.jpg)

موقع استفاده در اکتیویتی هم میایم و به این صورت استفاده میکنیم و با named مشخص میکنیم.

یه ماژول دیگه درست میکنیم و یه string داریم که نمیخوایم مستقیماً داخل ماژولمون بیایم و بهش مقدار بدیم، بلکه میخوایم از string داخل پوشه res استفاده کنیم، که برای دسترسی بهش حتماً نیاز به استفاده از context هست ولی بصورت تزریق وابستگی.

درحالت عادی میومدیم و تو constructor ش context رو میدادیم و بعد هرجا که میخواستیم از اون کلاس استفاده کنیم توی constructor پاس میدادیم و استفاده میکردیم، ولی اینجا اگه از این روش استفاده کنیم وابستگی بوجود میاره و کلاس ما به context وابستگی پیدا میکنه و بعد باید این وابستگی هارو توی activity مون تامین کنیم.

![My image](https://github.com/Developers0101/notes-android-course/raw/main/images/%D9%87%DB%8C%D9%84%D8%AA_files1/image075.png)

برای اینکه بتونیم text رو از پوشه res-> string بتونیم بخونیم و استفاده کنیم نیاز به get string هست، ولی نمیشناسه چون برای اینکه بتونیم از get string استفاده کنیم نیاز به context داریم.

وقتی از get string داخل اکتیویتی استفاده میکنیم میشناسه چون خود اکتیویتی بصورت پیشفرض context رو داره.

![My image](https://github.com/Developers0101/notes-android-course/raw/main/images/%D9%87%DB%8C%D9%84%D8%AA_files1/image076.png)

اگه بیایم و مستقیم داخل ورودی context بدیم یعنی داریم دوباره وابستگی ایجاد میکنیم و درست نیست.

![My image](https://github.com/Developers0101/notes-android-course/raw/main/images/%D9%87%DB%8C%D9%84%D8%AA_files1/image077.png)

![My image](https://github.com/Developers0101/notes-android-course/raw/main/images/%D9%87%DB%8C%D9%84%D8%AA_files1/image078.png)

میایم و context رو بهش میدیم ولی نه اینکه خودمون بیایم و تامینش کنیم بلکه با      @Application Context میگیم خودت برو تامینش کن، که میره و context مربوطه رو میاره و برامون تامینش میکنه و بعد ما میتونیم با context به get string دسترسی داشته باشیم.

درست که ما context رو در ورودی دادیم ولی خودش میره context رو تامین میکنه و بعد در اختیار ما قرار میده.

![My image](https://github.com/Developers0101/notes-android-course/raw/main/images/%D9%87%DB%8C%D9%84%D8%AA_files1/image079.png)

به همین سادگی میتونیم ازش استفاده کنیم، بدون اینکه نیاز باشه جایی بیایم و ماژولمون رو تعریف کنیم.



قسمت 36

استفاده از room در hilt : که یک صفحه داریم که کاربر روی دکمه save میزنه اطلاعات توی همون صفحه ذخیره میشه و توی recycler view نمایش داده میشه.

یه پوشه ی db برای دیتابیس روم ایجاد میکنیم و داخلش کلاس های entity, dao, database رو درست میکنیم، که همشون براساس کدهایی تکراری هست که قبلاً زدیم.

![My image](https://github.com/Developers0101/notes-android-course/raw/main/images/%D9%87%DB%8C%D9%84%D8%AA_files1/image080.jpg)

Entity رو از نوع data class تعریف میکنی و داخلش 2 تا متغییر داریم یه id و یه title .

![My image](https://github.com/Developers0101/notes-android-course/raw/main/images/%D9%87%DB%8C%D9%84%D8%AA_files1/image081.jpg)

داخل dao 2تا عملیات بیشتر نداریم یکی save هست که insert میکنیم و یکی دیگه هم یه custom query هست که  get All که بصورت mutable list هست و  میاد اطلاعات ذخیره شده رو نشون میده.

` `![My image](https://github.com/Developers0101/notes-android-course/raw/main/images/%D9%87%DB%8C%D9%84%D8%AA_files1/image082.jpg)

اگه از export Schema توی کلاس database استفاده نکنیم موقع خروجی گرفتن warning میده.

![My image](https://github.com/Developers0101/notes-android-course/raw/main/images/%D9%87%DB%8C%D9%84%D8%AA_files1/image083.png)

توی database مون entity و dao رو مینویسیم، که موقع استفاده از دیتابیس ما 2 تا فیلد داریم که یکی id که auto generate هست و یه فیلد دیگه title که توسط کاربر پر میشه و بعد لیست رو نشون میده.

![My image](https://github.com/Developers0101/notes-android-course/raw/main/images/%D9%87%DB%8C%D9%84%D8%AA_files1/image084.png)

میایم از کلاس adapter بصورت خام و بدون hilt استفاده میکنیم.



قسمت 37

اولین کار برای تزریق وابستگی ساخت کلاس Application هست و ما به ازای هر پروژه فقط یک کلاس application داریم.

میایم و برای تزریق وابستگی داخل دیتابیسمون یه package di درست میکنیم و module مون رو داخلش قرار میدیم.

ما برای استفاده کردن از room نیاز به 3تا چیز داشتیم که 1- database .

که میومدیم و توی تموم کلاس هایی که نیاز بود دیتابیس رو تعریف میکردیم :

![My image](https://github.com/Developers0101/notes-android-course/raw/main/images/%D9%87%DB%8C%D9%84%D8%AA_files1/image085.png)

2-  dao: که ما توسط dao که داخل کلاس دیتابیس تعریف کرده بودیم: 

![My image](https://github.com/Developers0101/notes-android-course/raw/main/images/%D9%87%DB%8C%D9%84%D8%AA_files1/image086.png)

میتونستیم به interface dao دسترسی داشتیم : 

![My image](https://github.com/Developers0101/notes-android-course/raw/main/images/%D9%87%DB%8C%D9%84%D8%AA_files1/image087.png)

که بتونیم عملیات هامون رو مثل delete, update, save و ... بتونیم انجام بدیم.

3- entity : وقتی میخوای اطلاعات رو save, update, delete و ... کنیم، نیاز داریم که اول اطلاعاتی مثلاً مثل id, tiltle و ... رو در entity بریزیم و بعد از entity بریزیم توی dao:

![My image](https://github.com/Developers0101/notes-android-course/raw/main/images/%D9%87%DB%8C%D9%84%D8%AA_files1/image088.png)

![My image](https://github.com/Developers0101/notes-android-course/raw/main/images/%D9%87%DB%8C%D9%84%D8%AA_files1/image089.jpg)

ما به این 3 تا(database, dao, entity) نیاز داریم و هرجا که بخوایم با database کار کنیم این 3 تا وابستگی های ما هستن.



میریم توی پوشه ی di و وابستگی های database مون رو با ماژول provide یا مهیا میکنیم:

![My image](https://github.com/Developers0101/notes-android-course/raw/main/images/%D9%87%DB%8C%D9%84%D8%AA_files1/image090.jpg)

اسمش رو میزاریم db module مخفف ماژول دیتابیس، چون تو پروژه ها، ما ماژول های مختلفی داریم مثلاً ماژول برای دیتابیس، ماژول برای ارتباط با اینترنت، ماژول برای صفحه ی اصلی، ماژول فرگمنت ها و ... و هرچندتا که بخوایم و نیاز باشه.

![My image](https://github.com/Developers0101/notes-android-course/raw/main/images/%D9%87%DB%8C%D9%84%D8%AA_files1/image091.jpg)

میایم محدوده ی ماژول رو singleton میکنیم که به ازای هر اکتیویتی یا فرگمنت ساخته نشه، چون دیتابیس یک عملیات سنگین و نباید توی هر صفحه یکبار ساخته بشه، و دیتابیس ما همه جای یکی هست و عوض نمیشه، فقط اطلاعاتش تغییر میکنه.

![My image](https://github.com/Developers0101/notes-android-course/raw/main/images/%D9%87%DB%8C%D9%84%D8%AA_files1/image092.png)

دقیقاً منظور همین دستورات هست که در آموزش دیتابیس و امدیم در صفحات مختلف و چندین بار تعریفش کردیم که این کار فشار اپلیکیشن به سخت افزار و زیاد میکنه و ما منابع محدودی داریم و نباید همه چی الکی از اول ساخته بشه، بخاطر همین singleton میکنیم، که تو کل زمانی که اپلیکیشن ما داره ساخته میشه، یکبار اونو درست میکنه و هرکجا که نیاز بود، میره از همون یکباری که داخل بلوک رم ذخیره شده بود استفاده میکنه و اگه از singleton استفاده نکنیم مدام داره تعریف میکنه که از بدترین نوع ممکن هست.

بعد میایم و 3 مورد دیتابیس، dao و entity رو توی ماژول تعریف میکنیم.



![My image](https://github.com/Developers0101/notes-android-course/raw/main/images/%D9%87%DB%8C%D9%84%D8%AA_files1/image093.png)

دیتابیس رو singleton تعریف میکنیم چون سنگین هست و میخوایم فقط یکبار تعریف بشه و همه اش تعریف نشه، و دیتابیس نیاز به context داره و نیاز به room . database builder که از ما 3 تا ورودی میخواد.

![My image](https://github.com/Developers0101/notes-android-course/raw/main/images/%D9%87%DB%8C%D9%84%D8%AA_files1/image094.png)

ورودی اول context ، ورودی دوم خود کلاس دیتابیس، ورودی سوم هم اسم دیتابیسمون هست که بصورت ثابت تعریف کرده بودیم.

![My image](https://github.com/Developers0101/notes-android-course/raw/main/images/%D9%87%DB%8C%D9%84%D8%AA_files1/image095.png)

بعد میایم و روی ترد main هم با allow main اوکی میکنیم و با migration برای نسخه های مختلف که به conflict نخوره و بعد build میکنیم.

نیاز به dao داریم برای انجام عملیات دیتابیس.

![My image](https://github.com/Developers0101/notes-android-course/raw/main/images/%D9%87%DB%8C%D9%84%D8%AA_files1/image096.jpg)

چون عملیات dao ثابت هست اونو هم بصورت singleton تعریف میکنیم، و dao برای انجام عملیات مثلاً ذخیره، آپدیت، دیلیت و ... ، نیاز به دیتابیس داره که ما نیاز داریم به دیتابسمون که provide ش کردیم.

هرچیزی که داریم provide (مثلاً database)میکنیم و میخوایم از اون توی چیز دیگه ایی (مثلاً dao) که وابسته اس به اون استفاده کنیم، باید از constructor ش استفاده کنیم.

![My image](https://github.com/Developers0101/notes-android-course/raw/main/images/%D9%87%DB%8C%D9%84%D8%AA_files1/image097.png)

و ما میخوایم از dao استفاده کنیم که وابسته هستیم به database ، پس میایم و database مون(Note database) رو توی ورودی dao و بهش میدیم، که با db به متد note dao که داخل کلاس دیتابیس نوشته بودیم دسترسی داریم.

بعد نیاز به entity داریم برای ذخیره اطلاعات.

![My image](https://github.com/Developers0101/notes-android-course/raw/main/images/%D9%87%DB%8C%D9%84%D8%AA_files1/image098.png)

چون entity سنگین نیست ما میتونیم واسش از singleton استفاده نکنیم.

ولی note model از ما مقدار پیشفرض میخواد error میده، چون میخواد تعریف بشه و نیاز به مقدار پیشفرض داره، ولی ما که نمیدونیم id, title ما با چه مقداری میخوان ذخیره بشن.

![My image](https://github.com/Developers0101/notes-android-course/raw/main/images/%D9%87%DB%8C%D9%84%D8%AA_files1/image099.png)

بخاطر همین توی مدلمون یه مقدار پیشفرض براشون set میکنیم که فعلاً error رو برای ما نشون نده.

وقتی که ما default value ست میکنیم میره برای ساختنشون از default value استفاده میکنه.

![My image](https://github.com/Developers0101/notes-android-course/raw/main/images/%D9%87%DB%8C%D9%84%D8%AA_files2/image100.png)

ما اومدیم و وابستگی های کلاس دیتابیسمون رو درست کردیم.

ما برای اینکه بتونیم از اینها استفاده کنیم، استفاده مستقیماً از این ها طبق برنامه نویسی های مدرن مورد استفاده قرار نمیگیره، بلکه نیاز به یک repository داریم.

repository یعنی میاد وظیفه ی تامین کردن اطلاعات مارو برعهده میگیره، مثلاً بخوایم اطلاعات رو از دیتابیس یا سرور بگیریم، میاد و برامون اوکی میکنه.

بخاطر همین میایم و دیتابیسمون رو داخل repository تعریف میکنیم و جاهایی که نیاز repository رو تعریف میکنیم و ازش استفاده میکنیم.

برای اینکه کدهامون شلوغ نشه یه package دیگه به اسم repository درست میکنیم.

![My image](https://github.com/Developers0101/notes-android-course/raw/main/images/%D9%87%DB%8C%D9%84%D8%AA_files2/image101.png)

میایم و کلاس db repository درست میکنیم.



![My image](https://github.com/Developers0101/notes-android-course/raw/main/images/%D9%87%DB%8C%D9%84%D8%AA_files2/image102.png)

این repository برای اینکه اطلاعات رو تامین کنه و در اختیار ما قرار بده نیاز به dao (note dao) داره، چون اطلاعات ما توسط note dao کنترل میشن مثلاً ذخیره، آپدیت، گرفتن، دیلیت و ... که داخل dao قرار داره و repository برای تامین این اطلاعات نیاز داره به dao دسترسی داشته باشه که اونو توی ورودی constructor repository قرار میدیم و میتونیم ازش استفاده کنیم.

ولی این الان شبیه حالت عادی شد و قرار بود که بصورت مستقیماً ازشون استفاده نکنیم.

جاهایی که میخوایم ورودی و constructor داشته باشیم و اونو قبلاً تامین کردیم یا میخوایم تامین کنیم، نباید بیام مستقیماً داخل constructor و بعد براش ورودی set کنیم.

![My image](https://github.com/Developers0101/notes-android-course/raw/main/images/%D9%87%DB%8C%D9%84%D8%AA_files2/image103.jpg)

برای تزریق وابستگی میایم و قبل از سازنده یا constructor کلاس و از @inject استفاده میکنیم.

![My image](https://github.com/Developers0101/notes-android-course/raw/main/images/%D9%87%DB%8C%D9%84%D8%AA_files2/image104.jpg)

با اینکار اون متد dao که داخل ماژولمون تعریف کرده بودیم رو تزریق کردیم، که داخل     constructor repository نیاز به note dao داشتیم که note dao رو تو ماژول provide کرده بودیم و خود note dao نیاز به note database داره که اونو هم همونجا provide کرده بودیم و بهش دادیم و همینطور سلسله وار میره جلو.

حالا داخل repository به ازای هر query که داخل dao نوشتیم میایم و ازشون استفاده میکنیم.

که 2تا query save, get all داشتیم.

![My image](https://github.com/Developers0101/notes-android-course/raw/main/images/%D9%87%DB%8C%D9%84%D8%AA_files2/image105.png)

برای ورودی constructor باید از نوع val در نظر بگیریم و گرنه داخل کلاس نمیتونیم از dao استفاده کنیم.

میایم و متد save مینویسیم که کلاس مدل entity مون رو میدیم و با dao میایم و ذخیره میکنیم.

و بعد با متد get all میایم و تموم مواردی که ذخیره کردیم رو میگیریم.

الان کامل این متدها و اطلاعاتشون در دسترس هستن و میتونیم ازشون استفاده کنیم.

میخوایم از hilt داخل adapter استفاده کنیم که نیایم و adapter رو مستقیم تعریف کنیم:

![My image](https://github.com/Developers0101/notes-android-course/raw/main/images/%D9%87%DB%8C%D9%84%D8%AA_files2/image106.png)

اینجا اومدیم و adapter رو هرچند بصورت lazy ، تعریف کردیم و بهش وابستگی داریم و داریم initialize ش میکنیم.

![My image](https://github.com/Developers0101/notes-android-course/raw/main/images/%D9%87%DB%8C%D9%84%D8%AA_files2/image107.jpg)

میایم و با @inject داخل constructor و تزریق میکنیم وابستگیمون رو.

زمانی که میخوایم برای یک کلاس وابستگی رو تزریق کنیم، چه constructor داشته باشه و چه نداشته باشه، ما باید بهش constructor رو اضافه کنیم.

![My image](https://github.com/Developers0101/notes-android-course/raw/main/images/%D9%87%DB%8C%D9%84%D8%AA_files2/image108.png)

اگه constructor نزاریم inject رو قبول نمیکنه و error میده.

برای اینکه مستقیماً note adapter رو تعریف نکنیم میایم و بهش constructor میدیم هرچند بصورت خالی باشه و هیچ مشکلی نداره و روش استفاده اش همینه.

![My image](https://github.com/Developers0101/notes-android-course/raw/main/images/%D9%87%DB%8C%D9%84%D8%AA_files2/image109.png)

ما میتونیم حتی کلاس ها و مواردی که داخل ماژول نیستن رو هم singleton یا activity scope ،       fragment scope یا view model scope بزنیم و استفاده کنیم و نیاز نیست حتماً داخل ماژول باشه تا بتونه singleton یا بقیه موارد باشه.

![My image](https://github.com/Developers0101/notes-android-course/raw/main/images/%D9%87%DB%8C%D9%84%D8%AA_files2/image110.png)

Component رو نمیتونیم خارج از ماژول بزنیم، چون مخصوص @install in هست و محدوده ی خود ماژول رو مشخص میکنه.

![My image](https://github.com/Developers0101/notes-android-course/raw/main/images/%D9%87%DB%8C%D9%84%D8%AA_files2/image111.png)

میتونیم adapter مون رو singleton کنیم که در طول اجرای اکتیوتی یه بار ساخته بشه و همونو نشون بده.

![My image](https://github.com/Developers0101/notes-android-course/raw/main/images/%D9%87%DB%8C%D9%84%D8%AA_files2/image112.png)

![My image](https://github.com/Developers0101/notes-android-course/raw/main/images/%D9%87%DB%8C%D9%84%D8%AA_files2/image113.png)

یا حتی میتونیم از activity scope یا fragment scope هم استفاده کنیم.

ما حتی میتونیم adapter رو داخل ماژول تعریف کنیم ولی چون ماژولمون db بود و مربوط به دیتابیس بود بخاطر همین adapter رو داخل ماژول قرار ندادیم، و همین که ممکن ما یه کلاسی(adapter) داشته باشیم که وابستگی داره به یه سری چیزهای دیگه، که اومدیم وابستگی خود کلاس (adapter) رو هم تامین کردیم، بخاطر همین توی ماژول ننوشتیم.

![My image](https://github.com/Developers0101/notes-android-course/raw/main/images/%D9%87%DB%8C%D9%84%D8%AA_files2/image114.png)

و حتی میتونیم repository رو هم بصورت singleton تعریف کنیم.

این خود ما هستیم که تعیین میکنیم که این کلاس داخل ماژول قرار بگیره یا تنهایی هست و باید خود همون یه کلاس رو تامین کرد و ... .



قسمت 38

ما برای اینکه بتونیم اطلاعات رو بگیریم و در activity نشون بدیم نیاز به 3 تا چیز داریم:

1- adapter 2- repository : چون ریپازیتوری میاد و عملیات های ما مثل ذخیره کردن، آپدیت، دیلیت کردن و گرفتن اطلاعات رو برای ما تامین میکنه.3- نیاز به مدل (note model) داریم تا بتونیم اطلاعات رو ذخیره کنیم.

![My image](https://github.com/Developers0101/notes-android-course/raw/main/images/%D9%87%DB%8C%D9%84%D8%AA_files2/image115.png)

میایم هر 3 مورد رو inject میکنیم و حتماً حتماً باید @Andoid Entry Point رو هم بهش بدیم وگرنه هیچکدوم از inject ها و وابستگی هارو نمیشناسه و کرش میکنه.

روی هرکدوم از علامت ها ![My image](https://github.com/Developers0101/notes-android-course/raw/main/images/%D9%87%DB%8C%D9%84%D8%AA_files1/image116.png) میزنیم دقیقاً وارد کلاسش میشه و constructor اون کلاس هارو نشون میده، هرچند مثلconstructor adapter  خالی باشه، بخاطر همین به constructor ها نیاز داریم.

![My image](https://github.com/Developers0101/notes-android-course/raw/main/images/%D9%87%DB%8C%D9%84%D8%AA_files2/image117.png)

چون entity رو inject کردیم و initialize شده دیگه نیازی نیست مجدداً  اینطوری بنویسیم و دوباره initialize کنیم بعد بیایم و به note model مقدار بدیم، البته میتونیم با همین روش هم بریم، یا میتونیم مستقیم ازش استفاده کنیم:

![My image](https://github.com/Developers0101/notes-android-course/raw/main/images/%D9%87%DB%8C%D9%84%D8%AA_files2/image118.png)

![My image](https://github.com/Developers0101/notes-android-course/raw/main/images/%D9%87%DB%8C%D9%84%D8%AA_files2/image119.png)

میتونیم مقداری که میخوایم رو مستقیماً، توی خودش ذخیره کنیم ولی باید بیایم و note model مون مواردش رو به var تغییر بدیم وگرنه error میده، چون میخوایم دوباره مقدار دهی کنیم و نباید val باشه.

![My image](https://github.com/Developers0101/notes-android-course/raw/main/images/%D9%87%DB%8C%D9%84%D8%AA_files2/image120.png)

میایم و id رو 0 میزاریم چون auto generate هست خودش بهش اضافه میشه و title رو هم از edit text مون میگیریم بعد اینکه entity رو پر کردیم میریم و از طریق repository ذخیره میکنیم.

![My image](https://github.com/Developers0101/notes-android-course/raw/main/images/%D9%87%DB%8C%D9%84%D8%AA_files2/image121.png)

بعد اینکه کاربر روی save زد میایم و edit text رو خالی میکنیم.

![My image](https://github.com/Developers0101/notes-android-course/raw/main/images/%D9%87%DB%8C%D9%84%D8%AA_files2/image122.png)

اومدیم با استفاده از adapter و با repository اطلاعات رو گرفتیم و بعد recycler view رو هم set میکنیم.

وقتی برنامه اجرا میشه و چیزی مینویسیم و دکمه save رو میزنیم برنامه ذخیره میکنه و چیزی نشون نمیده که باید دوباره اجرا کنیم تا نشون بده:

![My image](https://github.com/Developers0101/notes-android-course/raw/main/images/%D9%87%DB%8C%D9%84%D8%AA_files2/image123.png)

برای حل این مشکل و اینکه همون لحظه به لیست اضافه کنه میایم و adapter رو همونجایی که روی دکمه save کلیک شد قرار میدیم تا در لحظه نشون بده.

میخوایم روی هرکدوم از آیتم های recycler view که کلیک شد بیایم و id, title رو بصورت toast نشون بدیم.

برای گرفتن یه آیتم از recycler view میشه داخل خود adapter اومد و یه set on click نوشت، ولی روش حرفه ایی واصولی نیست.

مثل زمانی که میخوایم یه کاری روی اکتیویتی انجام بدیم و زمانی که روی یکی از آیتم ها که کلیک کردیم، اطلاعاتش رو بفرستیم به یه صفحه ی دیگه، اینجور کارها و عملیات های سنگین رو بهتر که توی اون activity یا فرگمنت انجام بدیم، نه توی adapter.

برای اینکه بتونیم وقتی روی آیتم recycler view کلیک که شد بتونیم اطلاعاتش رو بصورت toast یا هرچیز دلخواه دیگه بگیریم و دسترسی داشته باشیم نیاز به یه interface داریم.

Interface مثل یه شیلنگ آب میمونه، هر وقت وصلش کنیم به شیر آب و اون سرش که خالی هست هر سمتی بگیریم آب رو میفرسته همونجا، interface همچین حالتی داره و برای انتقال اطلاعات و اینجور چیزها مورد استفاده قرار میگیره، نه فقط انتقال اطلاعات، حتی میتونیم مثلاً داریم یه کاری انجام میدیم، بواسطه ی اینکار یه جای دیگه یه اتفاق دیگه ایی بیوفته که میتونیم از interface استفاده کنیم.

ما میخوایم رو آیتم recycler view کلیک کنیم و بواسطه ی اون توی activity بیایم و یه toast رو همراه با اطلاعات این آیتم(id, title) نشون بدیم.

داخل کلاس adapter و خارج از inner class مون کد میزنیم و نیاز به 2تا چیز داریم:

1- متغییری که توسط این متغییر میتونیم اطلاعاتی که میخوایم رو بگیریم و در نهایت اونرو در قالب interface بفرستیم و از lambda expression ها استفاده میکنیم.

![My image](https://github.com/Developers0101/notes-android-course/raw/main/images/%D9%87%DB%8C%D9%84%D8%AA_files2/image124.png)

یه متغییر به اسم on item click listener مینویسیم، چون میخوایم اطلاعات هر آیتم هم فرستاده بشه میایم و model مون رو هم میفرستیم که بصورت unit مینویسیم که یعنی، مقدار بازگشتی نداره و معادل void جاوا هست و براش امکان null بودن رو هم درنظر میگیریم.

2- نیاز به یه function داریم تا بتونیم از متغییرمون استفاده کنیم.

![My image](https://github.com/Developers0101/notes-android-course/raw/main/images/%D9%87%DB%8C%D9%84%D8%AA_files2/image125.png)

که براش یه اسم(set on item click listener) در نظر میگیریم که از ما یه listener میخواد، بعد از ما lambda expression یی که بالا نوشته بودیم رو میخواد و میایم بهش همون مدلمون (note model)

رو میدیم و بصورت unit هست چون نمیخوایم چیزی رو برگشت بدیم.

و برای انتقالش میایم متغییرمون رو برابر با listener ش قرار میدیم.

الان براحتی ما روی هر آیتم که کلیک کنیم و توی activity از متد set on item click listener استفاده کنیم، بواسطه متغییر on item click listener هر آیتمی که انتخاب بشه چون مقدار note model رو داریم برامون برمیگردونه.

![My image](https://github.com/Developers0101/notes-android-course/raw/main/images/%D9%87%DB%8C%D9%84%D8%AA_files2/image126.png)

میریم داخل inner class و داخل متد set data و کلیک رو مینویسیم و با استفاده از متغییر on item click listener میگیم اگه null نبود که از let استفاده میکنیم که همون note model رو برای ما برمیگردونه.

![My image](https://github.com/Developers0101/notes-android-course/raw/main/images/%D9%87%DB%8C%D9%84%D8%AA_files2/image127.jpg)

![My image](https://github.com/Developers0101/notes-android-course/raw/main/images/%D9%87%DB%8C%D9%84%D8%AA_files2/image128.jpg)

که با it که همون note model ماست میایم براش note یا یه دونه آیتم از لیستمون رو میفرستیم.

خلاصه توضیحات برای interface مون که برای کلیک نوشتیم.

![My image](https://github.com/Developers0101/notes-android-course/raw/main/images/%D9%87%DB%8C%D9%84%D8%AA_files2/image129.png)

اومدیم یه متغییر on item click listener درست کردیم که تقریباً کار listener مارو انجام میده و داخلش کلاس note model مون رو میخوایم انتقال بدیم، که میگیم بصورت unit باشه و مقدار برگشتی نداره، بعد میایم یه متد set on item click listener مینویسیم که بتونیم جای دیگه مثلاً توی فرگمنت یا اکتیویتی دیگه بتونیم ازش استفاده کنیم و بعد اومدیم داخل متدمون و اون متغییر item click رو مقدار دهی کردیم، بعد میگیم زمانی که روی آیتم recycler view کلیک شد و میخوایم اطلاعات رو بفرستیم میایم و متغییر on item click رو با استفاده از مدلمون هر item یی که کلیک شد رو پر میکنیم و مقدارشو میگیریم، و هرجا از متد set on item استفاده کنیم، چون listener مون رو با on item click مقدار دهی کردیم، خیلی راحت میتونیم ازش استفاده کنیم.



![My image](https://github.com/Developers0101/notes-android-course/raw/main/images/%D9%87%DB%8C%D9%84%D8%AA_files2/image130.png)

حالا داخل activity مون و با استفاده از adapter به متد set on item دسترسی داریم.

![My image](https://github.com/Developers0101/notes-android-course/raw/main/images/%D9%87%DB%8C%D9%84%D8%AA_files2/image131.png)

بعد میایم و داخلش هرکاری که نیاز هست رو انجام میدیم، مثلاً یه toast مینویسیم.

بوسیله ی it براحتی به id, title دسترسی داریم.

این یکی از بهترین روش ها برای هندل کردن عملیات کلیک هست که با hilt هم سازگاری داره.

![My image](https://github.com/Developers0101/notes-android-course/raw/main/images/%D9%87%DB%8C%D9%84%D8%AA_files2/image132.png)



قسمت 39

Hilt و Retrofit :

![My image](https://github.com/Developers0101/notes-android-course/raw/main/images/%D9%87%DB%8C%D9%84%D8%AA_files2/image133.jpg)

کتابخونه log interceptor به ما کمک میکنه بتونیم جزئیات بیشتری از api که داریم call میکنیم رو ببینیم.

مثلاً یه وقتی داریم با یه api کار میکنیم و error میده و نمیدونیم این error از طرف ماست یا از طرف سرور، مثلاً error 500 میده که نمیدونیم از سمت ما هست یا سرور، این کتابخونه میاد و نوع error و دلیل اینکه به error خورده رو میاد نشون میده و ما میتونیم اون error رو بدیم به بک اند کار تا اونو فیکس کنه.

درکل ما با این کتابخونه میتونیم از api که داریم call میکنیم چه اوکی باشه چه با error روبرو بشه میتونیم log بگیریم و با جزئیات کامل همه چیزرو به ما نشون میده.

![My image](https://github.com/Developers0101/notes-android-course/raw/main/images/%D9%87%DB%8C%D9%84%D8%AA_files2/image134.png)

میایم 3 تا پوشه api, model, module رو به پروژه مون اضافه میکنیم.

![My image](https://github.com/Developers0101/notes-android-course/raw/main/images/%D9%87%DB%8C%D9%84%D8%AA_files2/image135.png)

توی api services میایم و endpoint مون رو قرار میدیم.

توی model هم همون مدلی که قبلاً توی retrofit کار کرده بودیم رو قرار میدیم.

![My image](https://github.com/Developers0101/notes-android-course/raw/main/images/%D9%87%DB%8C%D9%84%D8%AA_files2/image136.png)

بعد میایم و ماژول api مون رو هم مینویسیم و singleton میزاریم چون یک تنظیمات بیشتر برای ارتباط با سرور نداریم مثلاً بیایم توی هر صفحه ی یه base url داشته باشیم و بیایم توی اکتویتی a دیجی کالا رو داشته باشیم و توی activity b به دیوار api بزنیم و مثلاً توی activity c به اسنپ api بزنیم، چون اپمون یه دونه اس و تنظیماتمون هم یه دونه اس بخاطر همین میایم و از singleton استفاده میکنیم ولی تو مواقع خیلی خاص که چندین api داریم و نیاز داریم که اطلاعات مختلف از جاهای مختلف بیاد و نشون بدیم میایم بجای singleton از حالت های دیگه ایی استفاده میکنیم و برای هرکدوم از api ها یه تنظیمات خاص میزنیم که در 99% موارد ما فقط یه api داریم و اطلاعات از یکجا میاد.

وابستگی هایی که توی retrofit و داخل api client نیاز داریم کدهایی که قبلاً زده بودیم رو بررسی میکنیم:

![My image](https://github.com/Developers0101/notes-android-course/raw/main/images/%D9%87%DB%8C%D9%84%D8%AA_files2/image137.png)

client به time وابستگی داره، چون تایم داره از جای دیگه ایی میاد، خود retrofit هم به 2 تا چیز دیگه وابستگی داره، 1- base url و 2- client .

ما به 3 تا چیز وابستگی داریم که یکی داخل خود client و مربوط به time میشه و 2 تا دیگه داخل رتروفیت و شامل base url و client میشه.

به این حالت میشه نحوه ی وابستگی هارو تشخیص داد و یکی از بهترین راهای تشخیص وابستگی، trace کردن کدهاست، یعنی همین کاری که ما با retrofit انجام دادیم.

![My image](https://github.com/Developers0101/notes-android-course/raw/main/images/%D9%87%DB%8C%D9%84%D8%AA_files2/image138.png)

ما میتونیم constants یا ثابت هارو هم بصورت فایل و هم بصورت object درست کنیم و هردو حالت درسته.

![My image](https://github.com/Developers0101/notes-android-course/raw/main/images/%D9%87%DB%8C%D9%84%D8%AA_files2/image139.jpg)

Base url و time رو به constants مون اضافه میکنیم.

Time برای مشخص کردن زمان time out شدن سرور نیاز داریم.

![My image](https://github.com/Developers0101/notes-android-course/raw/main/images/%D9%87%DB%8C%D9%84%D8%AA_files2/image140.jpg)

چون base url ما ثابت هست و عوض نمیشه singleton قرار میدیم.

![My image](https://github.com/Developers0101/notes-android-course/raw/main/images/%D9%87%DB%8C%D9%84%D8%AA_files2/image141.jpg)

Connection timeout رو هم singleton قرار میدیم.

وابستگی سوم رو برای gson مینویسم که همراه با تنظیمات خاص.

مثلاً بعضی وقتها backend developer ها یه سری options های خاصی رو برای json خودشون در نظر میگیرین، و مثلاً فراموش میکنن یا به هر دلیلی به ما نمیگن، ولی زمانی که ما میخوایم gson مون با json در ارتباط باشه با error روبرو میشیم و اپلیکیشن مون بدرستی کار نمیکنه.

در اینجور مواقع میایم و یک بخشی رو به gson اضافه میکنیم، که بتونیم اون تنظیمات و option های خاص رو هم بتونیم ساپورت کنیم که بهش میگن lenient .

![My image](https://github.com/Developers0101/notes-android-course/raw/main/images/%D9%87%DB%8C%D9%84%D8%AA_files2/image142.jpg)

متدمون رو از نوع gson میزاریم و برای اینکه بتونیم از set lenient استفاده کنیم باید از حالت gson builder برای اضافه کردن تنظیمات خاص استفاده کنیم، که gson رو با حالت lenient درست میکنیم.

برای وابستگی بعدی میایم موارد log یا log interceptor رو قرار میدیم.

مثلاً میخوایم ببینیم این api که call میکنیم بدنه اش چیه و در قالب چه چیزی فرستاده میشه و دریافت میشه، بتونیم ایراداتش رو ببینیم که کار میکنه یا نه، آیا چیزهایی که نیاز داریم رو بصورت 100% میفرسته یا دریافت میکنه، یا مثلاً برای هرچیزی که به error خورد، بتونیم اون error رو به backend کار بدیم تا اونو fix کنه، یا مثلاً به error هایی مثل سری 400 خورد، دلیلش رو بفهمیم که چرا به همچین error یی برخورد کردیم و برای همچین مواردی از log interceptor استفاده میکنیم.

برای log interceptor اکثراً در 80 تا 90 درصد مواقع از body استفاده میکنیم که میاد و بدنه اون response رو به ما میده، ولی اینجا ما هم از body و هم header استفاده میکنیم و جفتشون هم از یه جنس هستن و برای هرکدوم از named استفاده میکنیم که موقع استفاده مشخص باشن.

![My image](https://github.com/Developers0101/notes-android-course/raw/main/images/%D9%87%DB%8C%D9%84%D8%AA_files2/image143.png)

متدمون رو از نوع Log interceptor http قرار میدیم.

![My image](https://github.com/Developers0101/notes-android-course/raw/main/images/%D9%87%DB%8C%D9%84%D8%AA_files2/image144.jpg)

یه بخش داره به اسم level ، که ما توی level سطح اون log یی که میخوایم رو میگیریم، مثلاً میگیم body رو به ما بده یا header رو به ما بده یا هرچیزی که نیاز داریم رو به ما بده.

![My image](https://github.com/Developers0101/notes-android-course/raw/main/images/%D9%87%DB%8C%D9%84%D8%AA_files2/image145.png)

که ما level رو از نوع headers انتخاب میکنیم.

میایم و یه مدل دیگه هم از این log ولی برای body درست میکنیم.

![My image](https://github.com/Developers0101/notes-android-course/raw/main/images/%D9%87%DB%8C%D9%84%D8%AA_files2/image146.png)

الان ما هم header و هم body رو داریم که جفتشون از نوع okhhtp 3 و http logging interceptor هستن و چون یه نوع هست برای اینکه بتونیم ازشون استفاده کنیم باید از Named استفاده کنیم.

![My image](https://github.com/Developers0101/notes-android-course/raw/main/images/%D9%87%DB%8C%D9%84%D8%AA_files2/image147.png)

میایم و براشون 2 تا اسم توی const تعریف میکنیم و به هرکدوم از متدها میدیم.

![My image](https://github.com/Developers0101/notes-android-course/raw/main/images/%D9%87%DB%8C%D9%84%D8%AA_files2/image148.png)





قسمت 40

الان برای تنظیمات و config retrofit در ماژلمون به 2 تا چیز دیگه نیاز داریم که یکی client و دومی هم خود retrofit هست.

client نیاز به یکسری موارد و وابستگی داره مثل time و ما برای اینکه بتونیم این وابستگی رو تامین کنیم باید اونرو توی constructor قرار بدیم، ما علاوه بر time به log header و log body interceptor نیاز داریم چون میان وضعیت api مارو با log نشون میدن که اوکی هست یا نه که میایم و اونهارو هم داخل constructor قرار میدیم.

![My image](https://github.com/Developers0101/notes-android-course/raw/main/images/%D9%87%DB%8C%D9%84%D8%AA_files2/image149.png)

Client رو singleton در نظر میگیریم، چون فقط میخوایم یکبار اجرا بشه.

اولین موردی که در constructor قرار میدیم time هست که از نوع long هست، وقتی مینویسیم میره از بین متدهایی که برای تزریق وابستگی نوشته بودیم میبینه کدوم long هست و خودش میاد تشخیص میده:

![My image](https://github.com/Developers0101/notes-android-course/raw/main/images/%D9%87%DB%8C%D9%84%D8%AA_files2/image150.png)

![My image](https://github.com/Developers0101/notes-android-course/raw/main/images/%D9%87%DB%8C%D9%84%D8%AA_files2/image151.png)

بعد میایم و header, body رو قرار میدیم که از نوع http log interceptor در نظر میگیریم.

![My image](https://github.com/Developers0101/notes-android-course/raw/main/images/%D9%87%DB%8C%D9%84%D8%AA_files2/image152.png)

چون هردوتا از یک نوع بودن با استفاده از named میایم هرکدوم رو مشخص میکنیم.

![My image](https://github.com/Developers0101/notes-android-course/raw/main/images/%D9%87%DB%8C%D9%84%D8%AA_files2/image153.png)

بعد میایم و متدمون رو از نوع ok http client در نظر میگیریم.

![My image](https://github.com/Developers0101/notes-android-course/raw/main/images/%D9%87%DB%8C%D9%84%D8%AA_files2/image154.png)

بعد میایم و interceptor هارو با add interceptor اضافه میکنیم و header, body رو بهش میدیم.

` `![My image](https://github.com/Developers0101/notes-android-course/raw/main/images/%D9%87%DB%8C%D9%84%D8%AA_files2/image155.png)

بعد میایم و timeout هامون که شامل connection و read و write بود رو میدیم که از time که داخل constructor قرار دادیم استفاده میکنیم و مدت زمان و time unit رو بر حسب ثانیه در نظر میگیریم.

ما میتونیم بعد همه ی این کدها از build استفاده کنیم و کارو تموم کنیم، ولی ok http به ما یه config و تنظیمات خوب میده، که میگه زمانی که با failed روبرو شد و به هر دلیلی سرور response رو به ما نداد، یکبار دیگه هم تلاش کن، و اگه بعد اون یکباری که خودت هم چک کردی و اگه اوکی نشد بیا و یه error یی رو به کاربر نشون بده.

` `![My image](https://github.com/Developers0101/notes-android-course/raw/main/images/%D9%87%DB%8C%D9%84%D8%AA_files2/image156.png)

با retry on connection failure اگه مقدارشو true قرار بدیم زمانی که یکبار failed بشه میاد و یکبار دیگه خودش چک میکنه.

![My image](https://github.com/Developers0101/notes-android-course/raw/main/images/%D9%87%DB%8C%D9%84%D8%AA_files2/image157.jpg)

و بعد میایم و build میکنیم.

با log Header میتونیم تشخیص بدیم که اگه یه روزی backend کار گفته که header داره اشتباه میاد، بتونیم header رو کامل ببینیم.

Log body هم هرچیزی که کامل در قالب header هم میفرستیم رو میاد و کامل بهمون نشون میده و میاد جزئیات api رو کامل نشون میده، و چطور میشه ازش استفاده کرد. 

الان میایم و تنظیمات retrofit رو مینویسیم.

Retrofit نیاز داره به base url ، client ، و اگه تنظیمات خاصی برای gson در نظر گرفته باشیم:

![My image](https://github.com/Developers0101/notes-android-course/raw/main/images/%D9%87%DB%8C%D9%84%D8%AA_files2/image158.jpg)

` `میتونیم تو create بهش بدیم، که ما با set lenient براش تنظیمات خاص در نظر گرفتیم.

وداخل ورودی constructor میایم و base url, client, gson ره بهش میدیم.

![My image](https://github.com/Developers0101/notes-android-course/raw/main/images/%D9%87%DB%8C%D9%84%D8%AA_files2/image159.jpg)

چون retrofit هم یه کتابخونه ی سنگین هست اونو هم singleton مینویسیم تا فقط یکبار call بشه برای ما و ما وابستگی هارو به retrofit تزریق کردیم.

زمانی که قبلاً داشتیم از api services توی retrofit استفاده میکردیم اونو تعریف کرده بودیم:

![My image](https://github.com/Developers0101/notes-android-course/raw/main/images/%D9%87%DB%8C%D9%84%D8%AA_files2/image160.jpg)

و گفته بودیم برای اینکه بتونیم از تنظیمات api client مون استفاده کنیم اونو در قالب api services تعریف میکنیم، که وقتی اینطوری ازش استفاده کردیم یعنی یه وابستگی، و ما بجای اینکار میایم و همرو داخل ماژول و داخل خود retrofit تعریف میکنیم.

![My image](https://github.com/Developers0101/notes-android-course/raw/main/images/%D9%87%DB%8C%D9%84%D8%AA_files2/image161.png)

بخاطر همین میایم و نوع بازگشتی متد retrofit مون رو از نوع api services درنظر میگیریم، چون ما بواسطه ی این api services هست که میتونیم توی فرگمنت یا اکیتویتی call بزنیم، enqueue بزنیم و اطلاعات رو بگیریم و نشون بدیم.

` `![My image](https://github.com/Developers0101/notes-android-course/raw/main/images/%D9%87%DB%8C%D9%84%D8%AA_files2/image162.png)

میایم و با استفاده از retrofit . builder و base url, client رو بهش میدیم و بعد میایم و بهش convertor رو بهش میدیم و اگه تنظیمات خاصی داشته باشیم میتونیم داخل create ش قرار بدیم که ما میایم و داخل create و gson رو بعنوان تنظیمات خاص بهش پاس میدیم و بعد build میکنیم.

![My image](https://github.com/Developers0101/notes-android-course/raw/main/images/%D9%87%DB%8C%D9%84%D8%AA_files2/image163.jpg)

ولی ما گفتیم که api services رو برای ما برگشت بده و دقیقاً همونطوری که قبلاً توی activity و retrofit رو تعریف میکردیم، تعریف میکنیم و داخل create کلاس api services رو بهش میدیم.

![My image](https://github.com/Developers0101/notes-android-course/raw/main/images/%D9%87%DB%8C%D9%84%D8%AA_files2/image164.png)

تنظیمات کلی api ماژول مربوط به retrofit .

الان نیاز داریم به api repository ، چون ریپازیتوری وظیفه ی تامین کردن اطلاعات رو برعهده داره و نیاز داریم که ریپازیتوری ما به api service و endpoint ما وصل بشه و اطلاعات رو برای ما بفرسته.

یه پوشه ی repository و یه کلاس api repository درست میکنیم.

![My image](https://github.com/Developers0101/notes-android-course/raw/main/images/%D9%87%DB%8C%D9%84%D8%AA_files2/image165.png)

داخل constructor api repository برای اینکه به endpoint مون دسترسی داشته باشیم باید اونو تعریف کنیم.

private ش میکنیم چون فقط میخوایم اینجا تعریفش کنیم و val درنظر میگیریم که بهش دسترسی داشته باشیم.

![My image](https://github.com/Developers0101/notes-android-course/raw/main/images/%D9%87%DB%8C%D9%84%D8%AA_files2/image166.png)

براش یه متد با نام دلخواه در نظر میگیریم و با استفاده از api به متد movies list مون که مربوط به اون endpoint مون میشه دسترسی پیدا میکنیم و قرار میدیم.

الان ما از حالت عادی و بدون hilt استفاده کرده بودیم که با inject میایم و از hilt استفاده میکنیم و وابستگی رو تزریق میکنیم:

![My image](https://github.com/Developers0101/notes-android-course/raw/main/images/%D9%87%DB%8C%D9%84%D8%AA_files2/image167.jpg)

برای scope خود repository هم activity قرار بدیم بهتر، چون api های مختلف تو صفحات مختلف هستن و ازشون استفاده میکنیم، و مثلاً get all movies رو قرار در صفحه ی اول نشون بدیم که لیست همه ی فیلم هارو نشون بده، و یه api دیگه داریم که وقتی وارد جزئیات شدیم، میخوایم جزئیات اون فیلم رو نشون بدیم، و اگه این scope ش از نوع activity scope باشه خیلی بهتر، چون قرار یکسری از این api ها فقط توی یکسری از صفحات کار کنن، و اگه ننویسیم هم error یی نمیده.

خلاصه توضیحات api repository, api module :

اگه الان داخل کلاس api repository روی علامت ![My image](https://github.com/Developers0101/notes-android-course/raw/main/images/%D9%87%DB%8C%D9%84%D8%AA_files1/image168.jpg) بزنیم مارو میبره به api module و به متد retrofit چون داخل رتروفیت از api services استفاده کردیم و داخل ریپازیتوری مون به api services برای تامین اطلاعات نیاز داریم و به این شکل برای ما تامین کردن اطلاعات رو.

` `و api service اومد داخل متد رترفیت و کل رتروفیت رو تعریف کرده که رتروفیت برای تعریف نیاز به base url, gson, client داره.

خود client نیاز به time داره و 2 تا interceptor .

که بقیه ی مواردش رو که نیاز داشت داخل ماژول تعریف کرده بودیم.

بعد همه ی مواردی که نیاز بود رو برای ما تامین میکنه و بعد با api services داخل ریپازیتوری در اختیار ما قرار میده و ما در نهایت میتونیم ازش داخل کلاس activity مون استفاده کنیم.

![My image](https://github.com/Developers0101/notes-android-course/raw/main/images/%D9%87%DB%8C%D9%84%D8%AA_files2/image169.jpg)

برای استفاده از اینترنت هم بهش دسترسی میدیم.



قسمت 41

برای لیست فیلم هامون یه adapter نوشتیم.

![My image](https://github.com/Developers0101/notes-android-course/raw/main/images/%D9%87%DB%8C%D9%84%D8%AA_files2/image170.jpg)

متد get item view type برای اینه که آیتم هامون duplicate نشه.(تکراری اول قسمت 14 بخش رتروفیت گفته شده)

![My image](https://github.com/Developers0101/notes-android-course/raw/main/images/%D9%87%DB%8C%D9%84%D8%AA_files2/image171.png)

برای تامین وابستگی میایم و به adapter مون یه constructor میدیم و قبلش یه inject میزاریم.

یه زمانی نیاز داریم که توی کلاس adapter از context استفاده کنیم، مثلاً زمانی که از glide برای بارگذاری تصاویر استفاده میکنیم نیاز به context داریم.

![My image](https://github.com/Developers0101/notes-android-course/raw/main/images/%D9%87%DB%8C%D9%84%D8%AA_files2/image172.png)

در حالت عادی و بدون استفاده از hilt به این صورت میومدیم و context رو تعریف میکردیم و بعد از parent میگرفتیم یا:

![My image](https://github.com/Developers0101/notes-android-course/raw/main/images/%D9%87%DB%8C%D9%84%D8%AA_files2/image173.png)

یا میتونستیم توی constructor تعریفش کنیم و بعد هرجا که میخواستیم ازش استفاده کنیم تو constructor میومدیم و context رو بهش میدادیم.

ولی این روش ها مناسب نیستن و وابستگی داره و ما از هیلت استفاده میکنیم که وابستگی هارو برامون تامین کنه.

![My image](https://github.com/Developers0101/notes-android-course/raw/main/images/%D9%87%DB%8C%D9%84%D8%AA_files2/image174.jpg)

اگه نیاز به context داشته باشیم به اینصورت میایم و با application context وابستگیمون رو تامین میکنیم.

الان ما برای استفاده از retrofit و نمایش اطلاعاتمون توی activity به 2تا وابستگی نیاز داریم که اولی adapter هست و دومی repository که عملیات مارو برای api انجام داده که ما بتونیم دسترسی داشته باشیم و کارهای api رو انجام بدیم.

![My image](https://github.com/Developers0101/notes-android-course/raw/main/images/%D9%87%DB%8C%D9%84%D8%AA_files2/image175.jpg)

قبلاً برای دسترسی به api میومدیم و با lazy اونو تعریف میکردیم:

![My image](https://github.com/Developers0101/notes-android-course/raw/main/images/%D9%87%DB%8C%D9%84%D8%AA_files2/image176.jpg)

و بعد به این صورت ازش استفاده میکردیم:

![My image](https://github.com/Developers0101/notes-android-course/raw/main/images/%D9%87%DB%8C%D9%84%D8%AA_files2/image177.png)

ولی الان و با استفاده از hilt دیگه نیازی نیست که به این صورت تعریف بشه و بعد داخل متغییر call movies api قرار بدیم، بلکه با استفاده از repository و بصورت مستقیم ازش استفاده میکنیم:



![My image](https://github.com/Developers0101/notes-android-course/raw/main/images/%D9%87%DB%8C%D9%84%D8%AA_files2/image178.jpg)

با استفاده از repository میایم و متد get all movies رو میزنیم و داخل enqueue نیاز به object داریم که ازنوع callback هست و Callback یی که انتخاب میکنیم حتماً باید از نوع retrofit 2 باشه.

همه ی کدها تکراری هست و درقسمت رتروفیت زده شده و توضیحات کامل داده شده.

![My image](https://github.com/Developers0101/notes-android-course/raw/main/images/%D9%87%DB%8C%D9%84%D8%AA_files2/image179.png)

فقط در قسمت on failure میایم و از loge استفاده میکنیم و یه tag درست میکنیم.

![My image](https://github.com/Developers0101/notes-android-course/raw/main/images/%D9%87%DB%8C%D9%84%D8%AA_files2/image180.png)

کل کدهایی که در activity زدیم.

برای اینکه بتونیم موقع load شدن تصاویر یه حالت افکت بهش بدیم که جزء lambda expression ها هست و از cross fade که یه حالت محو شدن داره برای بارگذاری تصاویر استفاده میکنیم.

![My image](https://github.com/Developers0101/notes-android-course/raw/main/images/%D9%87%DB%8C%D9%84%D8%AA_files2/image181.png)

Cross fade 2 تا آیتم داره که باید اولی رو true کنیم تا نشون بده و دومی زمان هست برحسب میلی ثانیه که اگه ندیم خودش بصورت پیشفرض که 500 میلی ثانیه هست استفاده میکنه.



قسمت 42

این جلسه در مورد scope هاست و 2تا scope singleton, activity رو مورد بررسی قرار میدیم.

اینکه چرا وقتی از singleton استفاده میکنیم در طول اجرای اپلیکیشن کلاً یکبار تعریف میشه و در دسترس هست و اگه activity scope تعریف بشه به ازای lifecycle اون activity یکبار ساخته میشه و اگه یه اکتیویتی دیگه باز بشه دوباره ساخته میشه و این مورد برای fragment و view model و service و بقیه ی مواردی که هست با توجه به اون مورد و باتوجه به lifecycle ش تا موقعی که در دسترس هست مثل activity یکبار تعریف میشه و وقتی مثل activity به چیز دیگه ایی بره دوباره ساخته میشه و باهم فرقی ندارن.

ما 2تا activity داریم که با زدن یک دکمه از activity home میریم به profile و با log مشخص کنیم که برای scope بصورت singleton یا activity چه اتفاقی میفته.

![My image](https://github.com/Developers0101/notes-android-course/raw/main/images/%D9%87%DB%8C%D9%84%D8%AA_files2/image182.jpg)  

میایم برای api service که قبلاً داشتیم و بصورت activity scoped بود استفاده میکنیم و هیچ فرقی نداره میتونیم از متدهای داخل module استفاده کنیم یا از adapter و هیچ فرقی نداره.

میایم و api repository رو 2بار در activity home و 2بار هم در activity profile تعریف میکنیم و اگه یکبار تعریف کنیم یه بلوک در رم براش ذخیره میشه که مشخص نمیشه که به ازای هر تعریف در رم یکسان ذخیره میشه یا نه بخاطر همین با 2 تا اسم مختلف ذخیره میکنیم تا نتیجه مشخص بشه، که یکسان هستن یا نه.

![My image](https://github.com/Developers0101/notes-android-course/raw/main/images/%D9%87%DB%8C%D9%84%D8%AA_files2/image183.jpg)

بعد همین 2تا inject رو در activity profile هم قرار میدیم.

برای اینکه بفهمیم چیزهایی که توی رم ذخیره شده همون location هستن، کاتلین یک کدی به ما میده به اسم hash code که ما توسط hash code میتونیم بفهمیم location مون توی رم یکی هست یا نه.

![My image](https://github.com/Developers0101/notes-android-course/raw/main/images/%D9%87%DB%8C%D9%84%D8%AA_files2/image184.jpg)

میایم و توی constants یه tag درست میکنیم.

![My image](https://github.com/Developers0101/notes-android-course/raw/main/images/%D9%87%DB%8C%D9%84%D8%AA_files2/image185.jpg)

میایم و با استفاده از loge و hash code های repository 1,2 رو میگیریم و به string تبدیل میکنه تا نشون بده در logcat .

میخوایم ببینیم که به ازای هرکدوم از متغییرهایی که تعریف کردیم یه بلوک در رم رو به خودش اختصاص میده یا برای هردوتا یکی هست.

![My image](https://github.com/Developers0101/notes-android-course/raw/main/images/%D9%87%DB%8C%D9%84%D8%AA_files2/image186.jpg)

بعد براش یه intent مینویسیم که بریم به activity profile .

![My image](https://github.com/Developers0101/notes-android-course/raw/main/images/%D9%87%DB%8C%D9%84%D8%AA_files2/image187.jpg)

وقتی اجرا میگیریم میاد و api repository 1,2 رو عین هم چاپ میکنه و hash code هاشون یکی هست و اگه 1000 تای دیگه هم داشته باشیم hash code همشون یکی هست و محل ذخیره همشون توی رم یکی هست.

حالا میخوایم بواسطه زدن دکمه بریم به activity دوم و چون برای repository از activity scoped استفاده کردیم باید hash code های activity 1,2 باهم فرق داشته باشه.

![My image](https://github.com/Developers0101/notes-android-course/raw/main/images/%D9%87%DB%8C%D9%84%D8%AA_files2/image187.jpg)

چون یه scope یا محدوده ی اجرایی برای activity1 در نظر میگیره و وقتی از این صفحه میریم به صفحه ی بعد این activity stop میشه و چرخه ی حیاتش هم on stop میشه و چون در activity 2 یه activity دیگه میاد و create میشه، و وقتی یه اکتیویتی جدید ساخته شد، میاد و یه hash code جدید میسازه، چون scoped مون براساس activity هست.

بخاطر همین hash code های home activity با profile activity باهم فرق دارن و به ازای هر activity یه دونه object از api repository برای ما ساخته میشه.

![My image](https://github.com/Developers0101/notes-android-course/raw/main/images/%D9%87%DB%8C%D9%84%D8%AA_files2/image187.jpg)

میایم و scope کلاس api repository رو به singleton تغییر میدیم و اجرا میگیریم.

![My image](https://github.com/Developers0101/notes-android-course/raw/main/images/%D9%87%DB%8C%D9%84%D8%AA_files2/image187.jpg)

وقتی اجرا میگیریم در حالت singleton در هر 2تا activity hash code ها یکی هستن، یعنی در طول کل اپلیکیشن یکبار اومده و اونرو تعریف کرده، و توی هرصفحه ایی که میخوایم ازش استفاده کنیم نمیاد از اول تعریف کنه، میره به اون location یی که براش توی ram در نظر گرفته که ذخیره اش کنه، میره بهش اشاره میکنه و اونو در دسترس ما قرار میده.

بخاطر همین زمانی که میخوایم محدوده scope هارو مشخص کنیم باید در نظر بگیریم که چیزی که میخوایم استفاده کنیم آیا در طول کل زمانی که اپلیکیشن مون اجراست، نیاز هست که یکبار ساخته بشه یا به ازای هر activity, fragment, service, view model و بقیه موارد، بیاد و از اول ساخته بشه.

یکی از راهکارهای تشخیص scope اینه که کدهارو trace کنیم.


