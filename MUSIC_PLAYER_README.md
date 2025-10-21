# Dana N'kassa Music Player

A beautiful, Apple-inspired music player with chromatic audio visualization and smooth GSAP animations.

## 🎨 Features

### Visual Design
- **Chromatic Visualizer**: WebGL-based circular audio visualizer with real-time frequency analysis
- **White Background**: Clean, minimal white background with dynamic chromatic overlay when playing
- **Glass Morphism**: Frosted glass effects throughout the interface
- **Apple-Inspired**: Design inspired by iOS and AirPods 4 campaign

### Animations (GSAP)
- **Smooth Scrolling**: Hardware-accelerated smooth scrolling with ScrollTrigger
- **Card Entrance**: Staggered animations for track cards (0.05s delay per card)
- **Header Animation**: Slide-down effect with fade-in
- **Hover Effects**: Smooth lift and scale on card hover
- **Player Expansion**: Fluid expand/collapse animations for player controls
- **Body Fade-In**: Elegant page load animation

### Audio Features
- **23 Tracks**: Complete track listing for Dana N'kassa's music
- **Audio Controls**: Play/pause, seek, time display, loop
- **Single Playback**: Automatically pauses other tracks when playing
- **Format Support**: Both MP3 and WAV file formats
- **Real-time Sync**: Visualizer perfectly syncs with audio tempo

### Technical Implementation
- **WebGL Rendering**: High-performance visualizer with optimized rendering
- **Web Audio API**: Professional-grade audio analysis (FFT size: 256)
- **Frequency Mapping**: 
  - Red channel: Bass frequencies
  - Green channel: Mid frequencies
  - Blue channel: High frequencies
- **Multi-layer Depth**: Three visualization layers for depth effect
- **Responsive Design**: Mobile-optimized layout

## 📁 Project Structure

```
/app/frontend/
├── src/
│   ├── components/
│   │   ├── MusicPlayer.js          # Main music player component
│   │   └── MusicPlayer.css         # Styling with glass morphism
│   ├── App.js                      # App integration
│   ├── index.css                   # Global styles with smooth scrolling
│   └── index.js                    # Entry point
└── public/
    ├── AUDIO_FILES_README.md       # Audio files documentation
    └── [audio files]               # MP3/WAV files go here
```

## 🎵 Audio Files Setup

### Required Files
Place all audio files in `/app/frontend/public/` directory:

```
NM-205.mp3  NM-209.mp3  NM-208.mp3  NM-197.mp3  NM-153.mp3
NM-155.mp3  NM-157.mp3  NM-156.mp3  NM-158.mp3  NM-120.mp3
NM-092.mp3  NM-087.mp3  NM-046.mp3  NM-027.mp3  NM-044.mp3
NM-042.mp3  NM-064.mp3  NM-084.mp3  NM-079.mp3  NM-073.mp3
NM-072.mp3  NM-020.mp3  NM-037.mp3
```

### File Formats
- **Primary**: MP3 (recommended 128kbps or higher)
- **Fallback**: WAV (lossless quality)
- Component automatically tries both formats

### Adding Your Files
1. Copy audio files to `/app/frontend/public/`
2. Ensure exact naming (case-sensitive)
3. Refresh the page - player will auto-load them

## 🚀 Running the Application

### Start Development Server
```bash
cd /app/frontend
yarn start
```

### Build for Production
```bash
cd /app/frontend
yarn build
```

### Restart Services
```bash
sudo supervisorctl restart frontend
```

## 🎨 Customization

### Colors
Edit `/app/frontend/src/components/MusicPlayer.css`:
```css
/* Primary accent color */
.play-btn {
  background: linear-gradient(135deg, #007aff, #0051d5);
}

/* Visualizer colors (in MusicPlayer.js) */
const r = 0.3 + lowFreq * 0.7;   // Red (bass)
const g = 0.2 + midFreq * 0.6;   // Green (mids)
const b = 0.8 + highFreq * 0.2;  // Blue (highs)
```

### Animation Timing
Edit `/app/frontend/src/components/MusicPlayer.js`:
```javascript
// Card entrance delay
delay: 0.6 + index * 0.05  // Increase for slower stagger

// Hover animation duration
duration: 0.5  // Adjust for faster/slower hovers
```

### Visualizer Settings
```javascript
// FFT size (frequency resolution)
analyserRef.current.fftSize = 256;  // 128, 256, 512, etc.

// Blur amount
filter: blur(80px)  // Increase for more blur

// Opacity
opacity: 0.65  // Adjust visualizer visibility
```

## 🎯 Key Technologies

- **React 19**: Latest React with hooks
- **GSAP 3.13**: Professional animation library
- **WebGL**: Hardware-accelerated graphics
- **Web Audio API**: Real-time audio analysis
- **CSS**: Modern CSS with backdrop-filter
- **Tailwind CSS**: Utility-first CSS framework

## 📱 Browser Support

- **Chrome/Edge**: Full support ✅
- **Firefox**: Full support ✅
- **Safari**: Full support ✅
- **Mobile**: iOS Safari, Chrome Mobile ✅

## 🔧 Troubleshooting

### Visualizer Not Showing
- Check if audio is playing
- Verify Web Audio API support: `window.AudioContext`
- Check browser console for WebGL errors

### Audio Not Playing
- Verify audio files are in `/app/frontend/public/`
- Check file naming (case-sensitive)
- Open browser console for error messages
- Test with sample .wav files first

### Animations Stuttering
- Reduce number of visualizer layers
- Lower FFT size (128 instead of 256)
- Check CPU usage (should be <30%)

### Mobile Issues
- Ensure audio files aren't too large
- Test on WiFi first (not cellular)
- Check for iOS audio playback restrictions

## 💡 Performance Tips

1. **Optimize Audio Files**: 
   - Use 128-192kbps MP3 for web
   - Avoid unnecessarily large files

2. **Visualizer Performance**:
   - FFT size 256 is optimal balance
   - Reduce blur if needed (60px instead of 80px)
   - Limit to 2 layers instead of 3

3. **Animation Performance**:
   - GSAP uses hardware acceleration
   - All transforms use GPU
   - ScrollTrigger is optimized for 60fps

## 📝 Notes

- Audio files need to be uploaded from your GitHub repository
- 3 sample .wav files provided for initial testing
- Visualizer automatically adapts to any audio tempo
- Design follows Apple's HIG (Human Interface Guidelines)
- All animations use cubic-bezier easing for natural motion

## 🎬 Demo Features

Click any track card to:
1. See smooth GSAP expansion animation
2. Access play/pause controls
3. Scrub through the timeline
4. Toggle loop mode
5. Watch chromatic visualizer sync with audio

## 📧 Contact

Dana N'kassa - contact.danankassa@gmail.com

---

**Made with ❤️ using React, GSAP, and WebGL**
