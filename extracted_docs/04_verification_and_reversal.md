# Verify و Reverse

## Verify — الزامی

حداکثر **۳۰ دقیقه** پس از تراکنش؛ وگرنه Reverse خودکار.

* **URL:** `POST https://sep.shaparak.ir/verifyTxnRandomSessionkey/ipg/VerifyTransaction`
* **Header:** `Content-Type: application/json`

```json
{
  "RefNum": "jJnBmy/IojtTemplUH5ke9ULCGtDtb",
  "TerminalNumber": 2015
}
```

> فیلد ترمینال: **`TerminalNumber`** (نه `TerminalId`).

### Response

| فیلد | معنی |
| :--- | :--- |
| `Success` | موفقیت درخواست |
| `ResultCode` | `0` = موفق |
| `ResultDescription` | شرح |
| `TransactionDetail` | جزئیات |

### `TransactionDetail` (املای ثابت API)

| کلید | معنی |
| :--- | :--- |
| `RRN` | مرجع |
| `RefNum` | رسید |
| `MaskedPan` | کارت ماسک |
| `HashedPan` | هش کارت |
| `TerminalNumber` | ترمینال |
| `OrginalAmount` | مبلغ درگاه (**بدون i**) |
| `AffectiveAmount` | مبلغ کسرشده |
| `StraceDate` | تاریخ (**S اول**) |
| `StraceNo` | رهگیری (**S اول**) |

```json
{
  "TransactionDetail": {
    "RRN": "14226761817",
    "RefNum": "50",
    "MaskedPan": "621986****8080",
    "HashedPan": "b96a14400c3a59249e87c300ecc06e5920327e70220213b5bbb7d7b2410f7e0d",
    "TerminalNumber": 2001,
    "OrginalAmount": 1000,
    "AffectiveAmount": 1000,
    "StraceDate": "2019-09-16 18:11:06",
    "StraceNo": "100428"
  },
  "ResultCode": 0,
  "ResultDescription": "عملیات با موفقیت انجام شد",
  "Success": true
}
```

قبل از تحویل:
1. `RefNum` تکراری نباشد (Double Spending سمت پذیرنده).
2. `OrginalAmount` با مبلغ سفارش برابر باشد.

## Reverse — اختیاری

تا **۵۰ دقیقه** پس از تراکنش.

* **URL:** `POST https://sep.shaparak.ir/verifyTxnRandomSessionkey/ipg/ReverseTransaction`
* Body/Response مشابه Verify.

## ResultCode

| کد | API | معنی |
| :---: | :--- | :--- |
| 0 | verify \| reverse | موفق |
| 2 | verify \| reverse | تکراری |
| -2 | verify | یافت نشد |
| -6 | verify | منقضی (>۳۰ دقیقه) |
| -104 | verify \| reverse | ترمینال غیرفعال |
| -105 | verify \| reverse | ترمینال موجود نیست |
| -106 | verify \| reverse | IP غیرمجاز |
| 5 | verify | قبلاً برگشت خورده |
