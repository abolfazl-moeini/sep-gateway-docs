# هدایت به درگاه و Callback

## هدایت (Redirect)

باید از دامنه ثبت‌شده پذیرنده انجام شود (`Referrer` معتبر).

### POST Form (توصیه‌شده)

```html
<form id="sepForm" action="https://sep.shaparak.ir/OnlinePG/OnlinePG" method="post">
  <input type="hidden" name="Token" value="TOKEN" />
  <input type="hidden" name="GetMethod" value="" /><!-- true = Callback با GET -->
</form>
<script>document.getElementById('sepForm').submit();</script>
```

### GET

```
https://sep.shaparak.ir/OnlinePG/SendToken?token=TOKEN
```

بدون `GetMethod`؛ Callback همیشه POST.

### Neo-PG

```html
<form action="URL_FROM_X-IPG-Url" method="post">
  <input type="hidden" name="Token" value="TOKEN" />
</form>
```

## Callback

پیش‌فرض POST به `RedirectUrl`؛ با `GetMethod=true` به‌صورت GET/QueryString.

| پارامتر | توضیح |
| :--- | :--- |
| `MID` / `TerminalId` | ترمینال |
| `State` | متنی (`OK`, `CanceledByUser`, …) |
| `Status` | عددی (`2` = موفق) |
| `ResNum` | شماره سفارش |
| `RefNum` | رسید یکتا؛ خالی = ناموفق |
| `RRN` | مرجع شتاب |
| `TraceNo` | رهگیری SEP |
| `Amount` | مبلغ ریال |
| `Wage` | کارمزد |
| `AffectiveAmount` | مبلغ واقعی کسرشده |
| `SecurePan` | کارت ماسک‌شده |
| `HashedCardNumber` | SHA256 کارت |

ورود به Verify فقط وقتی `State == "OK"` (یا `Status == 2`) و `RefNum` پر باشد.

## Status / State

| Status | State | معنی |
| :---: | :--- | :--- |
| 1 | `CanceledByUser` | انصراف |
| 2 | `OK` | موفق |
| 3 | `Failed` | ناموفق |
| 4 | `SessionIsNull` | انقضای نشست / Refresh |
| 5 | `InvalidParameters` | پارامتر نامعتبر |
| 8 | `MerchantIpAddressIsInvalid` | IP نامعتبر |
| 10 | `TokenNotFound` | توکن یافت نشد |
| 11 | `TokenRequired` | فقط توکنی |
| 12 | `TerminalNotFound` | ترمینال نامعتبر |
| 21 | `MultisettlePolicyErrors` | خطای چندحسابی |
