# Dropship Pro — Setup Guide

## Files
- `index.html` — Main storefront (upload to GitHub Pages root)
- `admin.html` — Admin panel
- `schema.sql` — Supabase database schema

## 1. Supabase Setup
1. Create project at [supabase.com](https://supabase.com)
2. Go to SQL Editor → paste contents of `schema.sql` → Run
3. Copy your **Project URL** and **anon/public key** from Settings → API

## 2. Update Config
In both `index.html` and `admin.html`, replace:
```js
const SUPABASE_URL = 'YOUR_SUPABASE_URL';
const SUPABASE_KEY = 'YOUR_SUPABASE_ANON_KEY';
const RAZORPAY_KEY = 'YOUR_RAZORPAY_KEY_ID'; // index.html only
```

## 3. Razorpay Setup
1. Create account at [razorpay.com](https://razorpay.com)
2. Get your **Key ID** (public) → paste in `index.html`
3. Get your **Key Secret** (private) → add to Supabase Edge Function env vars
4. Deploy Edge Function: `supabase functions deploy create-razorpay-order`
5. Add env var: `supabase secrets set RAZORPAY_KEY_SECRET=your_secret`

## 4. Admin Access
- URL: `yourdomain.com/admin.html`
- Demo login: `admin@demo.com` / `admin123`
- Production: Create user in Supabase Auth → Dashboard → Authentication

## 5. GitHub Pages
```
Settings → Pages → Source: Deploy from branch → main → / (root)
```

## Features
- ✅ Product catalog with search + filter
- ✅ Excel/CSV sheet parser (matches product by name)
- ✅ 4-step order flow: Upload → Price → COD/Prepaid split → Payment
- ✅ Razorpay payment integration
- ✅ Admin: Add/Edit/Delete products, manage orders, update status
- ✅ Mobile responsive with bottom nav
- ✅ Dark luxury UI with amber accents

## Policy Config (via Admin → Settings)
- Return window: 4 days
- Unboxing video required for returns
- COD charge is non-refundable
