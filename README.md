# Wine Label Copy Generator

AI-powered back-label copywriting tool for wine producers. Built as a portfolio demonstration by Kae Yen Wong.

## Overview

This tool generates professional wine label copy variations based on tasting notes, winery details, and brand personality. It demonstrates:

- **AI as creative multiplier** — not replacement, but amplification of human expertise
- **Domain knowledge application** — wine industry understanding + copywriting craft
- **Strategic prompt engineering** — operationalizing brand voice systems at scale
- **Thoughtful UX design** — appropriate to wine industry, not generic tech aesthetics

## Features

- 🍷 **4 personality modes:** Poetic, Technical, Approachable, Luxury
- 📝 **3-4 copy variations** per generation showing different strategic approaches
- 🎨 **Wine-industry design** using Cormorant serif + Lato, warm cream/burgundy palette
- 🔒 **Rate limiting:** 25/day total, 3/day per user
- 📋 **One-click clipboard** copy for each variation
- 🤖 **Simple captcha** to prevent bot abuse
- 🌱 **Pre-loaded demo** featuring Sebastopol Gamay Noir

## Technology

- **Frontend:** React 18 (standalone HTML, no build step)
- **AI:** Anthropic Claude API (Sonnet 4)
- **Hosting:** Vercel (free tier)
- **Fonts:** Google Fonts (Cormorant, Lato)
- **Rate Limiting:** Client-side localStorage + API key limits

## Use Case

Built for **small wineries and boutique producers** who can't afford agency copywriters but need professional, differentiated label copy. Shows how AI can democratize access to creative services while maintaining craft quality.

## Portfolio Context

This project demonstrates:

1. **Strategic thinking** — understanding the real problem (cost barrier for small producers)
2. **AI fluency** — prompt engineering to generate brand-appropriate output
3. **Domain expertise** — wine industry knowledge + copywriting craft
4. **Execution quality** — production-ready UI, not prototype-quality

Particularly relevant for roles in:
- Wine/food/beverage brands
- Consumer goods
- Lifestyle/hospitality
- Any brand serving small business customers

## Deployment

See `DEPLOYMENT.md` for complete deployment instructions.

Quick start:
```bash
vercel
vercel env add ANTHROPIC_API_KEY
vercel --prod
```

## License

Portfolio demonstration project © 2026 Kae Yen Wong

## Contact

Built by Kae Yen Wong  
Portfolio: https://kaeyenwong.com  
LinkedIn: [Your LinkedIn]
