# مستندات توسعه درگاه پرداخت SEP (بانک سامان)

مستندات هم‌راستا با فایل‌های رسمی پوشه [`new/`](./new/) — فقط موارد لازم برای پیاده‌سازی.

| منبع در `new/` | نقش |
| :--- | :--- |
| `SEP_OnlinePG_Merchant Document_Minimal_Current_Protocol_V1.pdf` | مستند فنی OnlinePG نگارش **۳.۶** (دی ۱۴۰۴) |
| `blu_pay…pdf` | اتصال Neo-PG / بلوپی (`X-IPG-Url`) |
| `_سوالات پرتکرار.pdf` | خطاهای رایج پیاده‌سازی |
| `_الزامات_پذیرندگان…pdf` | الزامات شاپرک (رگولاتوری؛ خارج از scope توسعه API) |

## نقطه شروع

**[`saman_ipg_guide.md`](./saman_ipg_guide.md)** — راهنمای یکپارچه توسعه (جریان، Token، Redirect، Callback، Verify، Reverse، کدها، Neo-PG).

## بخش‌های تفکیک‌شده

| فایل | محتوا |
| :--- | :--- |
| [`extracted_docs/01_prerequisites_and_urls.md`](./extracted_docs/01_prerequisites_and_urls.md) | پیش‌نیازها و Base URLها |
| [`extracted_docs/02_token_generation.md`](./extracted_docs/02_token_generation.md) | دریافت توکن |
| [`extracted_docs/03_redirection_and_callback.md`](./extracted_docs/03_redirection_and_callback.md) | هدایت و Callback |
| [`extracted_docs/04_verification_and_reversal.md`](./extracted_docs/04_verification_and_reversal.md) | Verify / Reverse |
| [`extracted_docs/05_errors_and_gotchas.md`](./extracted_docs/05_errors_and_gotchas.md) | کدهای خطا و نکات حیاتی |
