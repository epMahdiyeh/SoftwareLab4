اعضای تیم: مهدیه ابراهیم پور
---------------------
شماره دانشجویی: 98170624
---------------------

--------------------------------

همانطور که در صورت سوال خواسته شده، پیاده سازی برنامه باید بصورت TDD باشد. پس ابتدا تست مربوط به برنامه را مینویسیم. (البته اسکرین شات پس از اتمام کد گرفته شده و به همین دلیل اروری مشاهده نمیشود).
تست‌ها بر اساس شرایط مختلف ورودی و خروجی تعریف میشوند تا اطمینان حاصل شود که هر تغییری در کد، همچنان سازگاری با نیازهای سیستم را حفظ میکند.

<img width="506" alt="2" src="https://github.com/epMahdiyeh/SoftwareLab4/assets/62205305/5bd5d862-c6b8-42c0-971b-1f999c3fac4c">

<img width="881" alt="1" src="https://github.com/epMahdiyeh/SoftwareLab4/assets/62205305/751f6f17-3496-4cea-805c-6c7fdca2a365">


سپس الگوی Strategy و State را پیاده سازی میکنیم:

ShippingStrategy
این اینترفیس شامل دو متد است که محاسبه قیمت ارسال را بر اساس وزن را انجام میدهد و به کمکStandardShipping و ExpressShipping، به عنوان الگوهای مختلف برای محاسبه قیمت استفاده میشود.

StandardShipping
این کلاس از ShippingStrategy ارث‌بری کرده و قیمت ارسال بر اساس وزن با ضریب 2.5 را محاسبه میکند.

ExpressShipping
این کلاس نیز از ShippingStrategy ارث‌بری میکند و قیمت ارسال را بر اساس وزن ضریب 3.5 محاسبه یکند.

ShippingContext
این کلاس وظیفه نگهداری الگوی Strategy را بر عهده دارد.

PackageState
در این اینترفیس وضعیت بسته به روز رسانی و نهایتا بعنوان خروجی چاپ میشود.

IntransitState 
این کلاس از PackageState ارث‌ بری کرده و در متد printStatus پیام مربوط به وضعیت   intransitچاپ میشود.

DeliveredState
این کلاس نیز از PackageState ارث ‌بری میکند و در متد printStatus پیام مربوط به وضعیت delivered چاپ می‌شود که یعنی بسته رسیده است.

PackageContext
این کلاس وظیفه نگهداری وضعیت بسته را دارد و متدهای آن به تغییر وضعیت بسته و چاپ آن عمل میکنند.

و در انتها ورودیهایی که نیاز داریم از کاربر بگیریم را در متد Main دریافت کرده و همچنین حلقه زمانی رسیدن محصول به مقصد را نیز تعریف میکنیم. خروجی برنامه بصورت زیر خواهد بود:

<img width="335" alt="3" src="https://github.com/epMahdiyeh/SoftwareLab4/assets/62205305/a2edcbde-1a2d-46ad-8762-41a002b07b9c">

ابتدا وزن بسته از کاربر دریافت میشود و پرسیده میشود که آیا بسته به مقصد رسیده یا خیر. سپس تعداد دفعاتی که نیاز است روش ارسال تغییر پیدا کند دریافت میشود و به همان تعداد دفعات با دو روش قیمت بسته محاسبه میشود. در اینجا تعداد دفعات برابر 3 است.


این برنامه الگوهای Strategy و State را برای مدیریت روشهای ارسال (Strategy) و وضعیت بسته (State) به خوبی پیاده‌سازی میکند. الگوی Strategy به کمک اینترفیس ShippingStrategy پیاده ‌سازی شده و این امکان را فراهم میکند که روش ارسال محاسبه شود. همچنین از این الگو برای تغییر روش ارسال در زمان اجرا به کمک  setShippingStrategy استفاده شده است.

همچنین، الگوی State برای مدیریت وضعیت بسته در طول زمان استفاده شده است. هر وضعیت IntransitState و DeliveredState به کمک اینترفیس PackageState پیاده‌سازی شدند. در این الگو تغییر وضعیت بسته در طول زمان به خوبی مدیریت شده و میتوان وضعیت‌ های مختلف بسته را به راحتی تغییر داد و رفتار مرتبط با هر وضعیت را اجرا کرد.

------------------------------------------------------------------------------

سوال 1.

1.	الگوهای ساختاری (Structural):

Adapter Pattern: این الگو دو اینترفیس متفاوت را با یکدیگر تطبیق می‌دهد تا یک کلاس وجودی را با ویژگیهای مورد نیاز یک دیگر تطبیق دهد.

Composite Pattern: این الگو به اجزای مختلف سیستم اجازه میدهد به صورت یکنواخت به کلاسهایی که با آنها ترکیب شده اند دسترسی داشته باشند.

2.	الگوهای رفتاری (Behavorial):

Observer Pattern: این الگو به یک شی این امکان را میدهد که تغییرات خود را به شی های دیگراعلان کند و برای ایجاد وابستگیهای کمتر بین کلاس‌ ها و افزایش انعطاف ‌پذیری مفید است.

Strategy Pattern : این الگو به یک شی این امکان را میدهد که یک رفتار را در زمان اجرا تعیین کند و تغییر دهد. درواقع اجازه میدهد که یک الگوریتم را از یک کلاس جدا کنیم و قابل تعویض کنیم.

3. Creational Pattern

 Singleton Pattern: این الگو تضمین میکند که یک کلاس تنها یک نمونه دارد و این نمونه به راحتی قابل دسترسی است. معمولا برای ایجاد یک نقطه دسترسی به یک سورس مشترک استفاده میشود.

 Factory Method Pattern: این الگو به یک کلاس این اجازه را میدهد که یک شی را به کلاسهای فرزند خود منتقل کند، بنابراین در این الگو می‌توان نوع خاصی از شی را ایجاد کرد.

سوال 2.

در این آزمایش از الگوی Strategy و State استفاده شده که زیرمجموعه الگوهای رفتاری (Behavorial) قرار میگیرند.

سوال 3.

برای ایجاد آبجکتی که در تمام اجراهای برنامه تنها یکبار ایجاد شود و از آن استفاده شود، الگوی طراحی Singleton مناسبترین است. با توجه به این که تنها یک بسته در هربار اجرای برنامه وجود دارد و نیاز به چند نمونه از کلاس مربوط به بسته نداریم، الگوی Singleton که یک نمونه یکتا از یک کلاس را تضمین می‌کند، بهترین الگو خواهد بود. همچنین الگوی Singleton امکان دسترسی به نمونه ایجاد شده را از هر قسمتی از برنامه را فراهم می‌ کند، بدون اینکه نیاز به ارسال این نمونه به عناصر مختلف داشته باشیم.

برای تحقق این امر، میتوانیم کلاسی بسازیم که شامل ویژگیهای زیر باشد:
- دارای یک فیلد نمونه خود (نمونه از خود کلاس) باشد.
- کانستراکتور داشته باشد تا از ایجاد نمونه ‌های جدید جلوگیری شود.
- یک متد پابلیک برای دسترسی به نمونه فراهم کند (اگر نمونه ایجاد نشده باشد، ایجاد شود و در غیر این صورت نمونه موجود را بازگرداند)

```java
public class PackageHandler {
    private static PackageHandler instance;

    private PackageHandler() {
    }

    public static PackageHandler getInstance() {
        if (instance == null) {
            instance = new PackageHandler();
        }
        return instance;
    }

}
```

با این روش هر جا که نیاز به دسترسی به نمونه PackageHandler داشته باشیم، از   PackageHandler.getInstance() استفاده میکنیم و یک نمونه یکتا خواهیم داشت.


سوال 4.

الگوی  Singleton با همه اصول SOLID  تطابق دارد. هرکدام از این اصول را جداگانه بررسی میکنیم:

Single Responsibility Principle:

الگوی Singleton بر مسئولیت واحد برای ایجاد و مدیریت یک نمونه از کلاس تاکید دارد. این کلاس تنها مسئول استفاده از یک نمونه از خود و تأمین آن به سایر بخش‌های برنامه است.

Open-Closed Principle:

الگوی Singleton معمولا قابلیت توسعه را باز میگذارد، بدون اینکه تغییرات زیادی در کد موجود صورت بگیرد. این امکان ویژگیها و رفتارهای جدیدی را به سیستم اضافه کرده و باز و بسته بودن را حفظ میکند.

Liskov Substitution Principle:

اگر یک کلاس از الگوی Singleton استفاده کند، می‌تواند جایگزین مناسبی برای آن در کد باشد. به عبارتی کلاسی که از یک نمونه از Singleton استفاده میکند، می‌تواند همان نحوه تعامل با یک شی را ادامه دهد.

Interface Segregation Principle:

الگوی Singleton ممکن است با یک اینترفیس ساده کار کند و در تطابق با تجزیه و تحلیل آن قرار گیرد. این امر معمولا در مواردی که Singleton یک سرویس یا منبع مشابه باشد، امکان‌ پذیر است.

Dependency Inversion Principle:

الگوی Singleton میتواند به عنوان یک وابستگی در کلاس‌ های دیگر ایجاد شود و از طریق این اصل، کلاس ‌های بالاتر در سلسله وابستگی بتوانند از یک نمونه از Singleton استفاده کنند. درواقع این اصل می‌تواند انعطاف ‌پذیری و تست ‌پذیری بیشتری را فراهم کند.

