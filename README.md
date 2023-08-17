<img width="32%" src="https://s6.uupload.ir/files/image_3i9b.png" align="center" alt="screenshot" />
<img width="32%" src="https://play-lh.googleusercontent.com/dOJ9g_OLnzOzqR0JaJXjgpc8Nc7NHtDkgNY5FewfpADjjsNm7ouiV9OMhhD0NOjWD2A" align="center" alt="screenshot" />

# کتابخانه تپسل پلاس برای اسکچور پرو
کتابخانه تپسل پلاس با تمامی تبلیغات ارائه شده توسط تپسل بصورت کامل و جامع برای اسکچور پرو طراحی شده.
## دانلود و اجرا پروژه سمپل
- پروژه را با فرمت اسکچور پرو از پوشه پروژه سمپل دانلود کنید.
- پروژه را داخل اسکچور ری استور کنید.
- از جاوا ۱.۸ به بالا استفاده کنید.
- پروژه را ران کنید.
## آموزش پیاده سازی قدم به قدم
### قدم اول
کانفیگ پروژه باید بصورت زیر باشد

Target sdk version -> 33

Minimal sdk version -> 19
### قدم دوم
ورژن جاوا را روی ۱.۸ یا بالاتر تنظیم کنید

D8 را فعال کنید

کتابخانه androidx یا AppCompat and Design رو فعال کنید.

کتابخانه مربوط به تپسل و تبلیغات را از پوشه کتابخانه دریافت کنید و در مسیر کتابخانه های اسکچور قرار دهید و آن ها را فعال کنید.
مسیر کتابخانه ها به صورت زیر است :

`/storage/emulated/0/.sketchware/libs/local_libs/`

### قدم سوم
تغییرات زیر را در Android Manifest اعمال کنید:

اضافه کردن درخواست های زیر

```xml
	<uses-permission android:name="android.permission.INTERNET" />
	<uses-permission android:name="android.permission.ACCESS_NETWORK_STATE" />
	<uses-permission android:name="android.permission.ACCESS_WIFI_STATE" />
	<uses-permission android:name="android.permission.CHANGE_WIFI_STATE" />
	<uses-permission android:name="com.google.android.gms.permission.AD_ID" />
	```
	
کد های زیر را در App Component قرار دهید

```xml
        <meta-data
            android:name="com.facebook.sdk.AutoLogAppEventsEnabled"
            android:value="false" />
        <meta-data
            android:name="applovin.sdk.key"
            android:value="5WfZLCGTQmDr6Mf7BBEf5blVwrf8VBMJSmwUSq9-1q5bPpCH_OGAWEP2z2lRkmonLgPzG6gbL4DlvUF9frFmt6" />
        <activity
            android:name="ir.tapsell.sdk.advertiser.TapsellAdActivity"
            android:configChanges="orientation|screenSize|keyboardHidden|smallestScreenSize|screenLayout" />
        <meta-data
            android:name="com.bumptech.glide.integration.okhttp3.OkHttpGlideModule"
            android:value="GlideModule" />
```

### قدم چهارم
کتابخانه ادموب را از قسمت کتابخانه ها فعال کنید ( نیاز نیست از کلید ادموب واقعی خود استفاده کنید)
پروژه آماده است و بقیه پیاده سازی را طبق پروژه نمونه یا مستندات تپسل جلو ببرید.

# نکته مهم
اگر پروژه شما آنلاین است و از درخواست های اینترنتی استفاده میکند نباید از کامپوننت اصلی اسکچور استفاده کنید ، میتوانید بدون هیچ کتابخانه اضافه ای مراحل زیر را دنبال کنید:

### مرحله اول
 دو فایل جاوا را که در پوشه Request Network قرار دارند را دانلود کنید و به قسمت فایل های جاوا پروژه خود اضافه کنید
 
### نحوه استفاده در اکتیویتی مورد نظر
دو شی با نام های دلخواه درست کنید به صورت زیر

```java
private RequestNetwork req;
private RequestNetwork.RequestListener _req_request_listener;
```

برای دریافت خروجی در صورت اتصال و یا ارور بصورت زیر عمل کنید ( این کد باید در بلوک initializer قرار بگیرد )

```java
req = new RequestNetwork(this);
_req_request_listener = new RequestNetwork.RequestListener() {
	@Override
	public void onResponse(String _param1, String _param2, HashMap<String, Object> _param3) {
		final String _tag = _param1;
		final String _response = _param2;
		final HashMap<String, Object> _responseHeaders = _param3;
        
        // Your code here
        
		
	}
	
	@Override
	public void onErrorResponse(String _param1, String _param2) {
		final String _tag = _param1;
		final String _message = _param2;
		// Your code here 
	}
};
```

و در نهایت برای ارسال درخواست به لینک از کد زیر استفاده کنید:

```java
req.startRequestNetwork(RequestNetworkController.GET, "YOUR_LINK", "tag", _req_request_listener);
```