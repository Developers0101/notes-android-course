---
layout: default
title: دیفیوتیل
nav_order: 4
---

قسمت 2

# Diff utils

استفاده از notify data set change در adapter recycler view اصولی نیست چون فشار زیادی به سخت افزار وارد میکنه و روش جایگزین که بهترین روش هست diff utils هست.

![My image](https://github.com/Developers0101/notes-android-course/raw/main/images/%D8%AF%DB%8C%D9%81%DB%8C%D9%88%D8%AA%DB%8C%D9%84%D8%B2/image001.png)

برای استفاده از recycler view نیاز به یه مدل داریم که میتونیم بصورت data class تعریف کنیم.

![My image](https://github.com/Developers0101/notes-android-course/raw/main/images/%D8%AF%DB%8C%D9%81%DB%8C%D9%88%D8%AA%DB%8C%D9%84%D8%B2/image002.jpg)

ونیاز به یک لایه xml داریم برای آیتم هایی recycler view .

![My image](https://github.com/Developers0101/notes-android-course/raw/main/images/%D8%AF%DB%8C%D9%81%DB%8C%D9%88%D8%AA%DB%8C%D9%84%D8%B2/image003.jpg)

و توی main activity به این صورت از مدلمون استفاده میکنیم و توی یک متد(load data) بصورت موک دیتا یا دیتای فیک پرش میکنیم و بعد به adapter recycler view پاس میدیم.

یه متد درست میکنیم که یه mutable list از کلاس user model ما رو برمیگردونه.

![My image](https://github.com/Developers0101/notes-android-course/raw/main/images/%D8%AF%DB%8C%D9%81%DB%8C%D9%88%D8%AA%DB%8C%D9%84%D8%B2/image004.jpg)

یه کلاس adapter درست میکنیم که از adapter recycler view ارث بری میکنیم و میایم view model مون رو بهش پاس میدیم و با view holder آیتم هامونو براش set میکنیم و نشون میدیم.

![My image](https://github.com/Developers0101/notes-android-course/raw/main/images/%D8%AF%DB%8C%D9%81%DB%8C%D9%88%D8%AA%DB%8C%D9%84%D8%B2/image005.png)

وقتی میخوایم از recycler view استفاده کنیم نیاز به 3 تا متد اصلی داره که میایم و هر3تا متد رو implement میکنیم و اونو override میکنه.

On create view holder میاد و view holder مارو درست میکنه که view holder همون بخش رابط کاربری ما هست که view های ما توش قرار داره مثل text view, image view, … رو شامل میشه که اطلاعات رو داخلش قرار میدیم که توسط متد on create view holder اون متد ما ساخته میشه.

متد on bind view holder میاد و به ازای هر آیتمی که توی recycler view داریم مثلاً 10 تا 100 تا آیتم، میاد آیتم هارو صدا میزنه و با توجه به position که دارن میاد set میکنه.

متد get item count که میایم داخلش تعداد آیتم هامون رو مشخص میکنیم که مثلاً 5 تا 10 تا یا کل آیتم هارو نشون بده.

![My image](https://github.com/Developers0101/notes-android-course/raw/main/images/%D8%AF%DB%8C%D9%81%DB%8C%D9%88%D8%AA%DB%8C%D9%84%D8%B2/image006.png)

برای اینکه بتونیم به view binding و view هامون دسترسی داشته باشیم داخل کلاس adapter میایم و یه inner class به اسم view holder درست میکنیم که اسم این کلاس دلخواه ولی باید با اسمی که توی adapter قرار دادیم یکی باشه.

و کلاس view holder ما باید از recycler view. view holder ارث بری کنه.

![My image](https://github.com/Developers0101/notes-android-course/raw/main/images/%D8%AF%DB%8C%D9%81%DB%8C%D9%88%D8%AA%DB%8C%D9%84%D8%B2/image007.png)

برای استفاده از binding میایم و اونو بصورت lateinit تعریف میکنیم.

![My image](https://github.com/Developers0101/notes-android-course/raw/main/images/%D8%AF%DB%8C%D9%81%DB%8C%D9%88%D8%AA%DB%8C%D9%84%D8%B2/image008.jpg)

حالا میایم و داخل متد on create view holder و binding مون رو initialize و پرش میکنیم.

![My image](https://github.com/Developers0101/notes-android-course/raw/main/images/%D8%AF%DB%8C%D9%81%DB%8C%D9%88%D8%AA%DB%8C%D9%84%D8%B2/image009.png)

که نیاز به layout inflater داره که inflater به ما اجازه میده که لایه رو درجاهایی که نیاز داریم بتونیم قرار بدیم و ازش استفاده کنیم.

Layout inflater از ما context میخواد که هم میتونیم مستقیم بهش پاس بدیم و هم از parent بگیریم ما هم میتونیم inflater رو داخل یه متغییر تعریف کنیم یا بصورت مستقیم استفاده کنیم.

بعد میایم و view holder رو return میکنیم.

![My image](https://github.com/Developers0101/notes-android-course/raw/main/images/%D8%AF%DB%8C%D9%81%DB%8C%D9%88%D8%AA%DB%8C%D9%84%D8%B2/image010.png)

حالا داخل inner class ما میتونیم از binding. root استفاده کنیم چون view های ما مشخص شد.

Diff utilis طوری هست که خودش چک میکنه که آیتمی که الان هست قبلاً توی مدل بوده یا نه و تکراری هست یا نه.

![My image](https://github.com/Developers0101/notes-android-course/raw/main/images/%D8%AF%DB%8C%D9%81%DB%8C%D9%88%D8%AA%DB%8C%D9%84%D8%B2/image011.png)

میایم و داخل کلاس view holder مون یه متد درست میکنیم(set data) و داخل این متدمون یه آیتم از اون کلاس مدلمون(user model)که قرار بصورت لیست ارسال بشه رو قرار میدیم و set میکنیم.

اگه کلاس view holder مون رو از نوع inner class تعریف نکنیم به ما اجازه دسترسی به binding هارو نمیده، بخاطر همین inner class رو مینویسم که کلاس adapter ما view holder رو یک کلاس داخلی خودش بحساب بیاره و اجازه بده از اتریبوت ها و مواردی که نیاز داریم استفاده کنیم.

![My image](https://github.com/Developers0101/notes-android-course/raw/main/images/%D8%AF%DB%8C%D9%81%DB%8C%D9%88%D8%AA%DB%8C%D9%84%D8%B2/image012.png)

وقتی میخوایم از string بصورت داینامیک استفاده کنیم میایم و از این annotation استفاده میکنیم که warning نده.

![My image](https://github.com/Developers0101/notes-android-course/raw/main/images/%D8%AF%DB%8C%D9%81%DB%8C%D9%88%D8%AA%DB%8C%D9%84%D8%B2/image013.png)

بواسطه item میایم و یه آیتم از لیست مدل هامون رو میسازیم.

![My image](https://github.com/Developers0101/notes-android-course/raw/main/images/%D8%AF%DB%8C%D9%81%DB%8C%D9%88%D8%AA%DB%8C%D9%84%D8%B2/image014.png)

داخل متد on bind view holder به وسیله holder به متد set data که داخل کلاس view holder تعریف کرده بودیم دسترسی داریم که متد set data از ما مدل میخواد همون کلاس مدلی که تعریف کرده بودیم.

![My image](https://github.com/Developers0101/notes-android-course/raw/main/images/%D8%AF%DB%8C%D9%81%DB%8C%D9%88%D8%AA%DB%8C%D9%84%D8%B2/image015.png)

برای پر کردن متد set data میایم و خارج از کلاس view holder یه متغییر به اسمdiffer call back یا هر اسم دلخواهی تعریف میکنیم.

چون میخوایم از listener های diff utilis مون استفاده کنیم از نوع object مینویسیم.

![My image](https://github.com/Developers0101/notes-android-course/raw/main/images/%D8%AF%DB%8C%D9%81%DB%8C%D9%88%D8%AA%DB%8C%D9%84%D8%B2/image016.jpg)

Diff util حالت های مختلفی داره که ما از item call back استفاده میکنیم.

![My image](https://github.com/Developers0101/notes-android-course/raw/main/images/%D8%AF%DB%8C%D9%81%DB%8C%D9%88%D8%AA%DB%8C%D9%84%D8%B2/image017.png)

Item callback از ما مدل میخواد که میایم و کلاس مدلمون رو بهش پاس میدیم و براش set میکنیم.

![My image](https://github.com/Developers0101/notes-android-course/raw/main/images/%D8%AF%DB%8C%D9%81%DB%8C%D9%88%D8%AA%DB%8C%D9%84%D8%B2/image018.jpg)

برای object مون باید 2تا متد رو impelements کنیم که این 2تا متد میاد و 2تا حالت رو چک میکنه، چون id یونیک هست ما توسط id چک میکنیم که آیا item که داخل لیست ما هست قبلاً وجود داشته یا جدید هست که الکی به سیستم فشار نیاریم و هر دوتا متدمون از نوع Boolean هست و نیاز به return داره.

متد اول are items the same میاد آیتم هارو چک میکنه.

و متد دوم are content the same میاد کل دیتا رو چک میکنه که آیا کل دیتا در حالت قبلی وجود داشت و تکراری هست یا نه که اگه بود دوباره اونو اضافه نکنه.

![My image](https://github.com/Developers0101/notes-android-course/raw/main/images/%D8%AF%DB%8C%D9%81%DB%8C%D9%88%D8%AA%DB%8C%D9%84%D8%B2/image019.jpg)

توی متد اول میایم id آیتم هارو چک میکنیم که آیا item جدید هست یا قدیمی، که آیتم های قدیمی رو نگه میداره و آیتم های جدید رو چک میکنه که با آیتم ها قبلی برابر یا نه که اگه برابر بود در نظر نمیگیره و اگه جدید بود به مدلمون اضافه میکنه و بصورت تک آیتمی چک میکنه.

![My image](https://github.com/Developers0101/notes-android-course/raw/main/images/%D8%AF%DB%8C%D9%81%DB%8C%D9%88%D8%AA%DB%8C%D9%84%D8%B2/image020.jpg)

داخل متد دوممون میاد و کل مدل رو چک میکنه.

![My image](https://github.com/Developers0101/notes-android-course/raw/main/images/%D8%AF%DB%8C%D9%81%DB%8C%D9%88%D8%AA%DB%8C%D9%84%D8%B2/image021.png)

نیاز به یه چیزی داریم که مدلمون رو داخلش قرار بدیم تا بتونیم ازش استفاده کنیم چون داخل constructor adapter مون قرار ندادیم و هیچ متدی هم برای add item ننوشتیم، بخاطر همین نیاز به یک Async list differ داریم که جز موارد diff utilis بحساب میاد و item رو بصورت async model رو از ما میگیره و به متغییر differ callback ما میده و differ callback میاد و item هارو میگیره و با 2تا متدش چک میکنه و اگه اجازه add شدن داشته باشه اتوماتیک اضافه میکنه.

بخاطر همین یه متغییر به اسم differ یا هر اسم دلخواهی تعریف میکنیم و از نوع Async تعریف میکنیم که تداخلی توی کارهای ما نداشته باشه و بتونه بصورت همزمانی کارهارو انجام بده.

که Async list differ از ما 2 تا ورودی میخواد که ورودی اول adapter میخواد و ورودی دوم از ما call back میخواد که میایم و متغییر differ call back که تعریف کرده بودیم رو پاس میدیم.

![My image](https://github.com/Developers0101/notes-android-course/raw/main/images/%D8%AF%DB%8C%D9%81%DB%8C%D9%88%D8%AA%DB%8C%D9%84%D8%B2/image022.jpg)

![My image](https://github.com/Developers0101/notes-android-course/raw/main/images/%D8%AF%DB%8C%D9%81%DB%8C%D9%88%D8%AA%DB%8C%D9%84%D8%B2/image023.jpg)

حالا داخل متد on bind view holder با استفاده از متغییر differ میتونیم item هامونو set کنیم که differ از یه متد به اسم current list یا لیست جاری استفاده میکنه، و لیست جاری رو برمیگردونه و بعد بهش position رو میدیم.

![My image](https://github.com/Developers0101/notes-android-course/raw/main/images/%D8%AF%DB%8C%D9%81%DB%8C%D9%88%D8%AA%DB%8C%D9%84%D8%B2/image024.png)

داخل متد get item count هم میایم و size اون لیست مون رو بهش میدیم.

![My image](https://github.com/Developers0101/notes-android-course/raw/main/images/%D8%AF%DB%8C%D9%81%DB%8C%D9%88%D8%AA%DB%8C%D9%84%D8%B2/image025.png)

میتونیم به این حالت هم get item count رو بنویسیم و فرقی نداره.

![My image](https://github.com/Developers0101/notes-android-course/raw/main/images/%D8%AF%DB%8C%D9%81%DB%8C%D9%88%D8%AA%DB%8C%D9%84%D8%B2/image026.png)

وقتی چیزی رو در قالب متغییر و بصورت lazy تعریف کنیم اونو یکبار تعریف میکنه و تا زمانی که اون activity زنده است، همون یکبار که تعریف کرده در اختیارمون قرار میده و مدام تعریف نمیشه که بار اضافه رو سخت افزار بیاره و هرموقع نیاز بود میاره و نبود از دسترس خارج میکنه.

![My image](https://github.com/Developers0101/notes-android-course/raw/main/images/%D8%AF%DB%8C%D9%81%DB%8C%D9%88%D8%AA%DB%8C%D9%84%D8%B2/image027.png)

بوسیله ی differ میایم و item های adapter رو پر میکنیم و differ یه متد submit list داره که از ما لیست میخواد و ما داخل متد load data اومده بودیم یه لیست از مدل هامون تعریف کرده بودیم و اونو بهش پاس میدیم.

![My image](https://github.com/Developers0101/notes-android-course/raw/main/images/%D8%AF%DB%8C%D9%81%DB%8C%D9%88%D8%AA%DB%8C%D9%84%D8%B2/image028.png)

وقتی از apply استفاده کنیم دیگه نیازی نیست که بیایم و اون view رو هی بنویسیم و تعریف کنیم و مستقیم به اتریبیوت هاش دسترسی داریم. 

که recycler view 2تا اتریبیوت داره که یکی layout manager و دومی هم adapter هست.

