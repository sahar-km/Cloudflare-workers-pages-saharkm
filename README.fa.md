# 优选订阅生成器 WorkerVless2sub

### این یک تولید کننده محتوای اشتراک گره VLESS است که از طریق Cloudflare Workers ساخته شده است که به طور خودکار مسیرهای ترجیحی را ایجاد می کند.[\[اصل اجرا\]](https://www.youtube.com/watch?v=p-KhFJAC4WQ&t=70s)

گروه ارتباطی تلگرام:[@CMLiussss](https://t.me/CMLiussss)

# روش استقرار صفحات[آموزش تصویری](https://www.youtube.com/watch?v=p-KhFJAC4WQ&t=509s)

### 1. صفحات Cloudflare را مستقر کنید:

-   این پروژه را در Github فورک کنید و ستاره را کلیک کنید!!!
-   در کنسول Cloudflare Pages انتخاب کنید`连接到 Git`پس از آن، را انتخاب کنید`WorkerVless2sub`بعد از مورد کلیک کنید`开始设置`。

### 2. یک دامنه سفارشی را به صفحات متصل کنید:

-   در کنسول Pages`自定义域`برگه، در زیر کلیک کنید`设置自定义域`。
-   نام دامنه ثانویه سفارشی خود را وارد کنید، مراقب باشید از نام دامنه ریشه خود استفاده نکنید، به عنوان مثال:
    نام دامنه ای که به شما اختصاص داده شده است`fuck.cloudns.biz`، سپس یک فیلد سفارشی برای پر کردن اضافه کنید`sub.fuck.cloudns.biz`خودشه؛
-   با توجه به الزامات Cloudflare، نام دامنه شما ارائه دهنده خدمات DNS بازگردانده خواهد شد و دامنه سفارشی اضافه خواهد شد.`sub`رکورد CNAME از`WorkerVless2sub.pages.dev`پس از آن، کلیک کنید`激活域`خودشه.

### 3. ورودی اشتراک سریع را تغییر دهید و اطلاعات گره Vless داخلی را اضافه کنید:

به عنوان مثال، نام دامنه پروژه صفحات شما:`sub.fuck.cloudns.biz`；

-   اضافه کردن به`TOKEN`متغیر، ورودی دسترسی سریع اشتراک، مقدار پیش فرض:`auto`، آدرس اشتراک گره پیش فرض مشترک را دریافت کنید، یعنی،`/auto`،مثلا`https://sub.fuck.cloudns.biz/auto`
-   اضافه کردن به`HOST`متغیرهایی مانند`edgetunnel-2z2.pages.dev`；
-   اضافه کردن به`UUID`متغیرهایی مانند`30e9c5c8-ed28-4cd9-b008-dc67277f8b02`；
-   اضافه کردن به`PATH`متغیرهایی مانند`/?ed=2048`；

### 4. مسیر دلخواه خود را اضافه کنید:

-   متغیرها را اضافه کنید`ADD`/`ADDNOTLS`خط ترجیحی استاتیک محلی، اگر شماره پورت وجود نداشته باشد، درگاه پیش‌فرض برای TLS 443 است / پورت پیش‌فرض برای noTLS 80 است و عدد # با نام مستعار یادآور دنبال می‌شود، برای مثال:
        icook.tw:2053#优选域名
        cloudflare.cfgo.cc#优选官方线路

-   متغیرها را اضافه کنید`ADDAPI`/`ADDNOTLSAPI`برای**فایل txt آدرس IP ترجیحی**URL. مثلا:
    ```url
    https://raw.githubusercontent.com/cmliu/WorkerVless2sub/main/addressesapi.txt
    https://raw.githubusercontent.com/cmliu/WorkerVless2sub/main/addressesipv6api.txt
    ```

<details>
<summary><code><strong>「 我不是小白！我有IP库！我知道IPtest是什么！我也有csv测速文件！ 」</strong></code></summary>

-   متغیرها را اضافه کنید`ADDCSV`برای**آدرس فایل csv نتیجه تست سرعت iptest**URL. مثلا:
    ```js
    https://raw.githubusercontent.com/cmliu/WorkerVless2sub/main/addressescsv.csv
    ```
-   متغیرها را اضافه کنید`DLS`،به معنای`ADDCSV`IP هایی که حداقل سرعت مورد نیاز را برآورده می کنند و مقدار اصلاح شده را برآورده نمی کنند به محتوای اشتراک ترجیحی اضافه نمی شوند. توجه: واحد در نظر گرفته نمی شود، فقط مقدار عددی در نظر گرفته می شود لطفاً به نتایج تست سرعت خود مراجعه کنید. مثلا:

    ```js
    8
    ```

    </details>

# روش استقرار کارگران[آموزش تصویری](https://youtu.be/AtCF7eq0hcE)

### 1. استقرار Cloudflare Worker:

-   یک Worker جدید در کنسول Cloudflare Worker ایجاد کنید.
-   اراده[worker.js](https://github.com/cmliu/WorkerVless2sub/blob/main/_worker.js)مطالب را در ویرایشگر Worker قرار دهید.

### 2. ورودی اشتراک سریع را تغییر دهید و اطلاعات گره Vless داخلی را اضافه کنید:

به عنوان مثال، نام دامنه پروژه کارگران شما این است:`sub.cmliussss.workers.dev`；

-   اضافه کردن به`TOKEN`متغیر، ورودی دسترسی سریع اشتراک، مقدار پیش فرض:`auto`، آدرس اشتراک گره پیش فرض مشترک را دریافت کنید، یعنی،`/auto`،مثلا`https://sub.cmliussss.workers.dev/auto`
-   اضافه کردن به`HOST`متغیرهایی مانند`edgetunnel-2z2.pages.dev`；
-   اضافه کردن به`UUID`متغیرهایی مانند`30e9c5c8-ed28-4cd9-b008-dc67277f8b02`；
-   اضافه کردن به`PATH`متغیرهایی مانند`/?ed=2048`；

### 3. مسیر دلخواه خود را اضافه کنید:

**3.1 نمونه ای از تغییر پارامتر آدرس ها**

-   تجدید نظر کنید`addresses`پارامترها یک خط ترجیحی ثابت محلی اضافه می کنند، اگر شماره پورت وجود نداشته باشد، پیش فرض 443 است.
    ```js
    let addresses = [
    	'icook.tw:2053#优选域名',
    	'cloudflare.cfgo.cc#优选官方线路',
    	'185.221.160.203:443#电信优选IP',
    ];
    ```
    این روش فقط اضافه کردن نام های دامنه ترجیحی را توصیه می کند که به طور مکرر تغییر می کنند`addressesapi`برای تحقق.

**3.2 مثالی از اصلاح پارامترهای آدرس‌اسپی**

-   تجدید نظر کنید`addressesapi`پارامترها، در اسکریپت تنظیم شده است`addressesapi`متغیر است**فایل txt آدرس IP ترجیحی**URL. مثلا:
    ```js
    let addressesapi = [
    	'https://raw.githubusercontent.com/cmliu/WorkerVless2sub/main/addressesapi.txt',
    	'https://addressesapi.090227.xyz/CloudFlareYes',
    ];
    ```
    قابل ارجاع است[addressesapi.txt](https://raw.githubusercontent.com/cmliu/WorkerVless2sub/main/addressesapi.txt)قالب محتوا توسط خودتان ساخته شده است.

<details>
<summary><code><strong>「 我不是小白！我有IP库！我知道IPtest是什么！我也有csv测速文件！ 」</strong></code></summary>

**3.3 مثالی از تغییر پارامترهای addressescsv**

-   تجدید نظر کنید`addressescsv`پارامترها، در اسکریپت تنظیم شده است`addressescsv`متغیر است**آدرس فایل csv نتیجه تست سرعت iptest**URL. مثلا:

    ```js
    let DLS = 4;//速度下限
    let addressescsv = [
    	'https://raw.githubusercontent.com/cmliu/WorkerVless2sub/main/addressescsv.csv',
    		'https://raw.githubusercontent.com/cmliu/WorkerVless2sub/main/addressescsv.csv',
    ];
    ```

    `DLS`IP هایی که حداقل سرعت مورد نیاز را ندارند به محتوای اشتراک ترجیحی اضافه نمی شوند. توجه: واحد در نظر گرفته نمی شود، فقط مقدار عددی در نظر گرفته می شود لطفاً به نتایج تست سرعت خود مراجعه کنید.

    </details>

# استفاده از مولد اشتراک[آموزش تصویری](https://youtu.be/OjqCKeEY7DQ)

به عنوان مثال، نام دامنه پروژه کارگران شما این است:`sub.cmliussss.workers.dev`；

### 1. اشتراک سریع

-   اضافه کردن به`TOKEN`متغیر، ورودی دسترسی سریع اشتراک، مقدار پیش فرض:`auto`، آدرس اشتراک گره پیش فرض مشترک را دریافت کنید، یعنی،`/auto`،مثلا:
    ```url
    https://sub.cmliussss.workers.dev/auto
    ```

### 2. اشتراک سفارشی

-   **فرمت اشتراک سفارشی**`https://[你的Workers域名]/sub?host=[你的Vless域名]&uuid=[你的UUID]&path=[你的ws路径]`
-   **میزبان**: نام دامنه مبدل VLESS شما، به عنوان مثال.`edgetunnel-2z2.pages.dev`；
-   **uuid**: UUID کلاینت VLESS شما، به عنوان مثال.`30e9c5c8-ed28-4cd9-b008-dc67277f8b02`；
-   **مسیر**(اختیاری): مسیر WS VLESS شما (اگر هیچ کدام را خالی بگذارید)، به عنوان مثال.`/?ed=2048`。
-   آدرس اشتراک سفارشی به شرح زیر است:
    ```url
    https://sub.cmliussss.workers.dev/sub?host=edgetunnel-2z2.pages.dev&uuid=30e9c5c8-ed28-4cd9-b008-dc67277f8b02&path=/?ed=2048
    ```
-   توجه داشته باشید که مسیر باید حاوی "/sub" باشد.

### 3. فایل های پیکربندی clash و singbox را مشخص کنید

-   اضافه کردن به`format=clash`مقدار کلید، پیکربندی اشتراک clash را دریافت کنید، به عنوان مثال:
    ```url
    https://sub.cmliussss.workers.dev/auto?format=clash
    https://sub.cmliussss.workers.dev/sub?format=clash&host=edgetunnel-2z2.pages.dev&uuid=30e9c5c8-ed28-4cd9-b008-dc67277f8b02&path=/?ed=2048
    ```
-   اضافه کردن به`format=singbox`مقدار کلید، پیکربندی اشتراک singbox را دریافت کنید، برای مثال:
    ```url
    https://sub.cmliussss.workers.dev/auto?format=singbox
    https://sub.cmliussss.workers.dev/sub?format=singbox&host=edgetunnel-2z2.pages.dev&uuid=30e9c5c8-ed28-4cd9-b008-dc67277f8b02&path=/?ed=2048
    ```

### توضیحات متغیر

| نام متغیر         | مثال                                                                                                                                                           | تذکر دهید                                                                                                                   |
| ----------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------- |
| رمز               | خودکار                                                                                                                                                         | به سرعت در آدرس مسیر اشتراک گره داخلی / auto مشترک شوید (از چندین عنصر پشتیبانی می کند که بین عناصر استفاده می شود`,`فاصله) |
| میزبان            | edgetunnel-2z2.pages.dev                                                                                                                                       | به سرعت در نام دامنه جعلی گره داخلی مشترک شوید                                                                              |
| UUID              | Bahaasaa-4f0-4496-90bas-1saaaaaa4904                                                                                                                           | به سرعت در UUID یک گره داخلی مشترک شوید                                                                                     |
| مسیر              | /?ed=2560                                                                                                                                                      | به سرعت در اطلاعات مسیر گره های داخلی مشترک شوید                                                                            |
| اضافه کردن        | icook.tw:2053#نام دامنه ترجیحی رسمی                                                                                                                            | مطابقت`addresses`فیلد (از چندین عنصر پشتیبانی می کند که بین عناصر استفاده می شود`,`فاصله)                                   |
| ADDAPI            | [https://raw.github.../addressesapi.txt](https://raw.githubusercontent.com/cmliu/WorkerVless2sub/main/addressesapi.txt)                                        | مطابقت`addressesapi`فیلد (از چندین عنصر پشتیبانی می کند که بین عناصر استفاده می شود`,`فاصله)                                |
| اضافه کردن        | icook.hk:8080# نام دامنه ترجیحی رسمی                                                                                                                           | مطابقت`addressesnotls`فیلد (از چندین عنصر پشتیبانی می کند که بین عناصر استفاده می شود`,`فاصله)                              |
| ADDNOTLSAPI       | [https://raw.github.../addressesapi.txt](https://raw.githubusercontent.com/cmliu/CFcdnVmess2sub/main/addressesapi.txt)                                         | مطابقت`addressesnotlsapi`فیلد (از چندین عنصر پشتیبانی می کند که بین عناصر استفاده می شود`,`فاصله)                           |
| ADDCSV            | [https://raw.github.../addressescsv.csv](https://raw.githubusercontent.com/cmliu/WorkerVless2sub/main/addressescsv.csv)                                        | مطابقت`addressescsv`فیلد (از چندین عنصر پشتیبانی می کند که بین عناصر استفاده می شود`,`فاصله)                                |
| DLS               | 8                                                                                                                                                              | `addressescsv`نتایج اندازه گیری سرعت با محدودیت سرعت پایین تر مطابقت دارد                                                   |
| NOTLS             | نادرست                                                                                                                                                         | تغییر به`true`، هیچ قضاوتی برای نام دامنه انجام نخواهد شد و noTLS همیشه برگردانده خواهد شد.                                 |
| TGTOKEN           | 6894123456:XXXXXXXXX0qExVsBPUhHDAbXXXXXXqWXgBA                                                                                                                 | توکن ربات برای ارسال اعلان های TG                                                                                           |
| شما انجام می دهید | 6946912345                                                                                                                                                     | شناسه دیجیتالی حساب برای دریافت اعلان های TG                                                                                |
| SUBAPI            | api.v1.mk                                                                                                                                                      | clash، singbox، و غیره باطن تبدیل اشتراک                                                                                    |
| SUBCONFIG         | [https://raw.github.../ACL4SSR_Online_Full_MultiMode.ini](https://raw.githubusercontent.com/cmliu/ACL4SSR/main/Clash/config/ACL4SSR_Online_Full_MultiMode.ini) | clash، singbox، و غیره. پروفایل های تبدیل اشتراک                                                                            |
| زیر نام           | WorkerVless2sub                                                                                                                                                | نام مولد اشتراک                                                                                                             |
| PS                | 【لطفا سرعت را اندازه نگیرید】                                                                                                                                   | پیام یادداشت نام گره                                                                                                        |

## ستاره ها طلوع می کنند

[![Stargazers over time](https://starchart.cc/cmliu/WorkerVless2sub.svg?variant=adaptive)](https://starchart.cc/cmliu/WorkerVless2sub)

# سپاسگزار

تخیل خودم،[ساکورا-کمان](https://github.com/SAKURA-YUMI)，[EzSync](https://github.com/EzSync)、[ACL4SSR](https://github.com/ACL4SSR/ACL4SSR/tree/master/Clash/config)、[گوسفند چاق](https://github.com/youshandefeiyang/sub-web-modify)
