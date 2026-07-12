# دریافت توکن (Token Request)

* **URL:** `POST https://sep.shaparak.ir/onlinepg/onlinepg`
* **Header:** `Content-Type: application/json`
* **اعتبار پیش‌فرض توکن:** ۲۰ دقیقه (`TokenExpiryInMin`: ۲۰–۳۶۰۰)

## Request

| پارامتر | نوع | الزامی | توضیحات |
| :--- | :--- | :---: | :--- |
| `action` | String | بله | `"token"` |
| `TerminalId` | String | بله | شماره ترمینال |
| `Amount` | Integer | بله | مبلغ ریال؛ عدد صحیح |
| `ResNum` | String | بله | شماره سفارش یکتا |
| `RedirectUrl` | String | بله | حداکثر ۲۰۸۳ کاراکتر (با GetMethod: ۱۵۳۸) |
| `CellNumber` | String | خیر | موبایل خریدار |
| `TokenExpiryInMin` | Integer | خیر | اعتبار توکن (دقیقه) |
| `Wage` | Integer | خیر | کارمزد تسهیم |
| `AffectiveAmount` | Integer | خیر | مبلغ کسر (تخفیف) |
| `HashedCardNumber` | String | خیر | MD5 کارت‌ها؛ حداکثر ۱۰؛ جداکننده `\|`;`,` |
| `ResNum1`…`ResNum4` | String | خیر | گزارش پنل؛ حداکثر ۵۰ کاراکتر |

```json
{
  "action": "token",
  "TerminalId": "0000",
  "Amount": 12000,
  "ResNum": "1qaz@WSX",
  "RedirectUrl": "http://mysite.com/receipt",
  "CellNumber": "9120000000"
}
```

## Response

```json
{ "status": 1, "token": "2c3c1fefac5a48geb9f9be7e445dd9b2" }
```

```json
{
  "status": -1,
  "errorCode": "5",
  "errorDesc": "پارامترهای ارسال شده نامعتبر است.; شماره تراکنش پذیرنده الزامی است"
}
```

| فیلد | معنی |
| :--- | :--- |
| `status` | `1` موفق / `-1` خطا |
| `token` | توکن (موفق) |
| `errorCode` / `errorDesc` | فقط در خطا |

## Neo-PG

در پاسخ موفق، هدر `X-IPG-Url` را بخوانید و کاربر را به همان آدرس هدایت کنید. بدنه JSON تغییری ندارد.
