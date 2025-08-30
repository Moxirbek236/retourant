# Restoran Tizimi — Flask

Funktsiyalar:
- Kirish sahifasi: **Foydalanuvchi** va **Xodim** tugmalari
- Foydalanuvchi: ism kiritadi → avtomatik tartib raqami (ticket) va **ETA** (qanchada tayyor) ko'rsatiladi
- Xodim: ID + parol bilan kiradi
- Xodim registratsiyasi: ism, familiya, tug'ilgan sana, telefon, parol → avtomatik **ID** beriladi
- Ma'lumotlar **SQLite** bazasida saqlanadi
- Xodim paneli: barcha buyurtmalar ro'yxati, **Foydalanuvchi kutmoqda** va **Foydalanuvchiga berildi** holatlari
- Xodim paneli va foydalanuvchi holati avtomatik yangilanadi (10s)

## Ishga tushirish
1) Python 3.10+ o'rnating.
2) Virtual muhit (ixtiyoriy):
```bash
python -m venv .venv
# Windows:
python -m venv .venv
# Linux/Mac:
source .venv/bin/activate
```
3) Kutubxonalar:
```bash
pip install flask werkzeug
```
4) Ishga tushirish:
```bash
python app.py
```
Brauzerda oching: http://localhost:5000

### Sozlamalar (ixtiyoriy)
- `AVG_PREP_MINUTES` — bir buyurtmaning o'rtacha tayyorlanish vaqti (default 7 daqiqa)
- `SECRET_KEY` — sessiya uchun kalit

Windows PowerShell misol:
```powershell
$env:AVG_PREP_MINUTES="5"
$env:SECRET_KEY="yashirin_kalit"
python app.py
```

## Tuzilma
```
app.py
templates/
  base.html
  index.html
  user.html
  user_success.html
  staff_login.html
  staff_register.html
  staff_dashboard.html
static/
  style.css
  main.js
database.sqlite3 (avtomatik yaratiladi)
```

## Eslatma
- Parollar **xeshlanadi**.
- Xodim ID raqami registratsiya yakunida **flash xabar** orqali ko'rsatiladi.
- Realtime talab qilinmasa ham, avtomatik yangilanish uchun 10s polling qo'shilgan.
- Agar boshqa maydonlar kerak bo'lsa (masalan, menyu, narxlar, to'lov), keyingi bosqichda qo'shamiz.
