# پیش‌نیازها و آدرس‌ها

## پیش‌نیاز توسعه

| مورد | توضیح |
| :--- | :--- |
| IP سرور | باید در SEP ثبت شود (Token و Verify/Reverse) |
| TerminalId | فقط شماره ترمینال؛ نه MID |
| HTTPS | الزامی برای ارتباط با SEP |
| سرور ایران | IP خارج از کشور مسدود است |
| حداقل مبلغ | کمتر از ۲۰۰۰ ریال مجاز نیست (FAQ) |

## Base URLs

| سرویس | آدرس |
| :--- | :--- |
| Token | `POST https://sep.shaparak.ir/onlinepg/onlinepg` |
| Redirect POST | `https://sep.shaparak.ir/OnlinePG/OnlinePG` |
| Redirect GET | `https://sep.shaparak.ir/OnlinePG/SendToken?token=...` |
| Verify | `POST https://sep.shaparak.ir/verifyTxnRandomSessionkey/ipg/VerifyTransaction` |
| Reverse | `POST https://sep.shaparak.ir/verifyTxnRandomSessionkey/ipg/ReverseTransaction` |
| گزارش | `https://report.sep.ir` |
| دیباگ شبکه | `91.240.182.20:443` |
