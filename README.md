# Dino Albizzati — Portfolio (deploy)

Static multi-page site, ready for GitHub Pages / Netlify / Vercel. No build step.

## Structure
- index.html ............ home
- case-studies/*.html ... 4 case study pages
- support.js ............ runtime (do not remove; a copy also lives in case-studies/)
- SiteHeader.dc.html .... shared header fragment (root + case-studies/)

## Before it looks complete, add:
1. Dino_Albizzati_CV.pdf at the repo root (the "Download My Resume" buttons point here).
2. The media folder `assets/` at the repo root, with these files:
   assets/passover/ : reel.mp4, ad-cold-contacts.jpg, ad-mid-campaign.jpg, ad-remarketing.jpg, menu-photo.jpg, email-1.jpg, email-2.jpg, email-3.jpg
   assets/hanukkah/ : email-hanukkah.png, email-shofar.png, ad-holiday-1.png, ad-holiday-2.png
   assets/farmers-market/ : market-video.mp4, incentive-card-1.jpg, incentive-card-2.jpg, a-frame.jpg, bagel-fest-sign.jpg
   assets/super-bowl/ : touchdown-ad.mp4, carousel-1.jpg, carousel-2.jpg, carousel-3.jpg, reheating-instructions.jpg
   assets/shared/ : website-popup-desktop.jpg, website-popup-mobile.jpg
   (Filenames must match exactly — the pages reference these paths.)

## GA4
Replace every G-XXXXXXXXXX with your Measurement ID (index.html + the 4 case pages).

## Contact form
Currently opens the visitor's mail client (mailto). To receive submissions automatically,
wire the <form> action to Formspree and change the submit handler — just ask.

## GitHub Pages
Push these files to the repo root, enable Pages on the main branch (root), point your domain.
