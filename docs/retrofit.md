---
layout: default
title: رتروفیت
nav_order: 3
---
# رتروفیت

قسمت 10:

برای گرفتن اطلاعات از سمت سرور و ارتباط با سرور و داشتن اپلیکیشن های آنلاین، از کتابخونه retrofit استفاده میکنیم که سرعتش نسبت به کتابخونه هایی مثله vally یا ok http خیلی بیشتر و کار باهاش راحتتره.

والد رتروفیت و بیسش از ok http هستش.

برای اینکه بتونیم بصورت basic از retrofit استفاده کنیم، نیاز به 2تا فایل داره:

1- فایلی که ما اطلاعات یا root ها یا مسیرهای سمت سرورمون یا endpoint هامونو داخلش قرار میدیم یعنی کلاس اینترفیس api services.

2- تنظیمات مربوط به retrofit داخل یه کلاس قرار میدیم به اسم api client.

متدهای http که retrofit پشتیبانی میکنه شامل:

GET, POST, PUT, PATCH, DELETE, OPTIONS, HEAD

زمانی که میخوایم از سرور اطلاعات رو بگیریم، همه ی اینها روی پروتکل های http هستن، ویکسری متدهای ارتباطی وجود داره بین دستگاه یا پلتفرمی که میخواد استفاده کنه با متدهای http .

متدهای http متدهایی هستن که هر پلتفرمی که میخواد باهاش کار بکنه، مثلاً بخواد اطلاعات آنلاین بگیره(فرقی نداره موبایل باشه، فرانت باشه یا ...)، کلاً هرچیزی که بخواد اطلاعات رو از سمت سرور بگیره و نشون بده توسط این متدهای http باید به اون سرور وصل بشه و اطلاعات رو بگیره.

تمام متدهای http سمت سرور درخواستی میفرسته، که به پاسخی که دریافت میکنه میگن response . 

GET : get برای دریافت اطلاعات از سمت سرور استفاده میشه، وقتی روی یک آیتمی یا محصولی، کلیک کنیم یکسری اطلاعات برای سرور فرستاده میشه و نتیجه ایی که سرور به ما میده بهش میگن response ، ونتیجه میتونه اطلاعات محصول باشه یا حتی خطا باشه.

GET برای اینه که ما یکسری موارد رو برای سرور بفرستیم و منتظر دریافت اطلاعات اون باشیم.

مواردی که GET ارسال میکنه توی url قرار دارده:

<https://moviesapi.ir/api/v1/movies?page=1>

اینجا با page 1 اومده اطلاعات رو در قالب get برای سمت سرور فرستاده و در قالب url فرستاده که از نظر امنیتی GET مناسب نیست و زمانی از GET استفاده میکنیم که ازنظر امنیتی مهم نباشه مثل صفحه محصولات یا لیستمون و ... .

POST : برای ارسال اطلاعات سمت سرور استفاده میشه و اطلاعاتی که از نظر امنیتی مهم هستن، مثل پسورد و POST میاد اطلاعات رو در قالب بدنه یا body ارسال میکنه.

اطلاعات در GET در قالب url فرستاده میشه، ولی در POST در قالب بدنه یا body فرستاده میشه.

<https://moviesapi.ir/api/v1/movies>

از POST زمانی استفاده میشه که بخوایم یکسری اطلاعات زیاد حالا چه بصورت امن یا بصورتی که در url مشخص نباشه و شلوغ نشه بفرستیم سمت سرور.

PUT : PUT برای آپدیت اطلاعات استفاده میشه، و اطلاعات رو مثل POST در قالب body یا بدنه میفرسته سمت سرور.

<a name="_hlk129260787"></a>[https://moviesapi.ir/api/v1/profile]()

PATCH : PATCH هم برای آپدیت و بروزرسانی اطلاعات استفاده میشه.

فرق PUT, PATCH در اینه که PUT وقتی میخواد آپدیت کنه تموم اطلاعاتی که هست رو پاک میکنه و دوباره override میکنه، ولی PATCH فقط اون موردی که تغییر کرده رو آپدیت میکنه، فرق دیگه شون اینکه که PUT اطلاعات رو در قالب body میفرسته ولی PATCH در قالب url میفرسته.

[https://moviesapi.ir/api/v1/profile?phone=09121112233](https://moviesapi.ir/api/v1/movies)

DELETE : برای حذف کردن اطلاعات استفاده میشه، که اکثراً اطلاعات رو در url میفرستن.

<https://moviesapi.ir/api/v1/profile?id=>5

OPTIONS, HEAD : OPTIONS برای حالتی هست که متدهای خاص یک url رو برای ما برمیگردونه و مثلاً اگه متدهای خاصی داشته باشه به ما اجازه میده ازشون بتونیم استفاده کنیم.

\*(متد OPTIONS یکی از متدهای HTTP که برای دریافت اطلاعاتی درباره‌ی مجوزها و مشخصات سرور ارسال میشه، و به سرور اجازه میده که بر اساس این اطلاعات، برای درخواست‌های بعدی پاسخ مناسبی ارسال کنه.

معمولاً درخواست OPTIONS به عنوان یک پیش‌نیاز برای ارسال درخواست‌های دیگه به یک منبع API استفاده می‌شه. برای مثال، درخواست OPTIONS می‌تونه برای بررسی دسترسی‌های مجاز به یک منبع API، بررسی نحوه پشتیبانی از تعدادی از متدهای HTTP (مثل GET و POST) و بررسی نحوه پشتیبانی از مجوزها و سیاست‌های امنیتی رو شامل بشه.)\*

HEAD برای دریافت اطلاعات مثل GET عمل میکنه و با این تفاوت که response body رو نداره و HEAD برای اینکه بفهمیم توی اون متد یا اون root که میخوایم بفرستیم چه چیزهایی برای Header نیازه.

وقتی میخوایم درخواست هارو بفرستیم سمت سرور از چندتا متد استفاده میکنیم که این متدها شامل:

Header, Query, Body, Path, Field, URL 

Header یا سربرگ: زمانی استفاده میشه که میخوان authenticate یا احراز هویت کنن، مثل رفتن به صفحه ی پروفایل و دسترسی به اطلاعات اون، که با استفاده از همین هدر یا احراز هویت قابل تشخیص هست و در header یکسری اطلاعاتی که بک اند نیاز داره مثل token به اون root میفرستیم که بک اند با توجه به این هدر تشخیص میده این کاربر کی هست و اجازه دسترسی به اون اطلاعات یا root رو داره یا نه.

هدر اول از همه است و برای اینه که بفهمیم کاربر اجازه دسترسی داره یا نه و اینکه اطلاعات رو درقالب json میخوایم.

Query : برای ارسال اطلاعات توی URL هست و هرجا توی url از ؟ علامت سوال استفاده شد یعنی داره از Query استفاده میکنه.

Body : ارسال اطلاعات در بدنه هست که در url مشخص نیست.

Path : یک روش دیگه برای ارسال اطلاعات هست ولی در url ، و یک قسمتی از url رو تغییر میده و توی اون قسمت خاص ما میتونیم اون فیلد خاصی که مد نظرمون هست رو بفرستیم و روش تشخیصش استفاده از { } هست.

از query معمولا برای فیلتر و sort و اینجور چیزا استفاده میشه.

Field : یکی دیگه از متدها برای ارسال اطلاعات که در قالب form-urlencoded قرار میگیره که مربوط به بک اند میشه و هرجا که نیاز بود باید علاوه بر @Field از @FormUrlEncoded هم استفاده کنیم.

URL : تموم این مسیرها و root هایی که تا الان گفته شده استاتیک بودن، زمانی که ما از URL استفاده کنیم میتونیم یکسری root های داینامیک رو بفرستیم و نسبت به اون root های داینامیک اطلاعات دریافت کنیم.

قسمت 11

وقتی یک api رو صدا میزنیم و ازش استفاده میکنیم بهش میگن call کردن.

هروقتی از علامت کروشه [ ] استفاده شد یعنی مقدارش از نوع لیست و موارد داخل list میشن object آبجکت:

![My image](https://github.com/Developers0101/notes-android-course/raw/main/images/%D8%B1%D8%AA%D8%B1%D9%88%D9%81%DB%8C%D8%AA_files/image001.jpg)

![My image](https://github.com/Developers0101/notes-android-course/raw/main/images/%D8%B1%D8%AA%D8%B1%D9%88%D9%81%DB%8C%D8%AA_files/image002.png)

توی این روت درخواست باید با GET زده بشه و از نوع Query هست چون علامت ؟ سوال داره.

چیزی که بک اند به ما میده به این صورت هست:

https://moviesapi.ir/api/v1/movies?page={page}

ولی موقعه ی استفاده از root به این صورت میشه:

<https://moviesapi.ir/api/v1/movies?page=1>

که به response که به ما میده JSON هم میگن.

به داکیمونت هایی که بک اند دولوپر ها میدن میگن Swagger .

برای اینکه بتونیم عکس رو سمت سرور بفرستیم چندین روش داریم مثل base 64 و multi part و ... .

Base 64 عکس رو تبدیل میکنه به یه string خیلی بزرگ و طولانی و بعد اون string رو میفرسته سمت سرور و بعد بک اند کار میاد این string رو decode میکنه و تبدیل به عکس میکنه.

Multi part میاد عکس رو به پارت های مختلف تقسیم میکنه بعد بصورت فایل میفرسته سمت سرور.

Path داخل { } آکولاد قرار میگیره تا ما بتونیم custom url یا قسمتی از url رو تغییر بدیم:

https://moviesapi.ir/api/v1/movies/{movie\_id}

که موقع استفاده به این صورت استفاده میکنیم:

https://moviesapi.ir/api/v1/movies/2

وقتی اطلاعات رو در قالب Path میفرستیم(movie\_id) کل اون عبارت داخل { } رو پاک میکنه و بجاش عدد رو جایگزین میکنه(2) که یعنی قسمتی از url توسط Path ادیت شد.

یه حالت هم هست که فقط root رو خالی بدون هیچ چیزی وفقط مثلاً با GET ارسال میکنیم و سرور به ما response میده:

https://moviesapi.ir/api/v1/genres

ترکیب حالت های Query, Path باهم:

https://moviesapi.ir/api/v1/genres/{genre\_id}/movies?page={page}

که موقع استفاده به این صورت میشه:

https://moviesapi.ir/api/v1/genres/1/movies?page=2

اکثراً query ها آخر میان ولی path مهم نیست میتونه اول آخر یا هرجای url رو که بخوایم edit کنیم.

فرق بین query و path : معمولا وقتی میخان یه چیزی رو شناسایی(identify) کنن از path استفاده میکنن.

مثلا توی https://moviesapi.ir/api/v1/movies/{movie\_id}

اگه {movie\_id} رو پاک کنیم و بجاش یه عدد بنویسیم مثلا 2، اونوقت اطلاعات ژانر فیلم های رو که idش 2 هست رو به ما نشون میده.

فرق دیگه اش اینه که زمانی که در path چیزی رو قرار میدیم، اگه اون مورد وجود نداشته باشه، مثلاً یه id که اصلاً وجود نداشته باشه در url مون چون داره بدنه ی اصلی url رو تغییر میده، در path با خطای 404 روبرو میشه، ولی اگه url مون مشکلی نداشته باشه و از query که داریم استفاده میکنیم اون query وجود نداشته باشه، دیگه اون url مون 404 نمیده، اگه response یی وجود داشته باشه، response رو بهمون میده و اگه نداشته باشه میگه response وجود نداره، اگه در query url رو اشتباه بفرستیم دیگه خطای 404 نمیده، ولی برای path مهم و اگه url رو اشتباه بفرستیم خطای 404 میده و باید اونو هندل کنیم. 

موارد استفاده از PUT, PATCH, DELETE هم مثل GET, POST هستن و هیچ فرقی نداره.

قسمت 12

Retrofit نیاز به 2 تا فایل داره :

که اولی api service هست که root و endpoint و هرچی که نیاز داریم رو در اون قرار میدیم.

دومی میشه api client که config و تنظیمات مربوط به retrofit که در اون قرار میدیم.

کتابخونه هایی که برای استفاده از retrofit در گردل قرار میدیم:

![My image](https://github.com/Developers0101/notes-android-course/raw/main/images/%D8%B1%D8%AA%D8%B1%D9%88%D9%81%DB%8C%D8%AA_files/image003.png)

این کتابخونه ی اصلی خود retrofit هست.

Response هایی که سرور به ما میده JSON جی سون هست و چیزی که این هارو برای retrofit قابل فهم میکنه که بتونه ازش استفاده کنه، کتابخونه ی Gson هست که اینو خود گوگل نوشته.

JSON یک استانداردی های هست که همه جا هست و همه ی موارد و response هارو برای ما برمیگردونه و Gson برای خود اندروید.

![My image](https://github.com/Developers0101/notes-android-course/raw/main/images/%D8%B1%D8%AA%D8%B1%D9%88%D9%81%DB%8C%D8%AA_files/image004.png)

این کتابخونه خود Gson هست.

![My image](https://github.com/Developers0101/notes-android-course/raw/main/images/%D8%B1%D8%AA%D8%B1%D9%88%D9%81%DB%8C%D8%AA_files/image005.png)

و این کتابخونه، کتابخونه ایی هست که JSON رو میگیره و تبدیل میکنه به Gson و برای رتروفیت قابل فهم میکنه.

![My image](https://github.com/Developers0101/notes-android-course/raw/main/images/%D8%B1%D8%AA%D8%B1%D9%88%D9%81%DB%8C%D8%AA_files/image006.png)

ما به واسطه کتابخونه okhttp و client میتونیم یکسری تنظیمات بیشتری رو برای retrofit مون اعمال کنیم مثلاً خود رتروفیت تا 10 ثانیه منتظر درخواست میمونه و اگه نتیجه نگرفت، میاد کنسل میکنه که ما میتونیم تایمشو تغییر بدیم و کلی تنظیمات دیگه که با okhttp میتونیم روی رتروفیت اعمال کنیم.

ما برای اینکه بتونیم به response و JSON که سرور برای ما میفرسته و توسط convertor به Gson تبدیل میشه دسترسی داشته باشیم نیاز به یک کلاس مدل داریم، که در قالب این کلاس مدل، رتروفیت اطلاعات رو دریافت میکنه و در اختیار ما قرار میده تا بتونیم ازش استفاده کنیم.

یه package به اسم model درست میکنیم و کلاس Response هامونو توش قرار میدیم.

تنظیمات مربوط به پلاگین json to kotlin class که متغییر رو روی val میزاریم، بعد روی nullable میزاریم که بتونیم null بودن رو چک کنیم، بعد روی حالت ست نکردن default value تنظیم میکنیم:

![My image](https://github.com/Developers0101/notes-android-course/raw/main/images/%D8%B1%D8%AA%D8%B1%D9%88%D9%81%DB%8C%D8%AA_files/image007.png)

بعد روی قسمت Annotaion روی Gson قرار میدیم:

![My image](https://github.com/Developers0101/notes-android-course/raw/main/images/%D8%B1%D8%AA%D8%B1%D9%88%D9%81%DB%8C%D8%AA_files/image008.png)

بعد تو قسمت other تیک inner class رو هم میزنیم:

![My image](https://github.com/Developers0101/notes-android-course/raw/main/images/%D8%B1%D8%AA%D8%B1%D9%88%D9%81%DB%8C%D8%AA_files/image009.png)

که اگه چندین کلاس داشتیم، همه رو یکجا و بصورت منسجمتر و تو در تو نشون بده.

موقع نام گذاری فایل JSON مون هم با Response شروع میکنیم که بدونیم این کلاسمون مربوط به response هامون میشه.

یه package دیگه به اسم server یا services درست میکنیم و داخل این پوشه فایل های مربوط به root ها و تنظیمات کلاس رتروفیت رو داخلش قرار میدیم.

فایلی که مربوط به api ها و root هامون میشه رو با یه کلاس interface به اسم ApiServices میسازیم.

Base url یا url پایه یا مسیر پایه و مشترک سایتمون رو مشخص میکنیم و base url اون قسمت از آدرسی هست که در url در صفحات مختلف تا یک قسمتیش بصورت مشترک یکی هست و تکرار میشه:

<https://moviesapi.ir/api/v1/>

در این سایت که تا v1/ در همه ی قسمت های سایت یکی و تکراری هست که ما به عنوان base url در نظر میگیرم.

قسمت های بعد v1/ میشه url یا مسیرهایی که میخوایم بهش دسترسی پیدا کنیم و میخوایم با استفاده از GET یا POST و ... بهش توی api درخواست بزنیم که بهش میگن endpoint یا مقصد:

![My image](https://github.com/Developers0101/notes-android-course/raw/main/images/%D8%B1%D8%AA%D8%B1%D9%88%D9%81%DB%8C%D8%AA_files/image010.jpg)

در اینجا این enpoint ما میشه بعد base url و v1/ که شامل movies/product/user میشه که میخوایم براش درخواست بزنیم.

استفاده از متد GET برای ارسال درخواست در اندروید:

<a name="_hlk129811259"></a>[https://moviesapi.ir/api/v1/movies?page={page}](https://moviesapi.ir/api/v1/movies?page=%7bpage%7d/) 

![My image](https://github.com/Developers0101/notes-android-course/raw/main/images/%D8%B1%D8%AA%D8%B1%D9%88%D9%81%DB%8C%D8%AA_files/image011.png)

![My image](https://github.com/Developers0101/notes-android-course/raw/main/images/%D8%B1%D8%AA%D8%B1%D9%88%D9%81%DB%8C%D8%AA_files/image012.png)

وقتی میخوایم از GET استفاده کنیم از ما یک string میخواد که endpoint ، مسیر یا root مون هست.

که بعد base url ما میشه movies و ما داخل string قرارش میدیم:

بعد میایم براش یه متد مینویسیم:

![My image](https://github.com/Developers0101/notes-android-course/raw/main/images/%D8%B1%D8%AA%D8%B1%D9%88%D9%81%DB%8C%D8%AA_files/image013.png)

و بعد برای متدمون مقدار برگشتی درنظر میگیرم تا ببینیم که آیا response ش اوکی هست یا نه که این کارو با Call انجام میدیم که از نوع retrofit هست و ما بوسیله ی Call میتونیم به enpoint مون (که همون movies هست) دسترسی داشته باشیم، حالا call از ما یه response میخواد که نتیجه رو به ما برگردونه که ما میایم و همون response که داخل package model ساخته بودیم رو بهش پاس میدیم.

حالا retrofit میره به root movies یه درخواست میفرسته و منتظر میمونه و نتیجه که اومد در قالب کلاس ResponseMoviesList نتیجه رو برمیگردونه.

وقتی توی fun moviesList داخل ( ) چیزی قرار ندادیم درواقع یعنی چیزی سمت سرور نفرستادیم و url ش معادل این میشه:

<https://moviesapi.ir/api/v1/movies> 

حالا اگه بخوایم در قالب query یا path چیزی بفرستیم به این صورت میشه:

<https://moviesapi.ir/api/v1/movies?page=1>

چون علامت ؟ سوال داره از نوع query هست و داخل متد moivesList به این صورت مینویسیم:

![My image](https://github.com/Developers0101/notes-android-course/raw/main/images/%D8%B1%D8%AA%D8%B1%D9%88%D9%81%DB%8C%D8%AA_files/image014.jpg)

بعد باید داخل Query کلیدش رو بفرستیم که اسم پارامترش اینجا page هست و حتماً هم باید از نوع string باشه و بعد میگیم این page نوع پارامترش از نوع int هست. 

مقداری که داخل query قرار میدیم (page) باید همون چیزی باشه که بک اند کار به ما گفته:

![My image](https://github.com/Developers0101/notes-android-course/raw/main/images/%D8%B1%D8%AA%D8%B1%D9%88%D9%81%DB%8C%D8%AA_files/image015.png)

ولی نوع پارامترمون که از نوع int هست رو میتونیم هر اسم دلخواهی که خواستیم بزاریم:

![My image](https://github.com/Developers0101/notes-android-course/raw/main/images/%D8%B1%D8%AA%D8%B1%D9%88%D9%81%DB%8C%D8%AA_files/image016.png)

قسمت 13

برای استفاده از retrofit نیاز به 2تا کلاس داریم که کلاس اولی api services و کلاس دوم کلاس api client هست که مربوط به تنظیمات خود retrofit میشه.

برای تنظیمات خود retrofit میایم و کلاس ApiClient رو در package server یا services میسازیم.

میایم از خود retrofit با یه متغییر و آبجکت میسازیم و بعد تنظیمات retrofit رو میریزیم داخلش و بعد توسط کلاس ApiClient هرجا که نیاز داشتیم به این تنظیمات دسترسی پیدا میکنیم:

![My image](https://github.com/Developers0101/notes-android-course/raw/main/images/%D8%B1%D8%AA%D8%B1%D9%88%D9%81%DB%8C%D8%AA_files/image017.png)

بعد میایم یه متد تعریف میکنیم به اسم getClient که retrofit رو برمیگردونه:

![My image](https://github.com/Developers0101/notes-android-course/raw/main/images/%D8%B1%D8%AA%D8%B1%D9%88%D9%81%DB%8C%D8%AA_files/image018.png)

درواقع یه کلاس(ApiClient) داریم که قرار تنظیمات retrofit رو داشته باشه، بعد میایم تنظیمات retrofit رو داخل متد getClient مینویسیم و بعد توسط متغییر retrofit که تعریف کرده بودیم بازگشت داده میشه به متد getClient و هرجا که این متد رو صدا بزنیم میتونیم ازش استفاده کنیم.

حالا میایم و retrofit رو مقدار دهی میکنیم:

![My image](https://github.com/Developers0101/notes-android-course/raw/main/images/%D8%B1%D8%AA%D8%B1%D9%88%D9%81%DB%8C%D8%AA_files/image019.png)

` `براش builder قرار میدیم و بعد براش یه base url قرار میدیم:

![My image](https://github.com/Developers0101/notes-android-course/raw/main/images/%D8%B1%D8%AA%D8%B1%D9%88%D9%81%DB%8C%D8%AA_files/image020.png)

چون base url ما ثابت هست میایم و داخل constants تعریفش میکنیم.

و چون ما به retrofit میایم base url رو میدیم دیگه توی api services اون مسیر root یا endpoint هامون رو مینویسیم.

![My image](https://github.com/Developers0101/notes-android-course/raw/main/images/%D8%B1%D8%AA%D8%B1%D9%88%D9%81%DB%8C%D8%AA_files/image021.png)

بعد میایم تبدیل کننده JSON به Gson رو قرار میدیم که بیاد تبدیل کنه با add convertor factory .

اگه تنظیمات خاصی برای Gson در نظر گرفته باشیم میتونیم بالا تعریف کنیم، بعد داخل create اون تنظیمات خاص رو اضافه کنیم.

بعد build رو میزنیم و بعد retrofit رو return میکنیم و برمیگردونیم:

![My image](https://github.com/Developers0101/notes-android-course/raw/main/images/%D8%B1%D8%AA%D8%B1%D9%88%D9%81%DB%8C%D8%AA_files/image022.png)

![My image](https://github.com/Developers0101/notes-android-course/raw/main/images/%D8%B1%D8%AA%D8%B1%D9%88%D9%81%DB%8C%D8%AA_files/image023.png)

یه تنظیمات اضافی دیگه هم برای retrofit در نظر میگیریم برای تایم کانکشن یا  read و write اطلاعات از سمت سرور چون retrofit خودش بصورت پیشفرض فقط 10 ثانیه در نظر میگیره برای منتظر موندن نتیجه یا ارسال اطلاعات به سمت سرور که بعد 10 ثانیه کنسل میکنه.

ما با اون کتابخونه client که به گردل اضافه کرده بودیم میتونیم تنظیمات اضافی رو روی retrofit اعمال کنیم و الان میایم زمان کانکشن retrofit رو بیشتر میکنیم.

میایم و یه متغییر به اسم client تعریف میکنیم:

![My image](https://github.com/Developers0101/notes-android-course/raw/main/images/%D8%B1%D8%AA%D8%B1%D9%88%D9%81%DB%8C%D8%AA_files/image024.png)

` `از نوع okhttpClient و از builder استفاده میکنیم و بعد میایم و زمان هارو مشخص میکنیم:

![My image](https://github.com/Developers0101/notes-android-course/raw/main/images/%D8%B1%D8%AA%D8%B1%D9%88%D9%81%DB%8C%D8%AA_files/image025.png)

مدت زمانی که طول میکشه کانکشنی که میخواد برقرار کنه time out بشه که ازما 2تا ورودی میخواد که ورودی اول مدت زمانی که طول بکشه مثلاً 60 و و ورودی دوم زمانش هست مثلاً ثانیه یا دقیقه و ... .

بعد میایم مدت زمانی که منتظر میمونه تا اطلاعات رو بخونه read time out رو مشخص میکنیم:

![My image](https://github.com/Developers0101/notes-android-course/raw/main/images/%D8%B1%D8%AA%D8%B1%D9%88%D9%81%DB%8C%D8%AA_files/image026.png)

بعد میایم مدت زمانی که میخواد اطلاعات رو write کنه یا بفرسته مشخص میکنیم:

![My image](https://github.com/Developers0101/notes-android-course/raw/main/images/%D8%B1%D8%AA%D8%B1%D9%88%D9%81%DB%8C%D8%AA_files/image027.png)

مثلاً تو body یا هرچیزی دیگه ایی رو که اطلاعات فرستادیم، سرور بگیره و نتیجه رو بگه که اوکی هست یا نه و برای زمانی که بخوایم عکس یا ویدئو آپلود کنیم میشه استفاده کرد.

و بعد میایم و build میکنیم:

![My image](https://github.com/Developers0101/notes-android-course/raw/main/images/%D8%B1%D8%AA%D8%B1%D9%88%D9%81%DB%8C%D8%AA_files/image028.png)

از اونجایی که تایم همه ی قسمت هارو روی 60 ثانیه قرار دادیم و تکراری هست میایم و بصورت constants تعریف میکنیم ولی باید کنار عدد L قرار بدیم چون از نوع long هست و باید نوعش رو مشخص کنیم:

![My image](https://github.com/Developers0101/notes-android-course/raw/main/images/%D8%B1%D8%AA%D8%B1%D9%88%D9%81%DB%8C%D8%AA_files/image029.png)

و اینطوری هر موقع خواستیم میتونیم با تغییر عدد داخل constants زمانش رو همه جا بصورت دلخواه تغییر بدیم.

حالا میایم و این client یی که تعریف کرده بودیم رو به retrofit میدیم:

![My image](https://github.com/Developers0101/notes-android-course/raw/main/images/%D8%B1%D8%AA%D8%B1%D9%88%D9%81%DB%8C%D8%AA_files/image030.png)

قسمت 14

وقتی داریم از recycler view استفاده میکنیم بعضی وقتها آیتم ها چندین با تکرار میشن و duplicate میشن برای اینکه جلوی این کار گرفته بشه میتونیم توی کلاس adapter متد get Item View Type رو override کنیم:

![My image](https://github.com/Developers0101/notes-android-course/raw/main/images/%D8%B1%D8%AA%D8%B1%D9%88%D9%81%DB%8C%D8%AA_files/image031.png)

بعد از return position استفاده میکنیم که یعنی از هر آیتم 1 دونه بیاره.

و چون اطلاعات ما داخل لیست بود ما بصورت لیست بهش پاس دادیم:

![My image](https://github.com/Developers0101/notes-android-course/raw/main/images/%D8%B1%D8%AA%D8%B1%D9%88%D9%81%DB%8C%D8%AA_files/image032.jpg)

اطلاعات ما در data بصورت لیست قرار داشت.

برای اینکه بتونیم از api مون استفاده کنیم و اونو call کنیم نیاز به یه متغییری داریم که بتونیم api services رو داخلش بنویسیم، چون همه ی root های ما داخل api services قرار دارن و توسط api services یکبار وصل میشن به تنظیمات مربوط به retrofit که در کلاس api client قرار داره و میگه با این تنظیمات root هایی که داخل api services هست رو بارگذاری کن، بخاطر همین نیاز داریم که api services رو در یک متغییر قرار بدیم:

![My image](https://github.com/Developers0101/notes-android-course/raw/main/images/%D8%B1%D8%AA%D8%B1%D9%88%D9%81%DB%8C%D8%AA_files/image033.png)

برای اینکه بتونیم از api services استفاده کنیم باید به api client وصل بشیم تا بتونیم کلیه تنظیمات رو اعمال کنیم و بتونیم api services رو مقدار دهی کنیم:

![My image](https://github.com/Developers0101/notes-android-course/raw/main/images/%D8%B1%D8%AA%D8%B1%D9%88%D9%81%DB%8C%D8%AA_files/image034.png)

برای اینکه بتونیم از api services مون استفاده کنیم باید create ش کنیم و حتی داخل خود کلاس api client و متد get client هم میتونستیم create کنیم و api service مون رو تعریف کنیم.

برای اینکه بتونیم از template هایی که برای اندروید استودیو تعریف شده استفاده کنیم و بتونیم خلاصه تر بنویسیم و خودش کد رو برای visible کردن view ها تکمیل کنه:

![My image](https://github.com/Developers0101/notes-android-course/raw/main/images/%D8%B1%D8%AA%D8%B1%D9%88%D9%81%DB%8C%D8%AA_files/image035.png)

وقتی viewVisible رو بنویسیم و enter بزنیم خودش کدرو کامل میکنه:

![My image](https://github.com/Developers0101/notes-android-course/raw/main/images/%D8%B1%D8%AA%D8%B1%D9%88%D9%81%DB%8C%D8%AA_files/image036.png)

![My image](https://github.com/Developers0101/notes-android-course/raw/main/images/%D8%B1%D8%AA%D8%B1%D9%88%D9%81%DB%8C%D8%AA_files/image037.png)

و بعد ما میایم و view مورد نظر خودمونو(movies loader) بهش اضافه میکنیم.

Call که در api services نوشته بودیم:

![My image](https://github.com/Developers0101/notes-android-course/raw/main/images/%D8%B1%D8%AA%D8%B1%D9%88%D9%81%DB%8C%D8%AA_files/image038.jpg)

Call جز متدهای retrofit و به ما این اجازه رو میده که بفهمیم که این عملیات و ارتباط با سروری که داره صورت میگیره اوکی و موفق بوده یا نه.

برای اینکه بتونیم از call استفاده کنیم و بفهمیم که همه چیز اوکی هست یا نه میایم و متد movies list و call رو در یک متغییر تعریف میکنیم که میشه این متغییرو بصورت global و سراسری هم تعریف کرد:

![My image](https://github.com/Developers0101/notes-android-course/raw/main/images/%D8%B1%D8%AA%D8%B1%D9%88%D9%81%DB%8C%D8%AA_files/image039.png)

بعد از ما ورودی میخواد که صفحه ی دلخواه رو بهش میدیم.

الان با متغییر call movies api خیلی راحت میتونیم به موارد retrofit دسترسی داشته باشیم که ببینیم همه چیز اوکی هست یا نه:

![My image](https://github.com/Developers0101/notes-android-course/raw/main/images/%D8%B1%D8%AA%D8%B1%D9%88%D9%81%DB%8C%D8%AA_files/image040.png)

enqueue اون call یا ارتباط با سرور رو توسط retrofit برای ما تامین میکنه که این api اوکی هست یا نه.

![My image](https://github.com/Developers0101/notes-android-course/raw/main/images/%D8%B1%D8%AA%D8%B1%D9%88%D9%81%DB%8C%D8%AA_files/image041.png)

enqueue بعنوان ورودی یه call back میخواد که از نوع retrofit هست چون میخوایم از listener هاش استفاده کنیم میایم از object استفاده میکنیم و بعد بهش اون مدل و response مون رو بهش پاس میدیم.

اگه object رو نمیزدیم نمیتونستیم مواردی که مورد نیاز هست و call back نیاز داره رو implement کنیم.

2تا متد داره که implement میکنیم:

![My image](https://github.com/Developers0101/notes-android-course/raw/main/images/%D8%B1%D8%AA%D8%B1%D9%88%D9%81%DB%8C%D8%AA_files/image042.png)

![My image](https://github.com/Developers0101/notes-android-course/raw/main/images/%D8%B1%D8%AA%D8%B1%D9%88%D9%81%DB%8C%D8%AA_files/image043.png)

1. on Response
1. on Failure

on Failure یعنی ارتباط با سرور برقرار نشده بنا به هر دلیلی، مثلاً 1- اینترنت نداریم 2- سرورمون down شده و در دسترس نیست 3- مثلاً توی مدل response مون اومدیم یه مورد رو int تعریف کردیم ولی سرور به ما string میده که data type هامون باهم یکی نیستن و بهم نمیخورن:

![My image](https://github.com/Developers0101/notes-android-course/raw/main/images/%D8%B1%D8%AA%D8%B1%D9%88%D9%81%DB%8C%D8%AA_files/image044.png)

یه همچین شرایطی که به کل به ما اجازه اتصال به سرور رو نمیده، این حالت ها داره توی on Failure هندل میشه.

میایم داخل on Failure یه log e میزاریم تا error هارو به ما نشون بده:

![My image](https://github.com/Developers0101/notes-android-course/raw/main/images/%D8%B1%D8%AA%D8%B1%D9%88%D9%81%DB%8C%D8%AA_files/image045.jpg)

که error هاش و کلی چیز دیگه توی t هست.

Response همون حالتی هست که response body رو برای ما برمیگردونه و شامل data, meta data, … بود:

![My image](https://github.com/Developers0101/notes-android-course/raw/main/images/%D8%B1%D8%AA%D8%B1%D9%88%D9%81%DB%8C%D8%AA_files/image046.jpg)

ممکن اینجا خود سرور به ما error بده و بک اند کار برای ما یه error یی بفرسته مثلاً ما بخوایم تو یه اپی یه کامنت بفرستیم و تا login نکرده باشیم سرور به ما اجازه نمیده و به ما پیام میده که login کنیم، که اینجور موارد error نیست بلکه response گرفتن از سمت سرور هست و چون response اوکی بوده که سرور تشخیص میده که ما ثبت نام نکردیم و اسه همین داخل on Response هست و on Failure میشه کلاً اتصالمون با سرورمون برقرار نیست و نمیتونیم وصل بشیم.

حالا میایم با if شرط میزاریم که مواردی که میخوایم دریافت کنیم اوکی هست یا نه یعنی is successful هست یا نه:

![My image](https://github.com/Developers0101/notes-android-course/raw/main/images/%D8%B1%D8%AA%D8%B1%D9%88%D9%81%DB%8C%D8%AA_files/image047.png)

اگه به این حالت بنویسیم و enter بزنیم بصورت خلاصه تر هست و خودش میاد if رو کامل میکنه:

![My image](https://github.com/Developers0101/notes-android-course/raw/main/images/%D8%B1%D8%AA%D8%B1%D9%88%D9%81%DB%8C%D8%AA_files/image048.png)

تمام چیزهایی که در قالب response body برای ما برمیگرده در قالب body هست و این body با body ارسال اطلاعات فرق داره:

![My image](https://github.com/Developers0101/notes-android-course/raw/main/images/%D8%B1%D8%AA%D8%B1%D9%88%D9%81%DB%8C%D8%AA_files/image049.jpg)

چون ما در response چیزهای مختلفی مثل headers, body, … داریم.

![My image](https://github.com/Developers0101/notes-android-course/raw/main/images/%D8%B1%D8%AA%D8%B1%D9%88%D9%81%DB%8C%D8%AA_files/image050.png)

میایم چک میکنیم که این response ما کلاً body داره یا نه یا خالی هست واسه همین از let استفاده میکنیم برای چک کردن null و چون میخوایم جاهای مختلف ازش استفاده کنیم براش اسم درنظر میگیریم(it Body).

![My image](https://github.com/Developers0101/notes-android-course/raw/main/images/%D8%B1%D8%AA%D8%B1%D9%88%D9%81%DB%8C%D8%AA_files/image051.png)

بعد اینکه درخواست ما body داشت و اوکی بود، حالا چک میکنیم که این body ما(it Body) data داره یا نه که میایم و با let چک میکنیم چون امکان داره دیتای ما هم null باشه.

![My image](https://github.com/Developers0101/notes-android-course/raw/main/images/%D8%B1%D8%AA%D8%B1%D9%88%D9%81%DB%8C%D8%AA_files/image052.png)

حالا میایم چک میکنیم که اون سایز و لیستی که داره برای ما میفرسته توش آیتمی وجود داره یا نه و بزرگتر از 0 هستن یا نه که با if چکش میکنیم.

![My image](https://github.com/Developers0101/notes-android-course/raw/main/images/%D8%B1%D8%AA%D8%B1%D9%88%D9%81%DB%8C%D8%AA_files/image053.png)

حالا میایم و adapter مون رو پر میکنیم که از ما یه دیتا میخواد که همون it Data رو میدیم بهش.

![My image](https://github.com/Developers0101/notes-android-course/raw/main/images/%D8%B1%D8%AA%D8%B1%D9%88%D9%81%DB%8C%D8%AA_files/image054.png) 

زمانی که یک اپ آنلاین مینویسیم که میخواد با اینترنت ارتباط برقرار کنه حتماً باید داخل manifest بهش permission internet یا دسترسی اینترنت رو بدیم.

![My image](https://github.com/Developers0101/notes-android-course/raw/main/images/%D8%B1%D8%AA%D8%B1%D9%88%D9%81%DB%8C%D8%AA_files/image055.jpg)

![My image](https://github.com/Developers0101/notes-android-course/raw/main/images/%D8%B1%D8%AA%D8%B1%D9%88%D9%81%DB%8C%D8%AA_files/image056.jpg)

قسمت 15

میخوایم از Path توی api service استفاده کنیم:

![My image](https://github.com/Developers0101/notes-android-course/raw/main/images/%D8%B1%D8%AA%D8%B1%D9%88%D9%81%DB%8C%D8%AA_files/image057.jpg)

[https://moviesapi.ir/api/v1/movies/{movie_id}](https://moviesapi.ir/)

برای دریافت response به این صورت مینویسیم:

[https://moviesapi.ir/api/v1/movies/1 ](https://moviesapi.ir/api/v1/movies/1%20)

توی کلاس api service به اینصورت call میکنیم:

![My image](https://github.com/Developers0101/notes-android-course/raw/main/images/%D8%B1%D8%AA%D8%B1%D9%88%D9%81%DB%8C%D8%AA_files/image058.jpg)

توی Path حتماً باید توی قسمت endpoint بیایم و از { { و هرچیزی که در اون نوشته شده رو بصورت کامل بنویسیم مثل {movie\_id} ولی در Query نیازی نیست که چیزهای بعد علامت ؟ سوال رو بنویسم مثل movies که page بعد علامت ؟ سوال بود و ننوشتیم.

نام پارامتر Path ما  movie\_id بود و نوعش از جنس عدد بود که با id و بصورت int نوشتیم.

استفاده از Path, Query بصورت ترکیبی:

![My image](https://github.com/Developers0101/notes-android-course/raw/main/images/%D8%B1%D8%AA%D8%B1%D9%88%D9%81%DB%8C%D8%AA_files/image059.jpg)

[]()

[https://moviesapi.ir/api/v1/genres/{genre_id}/movies?page={page}]()

که میایم وبه این صورت ازش response دریافت میکنیم:

<https://moviesapi.ir/api/v1/genres/1/movies?page=2>

که بجای general\_id و page عدد میزاریم و بهمون response میده.

توی api service به اینصورت استفاده میکنیم:

![My image](https://github.com/Developers0101/notes-android-course/raw/main/images/%D8%B1%D8%AA%D8%B1%D9%88%D9%81%DB%8C%D8%AA_files/image060.jpg)

همزمان از Path و Query استفاده کردیم.

استفاده از body :

![My image](https://github.com/Developers0101/notes-android-course/raw/main/images/%D8%B1%D8%AA%D8%B1%D9%88%D9%81%DB%8C%D8%AA_files/image061.jpg)

[https://moviesapi.ir/api/v1/register](https://moviesapi.ir/api/v1/genres/1/movies?page=2)

زمانی که نیاز داریم از body استفاده کنیم باید اونو در قالب json و بصورت کلاس بفرستیم همونجوری که برای response هامون کلاس درست کردیم باید برای body هم کلاس درست کنیم.

برای درست کردن کلاس body اگه بک اند کار به ما مثل response اطلاعات رو داده باشه که از پلاگین json to kotlin استفاده میکنیم اگه نه که خودمون بصورت دستی یه Data class میسازیم.

![My image](https://github.com/Developers0101/notes-android-course/raw/main/images/%D8%B1%D8%AA%D8%B1%D9%88%D9%81%DB%8C%D8%AA_files/image062.png)

@SerializedName برای اینکه اگه دیتایی که از سمت سرور میاد یه موقعه ایی ترتیبش بهم خورد براش مهم نیست و خودش میاد و بدون توجه به ترتیب قرار گیری که اول باشه یا وسط یا آخر خودش اوکی میکنه و اگه از @SerializedName استفاده نکنیم اسم فیلدهایی که از سمت سرور برای ما میاد، توی مدلمون هیچ اسمی براش در نظر نمیگیره و به ترتیب میره و اگه ترتیبی که ما در کلاسمون مدلمون درست کردیم با ترتیبی که سرور میده فرق داشته باشه برنامه کرش میکنه.

![My image](https://github.com/Developers0101/notes-android-course/raw/main/images/%D8%B1%D8%AA%D8%B1%D9%88%D9%81%DB%8C%D8%AA_files/image063.png)

![My image](https://github.com/Developers0101/notes-android-course/raw/main/images/%D8%B1%D8%AA%D8%B1%D9%88%D9%81%DB%8C%D8%AA_files/image064.png)

به این صورت واسه body مون کلاس مدل میسازیم حتی اگه خواستیم میتونیم براش کامنت هم بزاریم.

به اینصورت توی api service ازش استفاده میکنیم:

![My image](https://github.com/Developers0101/notes-android-course/raw/main/images/%D8%B1%D8%AA%D8%B1%D9%88%D9%81%DB%8C%D8%AA_files/image065.jpg)

دیگه توی body نیازی نیست که بهش کلید بدیم و فقط اسم اون کلاس body رو بهش میدیم:

![My image](https://github.com/Developers0101/notes-android-course/raw/main/images/%D8%B1%D8%AA%D8%B1%D9%88%D9%81%DB%8C%D8%AA_files/image066.jpg)

ولی توی GET بهش کلید میدیم مثل movie\_id که دادیم چون توی body یک کلید نداریم و چندین کلید داریم بخاطر همین میایم و کل body رو میفرستیم.


