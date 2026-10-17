# Hermes Calendar — Google Cloud Branding Handover

มอบหมายงานนี้ให้ใครรับต่อ เพื่อตั้ง **Google Cloud Project branding** สำหรับใช้งาน OAuth (Calendar API)

## ข้อมูลพื้นฐาน

| รายการ | ค่า |
|---|---|
| App name | Hermes Calendar |
| Support email | watcharapun.ta@gmail.com |
| Website (Home) | `https://phrem.github.io/hermes-calendar-site/` |
| Privacy Policy | `https://phrem.github.io/hermes-calendar-site/privacy.html` |
| Terms of Service | `https://phrem.github.io/hermes-calendar-site/terms.html` |
| GitHub repo | `phrem/hermes-calendar-site` (ต้องเป็น **public**) |
| Project ID (ตัวอย่าง) | `hermes-cal-509707` |

## ขั้นตอนทำ (ทำทั้งหมดนี้)

1. **เตรียม repo** — เปิด https://github.com/phrem/hermes-calendar-site/settings
   - ถ้ายังเป็น private → Settings → General → Change repository visibility → **Make public**
   - เปิด Pages: Settings → Pages → Source: **Deploy from a branch** → Branch: `main`, folder `/ (root)` → Save

2. **ยืนยันว่าเว็บ live** — เปิด 3 URL ข้างบนนี้ให้ครบ
   - Home: `https://phrem.github.io/hermes-calendar-site/`
   - Privacy: `https://phrem.github.io/hermes-calendar-site/privacy.html`
   - Terms: `https://phrem.github.io/hermes-calendar-site/terms.html`

3. **กรอก Google Cloud** — เปิด https://console.cloud.google.com/auth/branding?project=hermes-cal-509707
   - **App name**: `Hermes Calendar`
   - **Support email**: `watcharapun.ta@gmail.com`
   - **Logo**: upload logo ถ้ามี (ไม่มีข้ามได้)
   - **Website / Privacy policy**:
     - Website: `https://phrem.github.io/hermes-calendar-site/`
     - Privacy policy: `https://phrem.github.io/hermes-calendar-site/privacy.html`
   - กด **Save**

4. **Publish app** — กลับมาที่หน้า Consent screen
   - กด **PUBLISH APP / MOVE TO PRODUCTION**
   - Confirm
   - (ถ้ามี audit / verification step ก็ทำตาม)

5. **ออก token**
   - เปิด https://console.cloud.google.com/apis/credentials → สร้าง/ใช้ OAuth Client ID (Web application)
   - ที่ redirect URIs: เพิ่ม `http://localhost:8080/callback` (ตามที่ใช้)
   - **หรือ** ใช้ OAuth Playground: https://developers.google.com/oauthplayground
     - เลือก Calendar API → Authorize → **copy `refresh_token`**

6. **ส่ง refresh_token ให้ผู้รับ**
   - ส่งผ่านช่องทางปลอดภัย (chat ปิด หรือ password-protected note)
   - ⚠️ **อย่า** commit / paste เข้า repo ใดๆ

## Checklist ก่อนส่งมือ

- [ ] Repo `phrem/hermes-calendar-site` เป็น **public**
- [ ] GitHub Pages เปิด → 3 URL (home/privacy/terms) เปิดได้ด้วยคลิก
- [ ] Cloud Console Branding หน้า save แล้วเห็น `Hermes Calendar` + email
- [ ] Consent screen แสดง **Status: In Production**
- [ ] ได้ `refresh_token` มาส่งแล้ว

## Note

- Refresh token อายุใช้งาน: ตราบใดที่ไม่ถูก revoke (Google อาจ invalidate ถ้าไม่ใช้ ~6 เดือน)
- ถ้า Google ยิง audit / re-verify: แก้ policy → push → update URL ใน Console
