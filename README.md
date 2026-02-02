# Mziki Music Player

![Mziki](https://img.shields.io/badge/version-1.0.0-black)
![License](https://img.shields.io/badge/license-MIT-white)
![Status](https://img.shields.io/badge/status-active-black)

A minimalist, browser-based music player featuring a sleek black and white design with real-time music search and streaming capabilities powered by the Deezer API.

## ✨ Features

- **🎵 Real-time Music Search** - Search millions of tracks from Deezer's catalog
- **📋 List View Results** - Browse search results in a clean, organized list format
- **▶️ Audio Playback** - Stream 30-second preview clips of any track
- **🎨 Minimalist Design** - Pure black and white aesthetic with geometric precision
- **📱 Responsive Layout** - Works seamlessly on desktop, tablet, and mobile devices
- **⌨️ Keyboard Shortcuts** - Spacebar to play/pause for quick control
- **🔄 Auto-advance** - Automatically plays the next track in queue
- **🎯 Trending Section** - Discover popular tracks in a grid layout
- **🚫 No CORS Issues** - Uses JSONP for seamless API integration

## 🚀 Quick Start

### Installation

No installation required! Simply open the HTML file in any modern web browser.

```bash
# Clone or download the file
# Open mziki.html in your browser
```

### Usage

1. **Search for music** - Type artist names, song titles, or albums in the search bar
2. **Browse results** - Click any track from the list to start playing
3. **Control playback** - Use the player controls or press spacebar to play/pause
4. **Navigate tracks** - Use previous/next buttons or click tracks from the trending section

## 🎮 Controls

| Action | Method |
|--------|--------|
| Play/Pause | Click play button or press `Spacebar` |
| Previous Track | Click ⏮ button |
| Next Track | Click ⏭ button |
| Seek | Click anywhere on the progress bar |
| Search | Type in the search bar (auto-search after 2+ characters) |

## 🛠️ Technical Stack

- **HTML5** - Semantic markup and audio element
- **CSS3** - Custom properties, Grid, Flexbox
- **Vanilla JavaScript** - No frameworks or dependencies
- **Deezer API** - Music data and streaming via JSONP
- **JSONP** - Cross-origin resource sharing workaround

## 🏗️ Architecture

### Key Components

1. **Search Engine**
   - Real-time search with 500ms debounce
   - JSONP requests to bypass CORS restrictions
   - Dynamic result rendering

2. **Audio Player**
   - HTML5 Audio API integration
   - Progress tracking and seeking
   - Queue management system

3. **UI Layout**
   - Two-column grid layout (search results + player)
   - Sticky player sidebar
   - Responsive breakpoints for mobile

### Code Structure

```
mziki.html
├── HTML Structure
│   ├── Header (branding + search)
│   ├── Main Layout
│   │   ├── Search Results (list view)
│   │   └── Player (sticky sidebar)
│   └── Trending Section (grid)
│
├── CSS Styling
│   ├── CSS Variables (theme colors)
│   ├── Layout (Grid/Flexbox)
│   ├── Components (cards, lists, player)
│   └── Responsive (media queries)
│
└── JavaScript Logic
    ├── JSONP API wrapper
    ├── Search functionality
    ├── Playlist management
    ├── Audio controls
    └── Event handlers
```

## 🎨 Design Philosophy

Mziki embraces a **brutalist design** approach:

- **No gradients** - Pure black (#000) and white (#fff)
- **No rounded corners** - Sharp, geometric shapes
- **Minimal borders** - Subtle dividers (#333)
- **Typography** - System fonts for maximum performance
- **Contrast** - High contrast for accessibility

## 🔧 Customization

### Theme Colors

Modify the CSS variables in `:root`:

```css
:root {
    --bg-primary: #000000;
    --bg-secondary: #0a0a0a;
    --bg-card: #1a1a1a;
    --text-primary: #ffffff;
    --text-secondary: #888888;
    --border: #333333;
}
```

### API Configuration

The Deezer API is used via JSONP. To modify API endpoints:

```javascript
const DEEZER_API = 'https://api.deezer.com';

// Chart endpoint
jsonp(`${DEEZER_API}/chart/0/tracks?limit=50`)

// Search endpoint
jsonp(`${DEEZER_API}/search?q=${query}&limit=50`)
```

## 📊 Browser Support

| Browser | Version | Status |
|---------|---------|--------|
| Chrome | 90+ | ✅ Fully Supported |
| Firefox | 88+ | ✅ Fully Supported |
| Safari | 14+ | ✅ Fully Supported |
| Edge | 90+ | ✅ Fully Supported |

## ⚠️ Limitations

- **30-second previews** - Deezer API provides 30-second clips only
- **No offline mode** - Requires internet connection
- **Preview availability** - Some tracks may not have preview URLs
- **Rate limits** - Deezer API has usage limits (not enforced for JSONP)

## 🤝 Contributing

Contributions are welcome! To contribute:

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/amazing-feature`)
3. Commit your changes (`git commit -m 'Add amazing feature'`)
4. Push to the branch (`git push origin feature/amazing-feature`)
5. Open a Pull Request

### Development Guidelines

- Maintain the minimalist black and white aesthetic
- Keep the single-file structure
- No external dependencies
- Ensure mobile responsiveness
- Test across major browsers

## 📝 License

This project is licensed under the MIT License - see below for details:

```
MIT License

Copyright (c) 2026 Mziki Music Player

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.
```

## 🙏 Acknowledgments

- **Deezer** - For providing the music API and preview streams
- **Modern web standards** - HTML5, CSS3, ES6+
- **Open source community** - For inspiration and best practices

## 📧 Contact

For questions, feedback, or issues, please open an issue on the repository.

---

**Made with ♪ by the Mziki team**

*Swahili: "Mziki" means "Music"*
