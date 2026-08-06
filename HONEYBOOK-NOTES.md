# HoneyBook embed — implementation notes

## The short answer to "do you need my HoneyBook login?"

**No.** The embed code runs in the visitor's browser, so it's public on the live site. I pulled it straight off `919golfco.com/book-now`.

## The actual snippet currently on the live site

```html
<script>
  (function(h,b,s,n,i,p,e,t) {
    h._HB_ = h._HB_ || {};h._HB_.pid = i;;;;
    t=b.createElement(s);t.type="text/javascript";t.async=!0;t.src=n;
    e=b.getElementsByTagName(s)[0];e.parentNode.insertBefore(t,e);
})(window,document,"script","https://widget.honeybook.com/assets_users_production/websiteplacements/placement-controller.min.js","6a300ce8bbde8b2fb28d6b28");
</script>
```

Placement ID: `6a300ce8bbde8b2fb28d6b28`

This lives in Squarespace under **Settings → Advanced → Code Injection → Header**. Don't delete it — it's the entire booking, contract, and payment flow.

## Why the mockups don't run the live embed

A real submission on a mockup creates a **real lead in his HoneyBook pipeline**. Four directions × anyone clicking through = junk inquiries he has to sort out from actual customers.

So the Book Now pages show a designed form using the exact field list from his real HoneyBook form, with inputs disabled. Swapping in the live embed is a two-line change whenever he wants it.

## Fields on the real form

| Field | Required |
|---|---|
| Full name | Yes |
| Email | Yes |
| Phone number | Yes |
| Event address (street, city, state, zip) | Yes |
| Start date / Start time | Yes |
| End date / End time | Yes |
| How did you hear about us? | No |
| Additional booking information | No |

Plus an SMS consent line and Google reCAPTCHA notice.

## The design problem worth solving

On the live site the HoneyBook form renders in **HoneyBook's own styling** — cream panel, grey inputs, full-color Facebook and Instagram icons — sitting inside a green-and-gold page. It reads as a third-party form bolted onto the site, which is a real part of why the page feels less polished than the rest.

Three options, cheapest first:

1. **Style it inside HoneyBook.** HoneyBook lets you set brand colors, fonts, and a logo on its forms. Free, no code, and it gets most of the way there. Do this first regardless.
2. **Frame it better.** Put the embed in a contained column with on-brand content beside it — that's the approach in these mockups: "what happens next" on the left, form on the right. The form stops feeling like an orphan even if its internals stay HoneyBook-styled.
3. **Build a native form that hands off.** A fully on-brand form on the site that posts into HoneyBook. Most control, most work, and it risks breaking the contract/deposit automation. Not worth it unless 1 and 2 fall short.

## One conversion note

The current Book Now page opens cold with a long form and no context. The mockups add a short **"what happens next"** column — reply time, deposit amount, that the deposit counts toward the total, free weather rescheduling, and that setup is handled.

Every one of those answers a hesitation someone has right before submitting. It's the cheapest conversion improvement available here, and it's pure copy — no code.

## Deposit inconsistency — needs a decision

- **Homepage:** "pay a 50% deposit"
- **FAQ:** "50% for The Tee Time & The Scramble. 25% for The Invitational."

These contradict each other. Someone booking the Invitational is being quoted double what they actually owe. The mockups use the FAQ version, but confirm which is correct and make it consistent across the homepage, FAQ, Book Now page, and the HoneyBook form itself.
