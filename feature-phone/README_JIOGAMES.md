# 🎮 JioGames Integration Guide - Pacman

## ✅ क्या-क्या Ready है

### 1. Manifest File
- ✅ `manifest.webapp` - KaiOS के लिए
- ✅ App name, description, icons configured
- ✅ Permissions set (storage, audio)
- ✅ Hindi & English locales

### 2. JioGames SDK
- ✅ `jiogames_sdk.js` - Complete SDK wrapper
- ✅ All console logs enabled for debugging
- ✅ Ad integration (Interstitial & Rewarded Video)
- ✅ Leaderboard integration (postScore)
- ✅ User profile support

### 3. Game Files
- ✅ `index.html` - Updated with SDK integration
- ✅ `style.css` - Feature phone optimized
- ✅ `app.js` - Game logic
- ✅ Key mappings for JioPhone

---

## 📁 File Structure

```
feature-phone/
├── index.html              # Main game file (SDK integrated)
├── jiogames_sdk.js         # JioGames SDK (with console logs)
├── app.js                  # Game logic
├── style.css               # Styles
├── manifest.webapp         # KaiOS manifest
├── icons/                  # App icons folder
│   ├── icon-56.png        # 56x56 icon (create this)
│   ├── icon-112.png       # 112x112 icon (create this)
│   └── README.md          # Icon creation guide
└── README_JIOGAMES.md     # This file
```

---

## 🔧 SDK Configuration

### Package Details (jiogames_sdk.js में)

```javascript
var packageName = "com.jiogames.pacman";
var adSpotInterstitial = "zbjnq9gs";    // Test ad spot
var adSpotRewardedVideo = "81xnt9bw";   // Test ad spot
var banner_ZoneKey = "l9mp2wfq";        // Test banner
```

**⚠️ Important:** JioGames dashboard से approval के बाद real ad spot keys update करें!

---

## 🎯 SDK Functions

### 1. Post Score (Leaderboard)
```javascript
// Game over par call karein
postScore(currentScore);

// Example:
var finalScore = 5000;
postScore(finalScore);  // Console में log दिखेगा
```

### 2. Cache & Show Ads

#### Interstitial Ad (MidRoll)
```javascript
// Game start par cache karein
cacheAd();

// Game over par show karein
showAd();
```

#### Rewarded Video
```javascript
// Level start par cache karein
cacheAdRewarded();

// Extra life button par show karein
showAdRewarded();

// User को reward milega onAdClosed callback में
```

### 3. Get User Profile
```javascript
// Game start par call karein
getUserProfile();

// Response onUserProfileResponse() callback में milega
```

---

## 📊 Console Logs

Har function console में detailed logs print karega:

### SDK Loading
```
=== JioGames SDK Loading... ===
JioGames SDK: Configuration loaded
JioGames SDK: Package Name: com.jiogames.pacman
=== JioGames SDK Initialized Successfully! ===
```

### Ad Caching
```
=== JioGames: cacheAd() called ===
Current isAdReady state: false
JioGames: Initiating MidRoll ad cache...
=== JioGames: cacheAdMidRoll() ===
```

### Ad Ready
```
=== JioGames: onAdPrepared Callback ===
Ad Spot Key: zbjnq9gs
JioGames: MidRoll ad is ready!
```

### Showing Ad
```
=== JioGames: showAd() called ===
Is Ad Ready: true
JioGames: Showing MidRoll ad...
```

### User Profile
```
=== JioGames: onUserProfileResponse Callback ===
=== User Profile Data ===
Gamer ID: T9EMNU++dbtW0sdadgo83m...
Gamer Name: Player19998
Device Type: sp
```

---

## 🎮 Testing

### Browser में Test करें:

1. **Open Console:**
   - Chrome: F12 → Console tab
   - Firefox: F12 → Console tab

2. **Open Feature Phone Version:**
   ```
   feature-phone/index.html
   ```

3. **Check Logs:**
   - SDK initialization logs
   - Key press logs
   - Ad function calls
   - User profile logs

### Expected Console Output:
```
=== JioGames SDK Loading... ===
=== Initializing Feature Phone Controls ===
=== JioGames SDK Initialized Successfully! ===
=== JioGames: DOM Content Loaded ===
JioGames: Fetching user profile...
JioGames: Caching ads...
=== Testing JioGames Integration ===
```

---

## 🚀 JioGames पर Publish करने के Steps

### Step 1: Register
1. जाएं: https://publish.jiogames.com
2. Developer account बनाएं
3. Verification complete करें

### Step 2: App Details
1. Package name: `com.jiogames.pacman`
2. App name: "Pacman Game"
3. Description लिखें
4. Category: Games
5. Screenshots upload करें

### Step 3: Ad Spots बनाएं
1. JioAds dashboard में login करें
2. Create App/Game
3. Interstitial ad spot create करें
4. Rewarded video ad spot create करें
5. Banner ad spot create करें (optional)

### Step 4: SDK में Update करें
```javascript
// jiogames_sdk.js में update करें:
var packageName = "com.jiogames.YOUR_PACKAGE";
var adSpotInterstitial = "YOUR_INTERSTITIAL_KEY";
var adSpotRewardedVideo = "YOUR_REWARDED_KEY";
```

### Step 5: Icons बनाएं
```bash
# 56x56 और 112x112 icons create करें
# icons/ folder में save करें
```

### Step 6: Package बनाएं
```bash
# Feature-phone folder को ZIP करें
zip -r pacman-jiogames.zip feature-phone/

# या manually ZIP file बनाएं
```

### Step 7: Upload & Submit
1. Developer console में जाएं
2. ZIP file upload करें
3. Metadata fill करें
4. Submit for review
5. QA team test करेगी

### Step 8: Approval & Launch
- Review: 3-7 days
- Changes request हो सकता है
- Approval के बाद live हो जाएगा

---

## 🐛 Troubleshooting

### SDK Load नहीं हो रहा?
```javascript
// Console में check करें:
console.log(typeof cacheAd);  // "function" होना चाहिए
```

### DroidHandler not found?
```
यह normal है browser testing में।
JioGames app में automatically available होगा।
```

### Ads नहीं दिख रहे?
```
Browser में test ads simulate होंगे।
Real device पर test करें JioGames app में।
```

### Keys काम नहीं कर रहे?
```javascript
// Console में key logs check करें:
// "Key pressed - Code: 50 Key: 2" दिखना चाहिए
```

---

## ✅ Pre-Submission Checklist

### Code:
- [ ] Package name updated
- [ ] Ad spot keys updated (real ones)
- [ ] Icons created (56x56, 112x112)
- [ ] manifest.webapp validated
- [ ] All console logs working
- [ ] postScore() called on game over
- [ ] Ad integration tested

### Testing:
- [ ] Browser testing done
- [ ] Key mappings work (2,4,6,8)
- [ ] SDK functions work
- [ ] No JavaScript errors
- [ ] Game playable
- [ ] Score submission works

### Assets:
- [ ] Screenshots prepared (240x320)
- [ ] App icon ready
- [ ] Description written (English & Hindi)
- [ ] Privacy policy (if needed)

### Documentation:
- [ ] manifest.webapp complete
- [ ] README updated
- [ ] Version number set
- [ ] Credits added

---

## 📞 Support

### JioGames Support:
- Dashboard: https://publish.jiogames.com
- Developer docs: https://developer.jiogames.com
- Email: support@jiogames.com

### Testing:
- KaiOS Simulator: https://developer.kaiostech.com/simulator
- Browser DevTools: F12 → Console

---

## 🎉 Summary

**Kya Complete Hai:**
✅ Manifest file (KaiOS compatible)
✅ SDK integration (full console logs)
✅ Ad functions (Interstitial + Rewarded)
✅ Leaderboard (postScore)
✅ User profile support
✅ Key mappings (JioPhone optimized)
✅ Testing ready

**Agle Steps:**
1. Icons बनाएं (56x56, 112x112)
2. Browser में test करें
3. Real ad spot keys update करें
4. JioGames dashboard पर submit करें

---

**🎮 Congratulations! आपका game JioGames के लिए ready है!**

**Testing:** `feature-phone/index.html` खोलें और Console (F12) देखें


