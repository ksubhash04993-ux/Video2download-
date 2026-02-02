# 🚀 DEPLOYMENT GUIDE (हिंदी में)

## आसान तरीके से अपनी Website Live करें

### विकल्प 1: Vercel (सबसे आसान - FREE) ⭐ RECOMMENDED

**स्टेप 1:** Vercel पर अकाउंट बनाएं
- https://vercel.com पर जाएं
- "Sign Up" पर क्लिक करें
- GitHub/Google से sign up करें

**स्टेप 2:** Project Upload करें
- Dashboard में "Add New Project" पर क्लिक करें
- "Upload" चुनें या GitHub से connect करें
- अपने project की सभी files select करें

**स्टेप 3:** Deploy करें
- "Deploy" बटन पर क्लिक करें
- 2-3 मिनट wait करें
- आपकी website LIVE हो जाएगी! 🎉

**आपको मिलेगा:** `https://your-project-name.vercel.app`

---

### विकल्प 2: Render (FREE Forever)

**स्टेप 1:** Render पर अकाउंट बनाएं
- https://render.com पर जाएं
- "Get Started for Free" पर क्लिक करें

**स्टेप 2:** New Web Service बनाएं
- Dashboard में "New +" पर क्लिक करें
- "Web Service" चुनें
- GitHub repository connect करें (या public Git URL दें)

**स्टेप 3:** Settings भरें
- **Name:** `subhash-downloader`
- **Build Command:** `npm install`
- **Start Command:** `npm start`
- **Instance Type:** Free

**स्टेप 4:** Create Web Service
- "Create Web Service" पर क्लिक करें
- 5-10 मिनट में LIVE हो जाएगी

**आपको मिलेगा:** `https://subhash-downloader.onrender.com`

---

### विकल्प 3: Railway (FREE $5 Credit)

**स्टेप 1:** Railway पर अकाउंट बनाएं
- https://railway.app पर जाएं
- "Start a New Project" पर क्लिक करें

**स्टेप 2:** Deploy from GitHub
- "Deploy from GitHub repo" चुनें
- या "Empty Project" > "Deploy from a template"

**स्टेप 3:** Settings
- GitHub repo select करें
- Auto-detect करेगा Node.js
- "Deploy" पर क्लिक करें

**आपको मिलेगा:** Railway domain (बाद में custom domain add कर सकते हैं)

---

### विकल्प 4: अपना खुद का Server (VPS)

अगर आपके पास **VPS** है (DigitalOcean, AWS, Linode, etc.):

**स्टेप 1:** Server में SSH करें
```bash
ssh root@your-server-ip
```

**स्टेप 2:** Node.js Install करें
```bash
# Ubuntu/Debian
curl -fsSL https://deb.nodesource.com/setup_18.x | sudo -E bash -
sudo apt-get install -y nodejs

# Check installation
node --version
npm --version
```

**स्टेप 3:** Project Files Upload करें
- FileZilla या WinSCP use करें
- या Git से clone करें:
```bash
git clone your-repo-url
cd your-project-folder
```

**स्टेप 4:** Dependencies Install करें
```bash
npm install
```

**स्टेप 5:** PM2 Install करें (server को हमेशा चालू रखने के लिए)
```bash
npm install -g pm2
```

**स्टेप 6:** Server Start करें
```bash
pm2 start server.js --name video-downloader
pm2 startup
pm2 save
```

**स्टेप 7:** Nginx Setup (Domain के लिए)
```bash
sudo apt install nginx
sudo nano /etc/nginx/sites-available/default
```

File में यह add करें:
```nginx
server {
    listen 80;
    server_name your-domain.com;

    location / {
        proxy_pass http://localhost:3000;
        proxy_http_version 1.1;
        proxy_set_header Upgrade $http_upgrade;
        proxy_set_header Connection 'upgrade';
        proxy_set_header Host $host;
        proxy_cache_bypass $http_upgrade;
    }
}
```

Nginx Restart करें:
```bash
sudo systemctl restart nginx
```

**स्टेप 8:** Firewall खोलें
```bash
sudo ufw allow 80
sudo ufw allow 443
sudo ufw enable
```

---

## 🌐 Custom Domain Add करना

### Vercel/Render/Railway पर:

1. **Domain खरीदें** (GoDaddy, Namecheap, etc.)

2. **DNS Settings में जाएं**

3. **CNAME Record Add करें:**
   - Name: `@` या `www`
   - Value: आपका deployment URL

4. **Dashboard में Domain Add करें:**
   - Settings > Domains
   - अपना domain enter करें
   - Verify करें

5. **Wait करें** (10-30 मिनट)

---

## 🔧 महत्वपूर्ण Settings

### Environment Variables सेट करें:

Vercel/Render/Railway Dashboard में:
- `PORT` = 3000
- `NODE_ENV` = production

---

## ✅ चेकलिस्ट - Deployment से पहले

- [ ] सभी files upload हो गई हैं
- [ ] `package.json` सही है
- [ ] `.env` file बनाई है (optional)
- [ ] `server.js` में कोई error नहीं है
- [ ] Port settings सही हैं

---

## 🐛 Common Problems & Solutions

### Problem 1: "Cannot find module"
**Solution:**
```bash
npm install
```

### Problem 2: Port already in use
**Solution:**
- `.env` file में PORT change करें
- या server restart करें

### Problem 3: Website नहीं खुल रही
**Solution:**
- Check server logs
- Firewall settings check करें
- DNS propagation का wait करें (24 घंटे तक)

### Problem 4: Download काम नहीं कर रहा
**Solution:**
- URL सही है check करें
- Different quality try करें
- Browser console check करें (F12)

---

## 📊 100,000+ Users Handle करने के लिए

### Recommended Configuration:

**Minimum Requirements:**
- RAM: 4GB+
- CPU: 2 cores+
- Bandwidth: 100GB/month

**Optimization Tips:**
1. **CDN Use करें** - Cloudflare (Free)
2. **Caching Enable करें** - Redis
3. **Load Balancer** - Multiple instances
4. **Database** - PostgreSQL/MongoDB (for logs)
5. **Monitoring** - PM2, Datadog

---

## 🎯 Quick Start Commands

### Local Testing:
```bash
npm install
npm start
# Open: http://localhost:3000
```

### Production Deploy (PM2):
```bash
npm install
pm2 start server.js --name video-downloader
pm2 logs video-downloader
```

### Update Website:
```bash
git pull
npm install
pm2 restart video-downloader
```

---

## 💡 Pro Tips

1. **Cloudflare Free CDN** use करें - faster loading
2. **SSL Certificate** लगाएं - https://letsencrypt.org (Free)
3. **Regular backups** लें
4. **Monitor logs** - `pm2 logs`
5. **Rate limiting** enable रखें - spam से बचने के लिए

---

## 📞 Help चाहिए?

1. Server logs check करें: `pm2 logs`
2. Browser console check करें (F12)
3. Network tab में API calls देखें
4. README.md फिर से पढ़ें

---

## 🎉 Congratulations!

आपकी website अब LIVE है! 🚀

**Next Steps:**
1. Social media पर share करें
2. Domain add करें (optional)
3. Analytics add करें (Google Analytics)
4. SEO optimize करें

**याद रखें:**
- Regular updates करते रहें
- Server monitor करते रहें
- Backup लेते रहें

---

⚡ **अब आप तैयार हैं!** किसी भी hosting platform पर deploy करें
