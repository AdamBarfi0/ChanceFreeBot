<div align="center">

# 🎰 Jayzeh — Provably-Fair Lottery & TON Donations

### A self-contained Telegram Mini App for transparent, verifiable raffles with built-in TON wallet support

[![HTML5](https://img.shields.io/badge/HTML5-E34F26?logo=html5&logoColor=white)](#)
[![JavaScript](https://img.shields.io/badge/Vanilla%20JS-F7DF1E?logo=javascript&logoColor=black)](#)
[![TON](https://img.shields.io/badge/TON-0098EA?logo=ton&logoColor=white)](#)
[![Telegram Mini App](https://img.shields.io/badge/Telegram-Mini%20App-26A5E4?logo=telegram&logoColor=white)](#)
[![i18n](https://img.shields.io/badge/i18n-FA%20%7C%20EN-success)](#)
[![License](https://img.shields.io/badge/License-MIT-blue.svg)](#-license)

**🌐 Languages:** [English](#-english) · [فارسی](#-persian)

</div>

---

<a name="-english"></a>

## 🇬🇧 English

> A single-file (`index.html`), zero-dependency Telegram Mini App that runs a **provably-fair** lottery and accepts **TON** donations. No backend, no build step — just open it. Fully bilingual (Persian / English) with a one-tap language switch.

### ✨ Features

- 🎲 **Provably-Fair Draws** — Every winner is selected by a 4-layer cryptographic algorithm that anyone can independently verify.
- 🔐 **Commit–Reveal Scheme** — A Server Seed hash is committed *before* each draw and revealed after rotation, so results can never be manipulated.
- 💎 **TON Donations** — Shows live wallet balance and the latest incoming transactions, pulled directly from the TON blockchain.
- 🔗 **On-chain Transparency** — Every donation links to TONScan for public verification.
- 🌍 **Bilingual (FA / EN)** — Complete UI translation with a one-tap toggle; RTL/LTR switches automatically and numerals localize (۱۲۳ ↔ 123).
- 📱 **Telegram-Native** — Integrates the Telegram WebApp SDK: theme, main button, and haptic feedback.
- 🎨 **Modern Dark UI** — Animated startup loader, responsive layout, reduced-motion support, neon accents.
- 👥 **Up to 500 Participants** — Bulk add by pasting comma / newline-separated names.
- 📊 **Live Fairness Stats** — Real-time bias auditing and a full verification report per draw.
- 🧩 **Zero Dependencies** — Pure vanilla HTML/CSS/JS in one portable file.

### 🔐 How the Provably-Fair Algorithm Works

The winner is chosen through a transparent, reproducible pipeline:

| Layer | Purpose |
|-------|---------|
| 🌱 **Entropy Pool** | Mixes 5 independent sources: Server Seed · Client Seed · Nonce · Round · Timestamp |
| 🔑 **HMAC-DRBG** | Deterministic random-bit generator seeded from the entropy pool |
| 🔁 **8-Round Chained SHA-256** | Full avalanche effect — a 1-bit input change flips all 256 output bits |
| 🎯 **Rejection Sampling** | Guarantees **zero modulo bias** even when 2⁶⁴ isn't divisible by the participant count |

**Commit → Use → Reveal lifecycle:**

1. **Commit** — The hash of the Server Seed (`ServerSeedCommit`) is published *before* any draw. The server cannot change the seed afterwards without breaking the hash.
2. **Use** — While active (up to 64 draws), the raw seed stays hidden so future results are unpredictable.
3. **Reveal** — After 64 draws the old Server Seed is revealed, letting you **re-verify every draw of that period**. A fresh seed is then committed.

> This is the same commit–reveal model used by Provably-Fair casinos and Bitcoin Lightning.

### 💎 TON Donations

- Displays the project wallet's **live balance** and **last 10 incoming transactions**.
- Each transaction shows the sender, amount, and a relative timestamp, with a **"View on TONScan"** link.
- One-tap **copy address** with haptic + toast feedback.
- Data is fetched from the public **TonAPI** and cached briefly to stay responsive.

**Project wallet:**

```
UQCXZBew1zugws0K3smV4VJNyJyO16ECSlqEnUAHIUWJrAbW
```

### 🚀 Deployment (as a Telegram Mini App)

Because it's a single static file, hosting is trivial:

1. **Host the file** on any static host — GitHub Pages, Cloudflare Pages, Vercel, Netlify, or your own server.
   ```bash
   # Example: GitHub Pages
   git add index.html
   git commit -m "Deploy lottery mini app"
   git push
   # Then enable Pages in repo Settings → Pages
   ```
2. **Create a bot** with [@BotFather](https://t.me/BotFather) → `/newbot`.
3. **Register the Mini App** → `/newapp` (or set a Menu Button) and point its URL to your hosted file.
4. Open the bot, tap the button — done. 🎉

> 💡 Tip: HTTPS is required by Telegram. GitHub Pages / Cloudflare Pages provide it for free.

### 🧩 Tech Stack

- **HTML5 + CSS3** (custom properties, grid, animations)
- **Vanilla JavaScript** (modular `State`, `UI`, `Lottery`, `Donate`, `Fairness`, `I18N` controllers)
- **Web Crypto API** (SHA-256 / HMAC)
- **Telegram WebApp SDK**
- **TonAPI** (balance & transactions) · **TONScan** (explorer links)

### 🔧 Configuration

All settings live in a single `CONFIG` block near the top of the script:

| Key | Description |
|-----|-------------|
| `ADDRESS` | Your TON wallet address (friendly format) |
| `TONAPI_BASE` | TonAPI base endpoint |
| `EXPLORER_URL` | Explorer base URL for address/tx links (TONScan) |
| `CACHE_TTL` | How long blockchain data is cached (ms) |

To use your own wallet, just replace `ADDRESS` — the raw address is derived automatically at runtime.

### 🛡️ Security Notes

- The raw Server Seed is **never** exposed while active — only its hash (commitment).
- All randomness is generated client-side with the Web Crypto API.
- No private keys or secrets are stored in the app; it only **reads** public on-chain data.

### 💸 Support

If this project helps you, consider a TON donation to the wallet above, or ⭐ the repo!

### 📄 License

Released under the **MIT License** — see [`LICENSE`](LICENSE).

---

<div dir="rtl" align="right">

<a name="-persian"></a>

## 🇮🇷 فارسی

> یک مینی‌اپ تلگرام **تک‌فایلی** (`index.html`) و **بدون هیچ وابستگی** که یک قرعه‌کشی **قابل‌اثبات و عادلانه (Provably-Fair)** اجرا می‌کند و از **دونیت با TON** پشتیبانی می‌کند. بدون بک‌اند و بدون مرحله‌ی Build — کافی است بازش کنید. کاملاً دوزبانه (فارسی/انگلیسی) با دکمه‌ی تعویض زبان با یک لمس.

### ✨ امکانات

- 🎲 **قرعه‌کشی قابل‌اثبات** — برنده با یک الگوریتم رمزنگاری ۴ لایه انتخاب می‌شود که هرکسی می‌تواند مستقلاً صحت آن را تأیید کند.
- 🔐 **طرح تعهد و افشا (Commit–Reveal)** — هش Server Seed *پیش از* هر قرعه‌کشی ثبت و پس از چرخش افشا می‌شود؛ پس نتایج هرگز قابل دستکاری نیستند.
- 💎 **دونیت با TON** — موجودی لحظه‌ای کیف‌پول و آخرین تراکنش‌های دریافتی را مستقیماً از بلاکچین TON نمایش می‌دهد.
- 🔗 **شفافیت روی زنجیره** — هر حمایت به TONScan لینک می‌شود تا به‌صورت عمومی قابل بررسی باشد.
- 🌍 **دوزبانه (فارسی/انگلیسی)** — ترجمه‌ی کامل رابط کاربری با دکمه‌ی تعویض؛ جهت صفحه (RTL/LTR) و ارقام (۱۲۳ ↔ 123) به‌صورت خودکار محلی‌سازی می‌شوند.
- 📱 **بومیِ تلگرام** — یکپارچه با Telegram WebApp SDK: تم، دکمه‌ی اصلی و بازخورد لمسی (Haptic).
- 🎨 **رابط مدرن تیره** — صفحه‌ی بارگذاری متحرک، چیدمان واکنش‌گرا، پشتیبانی از کاهش حرکت و رنگ‌های نئونی.
- 👥 **تا ۵۰۰ شرکت‌کننده** — افزودن گروهی با چسباندن نام‌های جداشده با کاما یا خط جدید.
- 📊 **آمار زنده‌ی عدالت** — بررسی بایاس در لحظه و گزارش کامل تأیید برای هر قرعه‌کشی.
- 🧩 **بدون وابستگی** — کاملاً HTML/CSS/JS خالص در یک فایل قابل‌حمل.

### 🔐 الگوریتم عادلانه چگونه کار می‌کند؟

برنده از طریق یک خط‌لوله‌ی شفاف و قابل‌بازتولید انتخاب می‌شود:

| لایه | کاربرد |
|------|--------|
| 🌱 **استخر آنتروپی** | ترکیب ۵ منبع مستقل: Server Seed · Client Seed · Nonce · Round · Timestamp |
| 🔑 **HMAC-DRBG** | مولد بیت‌های تصادفیِ قطعی که از استخر آنتروپی تغذیه می‌شود |
| 🔁 **SHA-256 زنجیره‌ای ۸ دور** | اثر بهمنی کامل — تغییر ۱ بیت ورودی، تمام ۲۵۶ بیت خروجی را تغییر می‌دهد |
| 🎯 **Rejection Sampling** | تضمین **بایاس صفر** حتی وقتی ۲⁶⁴ بر تعداد شرکت‌کنندگان بخش‌پذیر نباشد |

**چرخه‌ی تعهد ← استفاده ← افشا:**

1. **تعهد (Commit)** — هش Server Seed (به نام `ServerSeedCommit`) *پیش از* هر قرعه‌کشی منتشر می‌شود. سرور بعداً نمی‌تواند Seed را بدون شکستن هش تغییر دهد.
2. **استفاده (Use)** — تا زمانی که فعال است (حداکثر ۶۴ قرعه‌کشی)، Seed خام مخفی می‌ماند تا نتایج آینده غیرقابل‌پیش‌بینی باشند.
3. **افشا (Reveal)** — پس از ۶۴ قرعه‌کشی، Server Seed قدیمی افشا می‌شود تا بتوانید **تمام قرعه‌کشی‌های آن دوره را دوباره تأیید کنید**. سپس یک Seed جدید تعهد می‌شود.

> این همان مدل تعهد–افشایی است که کازینوهای Provably-Fair و Bitcoin Lightning استفاده می‌کنند.

### 💎 دونیت با TON

- **موجودی لحظه‌ای** کیف‌پول پروژه و **۱۰ تراکنش دریافتی آخر** را نمایش می‌دهد.
- هر تراکنش، فرستنده، مبلغ و زمان نسبی را به‌همراه لینک **«مشاهده در TONScan»** نشان می‌دهد.
- **کپی آدرس** با یک لمس همراه با بازخورد لمسی و پیام (Toast).
- داده‌ها از **TonAPI** عمومی دریافت و برای پاسخ‌دهی سریع، کوتاه‌مدت کش می‌شوند.

**کیف‌پول پروژه:**

```
UQCXZBew1zugws0K3smV4VJNyJyO16ECSlqEnUAHIUWJrAbW
```

### 🚀 استقرار (به‌عنوان مینی‌اپ تلگرام)

چون فقط یک فایل ثابت است، میزبانی آن بسیار ساده است:

1. **فایل را میزبانی کنید** روی هر هاست استاتیک — GitHub Pages، Cloudflare Pages، Vercel، Netlify یا سرور خودتان.
   ```bash
   # نمونه: GitHub Pages
   git add index.html
   git commit -m "Deploy lottery mini app"
   git push
   # سپس از مسیر Settings → Pages گزینه‌ی Pages را فعال کنید
   ```
2. **یک ربات بسازید** با [@BotFather](https://t.me/BotFather) → دستور `/newbot`.
3. **مینی‌اپ را ثبت کنید** → `/newapp` (یا یک Menu Button تنظیم کنید) و آدرس آن را به فایل میزبانی‌شده وصل کنید.
4. ربات را باز کنید و روی دکمه بزنید — تمام! 🎉

> 💡 نکته: تلگرام نیازمند HTTPS است. GitHub Pages و Cloudflare Pages آن را رایگان فراهم می‌کنند.

### 🧩 پشته‌ی فناوری

- **HTML5 + CSS3** (متغیرهای سفارشی، Grid، انیمیشن‌ها)
- **جاوااسکریپت خالص** (کنترلرهای ماژولار `State`، `UI`، `Lottery`، `Donate`، `Fairness`، `I18N`)
- **Web Crypto API** (SHA-256 / HMAC)
- **Telegram WebApp SDK**
- **TonAPI** (موجودی و تراکنش‌ها) · **TONScan** (لینک‌های اکسپلورر)

### 🔧 پیکربندی

همه‌ی تنظیمات در یک بلوک `CONFIG` نزدیک ابتدای اسکریپت قرار دارند:

| کلید | توضیح |
|------|-------|
| `ADDRESS` | آدرس کیف‌پول TON شما (فرمت Friendly) |
| `TONAPI_BASE` | آدرس پایه‌ی TonAPI |
| `EXPLORER_URL` | آدرس پایه‌ی اکسپلورر برای لینک آدرس/تراکنش (TONScan) |
| `CACHE_TTL` | مدت‌زمان کش‌شدن داده‌های بلاکچین (میلی‌ثانیه) |

برای استفاده از کیف‌پول خودتان، کافی است `ADDRESS` را تغییر دهید — آدرس خام (raw) به‌صورت خودکار در زمان اجرا محاسبه می‌شود.

### 🛡️ نکات امنیتی

- Server Seed خام تا زمانی که فعال است **هرگز** فاش نمی‌شود — فقط هش آن (تعهد) نمایش داده می‌شود.
- تمام تصادفی‌سازی سمت کلاینت با Web Crypto API انجام می‌شود.
- هیچ کلید خصوصی یا رازی در اپ ذخیره نمی‌شود؛ اپ فقط داده‌های عمومی روی زنجیره را **می‌خواند**.

### 💸 حمایت

اگر این پروژه برایتان مفید بود، با دونیت TON به کیف‌پول بالا حمایت کنید یا به مخزن ⭐ بدهید!

### 📄 مجوز

تحت مجوز **MIT** منتشر شده است — فایل [`LICENSE`](LICENSE) را ببینید.

</div>

---

<div align="center">

⭐ **Star this project if you find it useful! · اگر مفید بود ستاره بدهید!**

Made with ❤️ for the TON & Telegram community

</div>
