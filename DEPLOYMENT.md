# Wine Label Copy Generator - Deployment Guide

## What You've Built

An AI-powered wine label copywriting tool that:
- Generates 3-4 professional back-label copy variations
- Features elegant wine-industry design (Cormorant serif + Lato sans)
- Includes simple captcha verification
- Rate limiting: 25 generations/day total, 3/day per user
- Pre-loaded demo with your Sebastopol Gamay Noir
- One-click copy to clipboard

## Files Included

1. **wine-label-generator.html** - The complete React app (HTML + embedded JS)
2. **package.json** - Vercel deployment metadata
3. **vercel.json** - Vercel routing configuration
4. **DEPLOYMENT.md** - This guide

## Deployment Steps

### 1. Get Your Anthropic API Key

1. Go to https://console.anthropic.com/
2. Sign in or create account
3. Navigate to "API Keys"
4. Click "Create Key"
5. Copy the key (starts with `sk-ant-`)
6. **Set rate limits on the key:**
   - Go to the key settings
   - Set: Max requests per day = 25
   - This is your backup safety limit

### 2. Deploy to Vercel

**Option A: Using Vercel CLI (Recommended)**

1. Install Vercel CLI:
   ```bash
   npm install -g vercel
   ```

2. Navigate to your project folder containing these files

3. Login to Vercel:
   ```bash
   vercel login
   ```

4. Deploy:
   ```bash
   vercel
   ```

5. Follow prompts:
   - "Set up and deploy?" → Yes
   - "Which scope?" → Your personal account
   - "Link to existing project?" → No
   - "What's your project's name?" → wine-label-generator (or whatever you prefer)
   - "In which directory is your code located?" → ./

6. Add your API key as environment variable:
   ```bash
   vercel env add ANTHROPIC_API_KEY
   ```
   - Choose "production"
   - Paste your API key
   - Redeploy: `vercel --prod`

**Option B: Using Vercel Dashboard**

1. Go to https://vercel.com/
2. Sign up/login with GitHub, GitLab, or Bitbucket
3. Click "Add New..." → "Project"
4. Import this project (upload files or connect Git repo)
5. In "Environment Variables":
   - Add variable: `ANTHROPIC_API_KEY`
   - Value: your API key from step 1
6. Click "Deploy"

### 3. Update the HTML with Environment Variable

After deploying, you need to update the API key reference in the HTML.

The line in `wine-label-generator.html` currently says:
```javascript
'x-api-key': 'YOUR_API_KEY_HERE'
```

**For client-side apps (current setup):**
Since this is a pure frontend app, you have two options:

**Option 1: Hardcode the key (simple, less secure)**
Replace `'YOUR_API_KEY_HERE'` with your actual API key. This exposes the key in the client but is acceptable for a portfolio demo with rate limits.

**Option 2: Create a Vercel serverless function (more secure)**
Create an API proxy to hide the key. I can help you set this up if you want.

For now, **Option 1 is fine** since:
- You have rate limits on the API key (25/day)
- App has client-side rate limiting (3/user/day)
- It's a portfolio demo with minimal traffic
- You can rotate the key anytime

### 4. Custom Domain (Optional)

If you own kaeyenwong.com:

1. In Vercel dashboard, go to your project
2. Click "Settings" → "Domains"
3. Add: `wine-label-ai.kaeyenwong.com`
4. Follow DNS instructions to point subdomain to Vercel
5. Wait for SSL certificate (automatic, ~5 minutes)

Or use the free Vercel URL: `wine-label-generator.vercel.app`

## Testing After Deployment

1. Visit your deployed URL
2. Click "Load Sebastopol Demo" to populate fields
3. Check the captcha
4. Click "Generate Label Copy"
5. Verify 3-4 variations appear
6. Test copy-to-clipboard buttons

## Rate Limit Monitoring

The app stores rate limit data in browser localStorage:
- Resets daily at midnight
- 25 total generations/day
- 3 per user fingerprint/day

**Monitor API usage:**
- Check Anthropic Console: https://console.anthropic.com/settings/usage
- Set up billing alerts if needed

**If you exceed limits:**
- Rotate your API key in Vercel environment variables
- Adjust rate limits in the HTML (search for `RATE_LIMIT`)

## Updating the App

To make changes:

1. Edit `wine-label-generator.html`
2. Redeploy:
   ```bash
   vercel --prod
   ```

## Troubleshooting

**"API request failed" error:**
- Check if API key is correctly set
- Verify key hasn't hit rate limits
- Check browser console for detailed error

**Rate limit not working:**
- Uses localStorage - works per-browser
- Users can bypass by clearing localStorage (acceptable for portfolio demo)

**CORS errors:**
- Anthropic API supports CORS, but if issues arise, you'll need the serverless function proxy

**Styling issues:**
- Google Fonts must load (requires internet)
- Test in Chrome, Firefox, Safari

## Cost Estimates

**Anthropic API:**
- ~800 tokens per generation (500 input + 300 output)
- Cost: ~$0.006 per generation
- 25 generations/day max = ~$0.15/day = $4.50/month worst case
- Realistic usage (10-15/week) = ~$0.20/month

**Vercel Hosting:**
- Free tier includes:
  - 100GB bandwidth
  - Unlimited deployments
  - Custom domains
- This app will never exceed free tier

**Total monthly cost: $0.20 - $4.50** depending on usage

## Portfolio Presentation

Add to your Cargo site:
- Thumbnail: Screenshot of the tool
- Title: "Wine Label Copy Generator — AI Tool"
- Description: "AI-powered copywriting tool for small wineries. Demonstrates strategic thinking about AI as creative multiplier + domain expertise in wine/food/beverage."
- Link: Your Vercel URL

In interviews, frame it as:
- **Problem:** Small producers can't afford agency copywriters
- **Solution:** AI tool that generates professional copy variations
- **Your role:** Strategy, prompt engineering, UX design, wine industry knowledge
- **Demonstrates:** AI fluency, understanding of brand voice systems, domain expertise

## Security Notes

- API key is exposed in client code (acceptable for portfolio demo)
- Rate limiting provides cost protection
- No sensitive user data collected
- No backend database needed
- Can rotate API key anytime without code changes (via Vercel env vars)

## Next Steps

1. Deploy to Vercel (10 minutes)
2. Test thoroughly
3. Add to portfolio
4. Share in job applications/interviews
5. Monitor usage in Anthropic console

Questions? Issues? Let me know and I'll help troubleshoot.
