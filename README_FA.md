# هوش مصنوعی سیگنال پرو — سورس اپلیکیشن اندروید

این پروژه سورس اولیه Flutter برای اپلیکیشن فارسی و راست‌چین AI Crypto Signal Pro است.

## وضعیت
- رابط کاربری فارسی و راست‌چین (RTL)
- فیلتر بازار نقدی و آتی
- فیلتر بازه‌های ۵ دقیقه، ۱۵ دقیقه، ۱ ساعت و ۴ ساعت
- نمایش کارت سیگنال و دلایل تحلیل
- اتصال اختیاری به سرور از طریق `GET /signals`
- در صورت نبود آدرس سرور، داده‌های ساختگی آزمایشی نمایش داده می‌شود.
- اپلیکیشن هیچ سفارش واقعی ثبت نمی‌کند.

## ساخت APK
برای ساخت فایل نصب اندروید، روی رایانه‌ای که Flutter SDK و Android SDK نصب دارد:

```bash
flutter pub get
flutter build apk --release
```

برای اتصال به سرور:

```bash
flutter build apk --release --dart-define=API_BASE_URL=https://YOUR_API_HOST
```

خروجی معمولاً در این مسیر قرار می‌گیرد:

```text
build/app/outputs/flutter-apk/app-release.apk
```

## نکته مهم
در محیط فعلی ابزار Flutter و Android SDK نصب نیست؛ بنابراین اینجا امکان کامپایل و تحویل APK واقعی وجود ندارد. فایل تحویلی سورس اصلاح‌شده است، نه APK. برای تولید APK باید پروژه در محیط Flutter/Android SDK کامپایل شود.

## API مورد انتظار
`GET /signals`

```json
{
  "items": [
    {
      "symbol": "BTC/USDT",
      "market_type": "spot",
      "timeframe": "5m",
      "direction": "WAIT",
      "score": 52,
      "reference_price": 65000,
      "stop_loss": null,
      "target_1": null,
      "reasons": ["در انتظار تأیید"],
      "status": "PAPER_ONLY"
    }
  ]
}
```
