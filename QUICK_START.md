# 🚀 QUICK START GUIDE

## 1️⃣ Files Download करें
ZIP file download करें और extract करें

## 2️⃣ तुरंत Deploy करें (सबसे आसान तरीका)

### Vercel पर (1 मिनट में LIVE) ⚡

1. **https://vercel.com** पर जाएं और Sign Up करें
2. "Add New Project" > "Upload"
3. अपनी files upload करें
4. "Deploy" पर क्लिक करें
5. **DONE!** आपकी website LIVE है! 🎉

आपको मिलेगा: `https://your-project.vercel.app`

---

### या Render पर (FREE Forever)

1. **https://render.com** पर Sign Up करें
2. "New Web Service" पर क्लिक करें
3. GitHub से connect करें या files upload करें
4. Settings:
   - Build: `npm install`
   - Start: `npm start`
5. "Create" पर क्लिक करें

---

## 3️⃣ Local Testing (अपने Computer पर)

```bash
# 1. Node.js install करें (अगर नहीं है)
# Download: https://nodejs.org

# 2. Project folder में जाएं
cd subhash-video-downloader

# 3. Dependencies install करें
npm install

# 4. Server start करें
npm start

# 5. Browser में खोलें
# http://localhost:3000
```

---

## 📱 Features

✅ YouTube - Videos + Shorts
✅ Instagram - Reels + Posts + Stories
✅ Facebook - Videos
✅ TikTok - Videos
✅ Twitter/X - Videos
✅ Snapchat - Stories

---

## 🎯 100,000+ Users Support

- **Rate Limiting:** 100 requests/min per IP
- **Performance:** High-speed API
- **Security:** Helmet + CORS + Validation
- **Scalable:** Ready for production

---

## ⚙️ Customize करें (Optional)

### Colors बदलें:
`public/index.html` में CSS edit करें

### Rate Limit बदलें:
`server.js` में:
```javascript
const rateLimiter = new RateLimiterMemory({
  points: 100,    // requests per window
  duration: 60,   // time window in seconds
});
```

---

## 🐛 Problems?

**"Module not found"**
```bash
npm install
```

**"Port in use"**
- `.env` file में PORT change करें

**Download नहीं हो रहा**
- URL check करें
- Different quality try करें

---

## 📞 Need Help?

1. `README.md` पढ़ें - detailed guide
2. `DEPLOYMENT_GUIDE.md` पढ़ें - Hindi में full deployment
3. Logs check करें

---

## 🎉 Ready!

अब आप कहीं भी deploy कर सकते हैं:
- Vercel ✅
- Render ✅
- Railway ✅
- Heroku ✅
- Your own VPS ✅

**All files included - No crash, Production ready!** 🚀
