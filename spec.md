# Mziki Music Player - Project Specification

## Project Overview

**Project Name:** Mziki Music Player  
**Version:** 1.0.0  
**Type:** Browser-based Music Streaming Application  
**Platform:** Web (HTML/CSS/JavaScript)  
**Target Audience:** Music enthusiasts seeking a minimalist listening experience  
**Development Timeline:** 1-2 weeks  
**Status:** Production Ready

---

## Executive Summary

Mziki is a lightweight, browser-based music player that provides users with instant access to millions of songs through the Deezer API. The application emphasizes simplicity, speed, and aesthetic minimalism through a pure black and white design language. Unlike traditional music players, Mziki requires no installation, runs entirely in the browser, and offers a distraction-free listening experience.

---

## Product Vision

**Mission Statement:**  
To deliver a beautiful, fast, and accessible music discovery experience that respects user attention through minimalist design and efficient functionality.

**Core Values:**
- **Simplicity First** - Remove complexity, keep only essential features
- **Performance** - Instant loading, smooth interactions
- **Accessibility** - Works everywhere, for everyone
- **Aesthetic Discipline** - Pure black and white, no unnecessary decoration

---

## Technical Specifications

### 1. Core Technologies

| Technology | Purpose | Version |
|------------|---------|---------|
| HTML5 | Structure & Audio | Latest |
| CSS3 | Styling & Layout | Latest |
| JavaScript (ES6+) | Logic & Interaction | ES2020+ |
| Deezer API | Music Data & Streaming | v1 |
| JSONP | API Communication | N/A |

### 2. System Architecture

```
┌─────────────────────────────────────────┐
│           Browser Client                │
├─────────────────────────────────────────┤
│  UI Layer                               │
│  ├── Search Interface                   │
│  ├── Results List                       │
│  ├── Audio Player                       │
│  └── Trending Grid                      │
├─────────────────────────────────────────┤
│  Logic Layer                            │
│  ├── JSONP Handler                      │
│  ├── Playlist Manager                   │
│  ├── Audio Controller                   │
│  └── Event System                       │
├─────────────────────────────────────────┤
│  Data Layer                             │
│  └── Deezer API (JSONP)                 │
└─────────────────────────────────────────┘
```

### 3. API Integration

**Endpoint:** `https://api.deezer.com`

**Methods Used:**
- `GET /chart/0/tracks` - Fetch trending tracks
- `GET /search` - Search for tracks

**Request Format:** JSONP (bypasses CORS)
**Response Format:** JSON
**Authentication:** Not required for public endpoints

### 4. Data Models

**Track Object:**
```javascript
{
  id: number,
  title: string,
  duration: number,
  preview: string,          // 30-second MP3 URL
  artist: {
    id: number,
    name: string
  },
  album: {
    id: number,
    title: string,
    cover_small: string,
    cover_medium: string,
    cover_big: string
  }
}
```

**Playlist State:**
```javascript
{
  queue: Track[],
  currentIndex: number,
  isPlaying: boolean
}
```

---

## Functional Requirements

### FR-1: Music Search
**Priority:** High  
**Description:** Users can search for songs, artists, or albums

**Acceptance Criteria:**
- Search activates after typing 2+ characters
- Results appear within 1 second
- Debounced input (500ms delay)
- Displays up to 50 results
- Shows track name, artist, album, and duration

### FR-2: Audio Playback
**Priority:** High  
**Description:** Users can play 30-second preview clips

**Acceptance Criteria:**
- Click any track to start playback
- Play/pause toggle functionality
- Progress bar shows current position
- Time display shows current/total time
- Auto-advance to next track on completion

### FR-3: Queue Management
**Priority:** Medium  
**Description:** Users can navigate through tracks

**Acceptance Criteria:**
- Previous button goes to previous track
- Next button advances to next track
- Clicking a new track updates the queue
- Queue persists during session

### FR-4: Browse Trending
**Priority:** Medium  
**Description:** Users can discover popular music

**Acceptance Criteria:**
- Loads top 50 chart tracks on startup
- Displays 6 tracks in grid format
- Clicking trending track starts playback
- Updates weekly based on Deezer charts

### FR-5: Keyboard Controls
**Priority:** Low  
**Description:** Power users can control playback via keyboard

**Acceptance Criteria:**
- Spacebar toggles play/pause
- Only works when search bar is not focused

---

## Non-Functional Requirements

### NFR-1: Performance
- Initial page load: < 1 second
- Search response time: < 500ms
- Audio start latency: < 100ms
- Smooth 60fps UI interactions

### NFR-2: Compatibility
- Chrome 90+
- Firefox 88+
- Safari 14+
- Edge 90+
- Mobile browsers (iOS Safari, Chrome Mobile)

### NFR-3: Responsive Design
- Desktop: 1920x1080 and above
- Tablet: 768px - 1024px
- Mobile: 320px - 767px
- Orientation: Portrait and landscape

### NFR-4: Accessibility
- Keyboard navigable
- High contrast (black/white)
- Semantic HTML structure
- ARIA labels where appropriate

### NFR-5: Code Quality
- Single-file architecture
- No external dependencies
- ESLint compliant
- Comprehensive code comments
- Self-documenting variable names

---

## User Interface Specifications

### Layout Structure

**Desktop (> 1024px):**
- Two-column grid: 60% search results, 40% player
- Player sidebar is sticky
- Trending grid: 3 columns

**Tablet (768px - 1024px):**
- Single column layout
- Player appears above search results
- Trending grid: 2-3 columns

**Mobile (< 768px):**
- Single column, stacked layout
- Player at top
- Search results below
- Trending grid: 2 columns

### Color Palette

| Element | Color | Hex Code |
|---------|-------|----------|
| Background Primary | Black | #000000 |
| Background Secondary | Near Black | #0a0a0a |
| Background Card | Dark Gray | #1a1a1a |
| Text Primary | White | #ffffff |
| Text Secondary | Gray | #888888 |
| Borders | Dark Gray | #333333 |
| Hover State | Lighter Gray | #2a2a2a |

### Typography

- **Font Family:** System fonts (-apple-system, BlinkMacSystemFont, Segoe UI)
- **Headings:** 900 weight, uppercase, negative letter-spacing
- **Body Text:** 400 weight, normal case
- **Labels:** 700 weight, uppercase, 1px letter-spacing

---

## Development Phases

### Phase 1: Core Foundation (Days 1-3)
- [ ] HTML structure and semantic markup
- [ ] CSS Grid/Flexbox layout
- [ ] Basic styling (black/white theme)
- [ ] JSONP API integration
- [ ] Audio element setup

### Phase 2: Search & Display (Days 4-6)
- [ ] Search input with debouncing
- [ ] Results list rendering
- [ ] Trending grid display
- [ ] Click handlers for tracks

### Phase 3: Player Logic (Days 7-9)
- [ ] Play/pause functionality
- [ ] Progress bar interaction
- [ ] Next/previous navigation
- [ ] Auto-advance on track end
- [ ] Keyboard shortcuts

### Phase 4: Polish & Testing (Days 10-14)
- [ ] Responsive design refinement
- [ ] Cross-browser testing
- [ ] Performance optimization
- [ ] Error handling
- [ ] Documentation

---

## Risk Assessment

| Risk | Probability | Impact | Mitigation |
|------|-------------|--------|------------|
| Deezer API changes | Low | High | Abstract API calls, easy to swap |
| CORS policy changes | Medium | High | JSONP already implemented |
| Browser compatibility | Low | Medium | Use standard web APIs only |
| Performance on mobile | Medium | Medium | Optimize asset loading, lazy render |
| Preview URL unavailability | High | Low | Handle gracefully with error messages |

---

## Success Metrics

### Quantitative Metrics
- Page load time < 1s
- Search response time < 500ms
- Zero external dependencies
- 100% mobile responsive
- 95%+ browser compatibility

### Qualitative Metrics
- Clean, minimalist aesthetic
- Intuitive user experience
- Smooth, glitch-free playback
- Professional code quality
- Comprehensive documentation

---

## Future Enhancements (Out of Scope for v1.0)

1. **Playlist Management**
   - Create custom playlists
   - Save playlists to localStorage
   - Share playlists via URL

2. **User Preferences**
   - Remember volume level
   - Last played track
   - Search history

3. **Advanced Features**
   - Lyrics display
   - Artist information
   - Album view
   - Genre filtering

4. **Social Features**
   - Share tracks
   - Copy link to track
   - Tweet currently playing

5. **Customization**
   - Light mode option
   - Accent color picker
   - Layout preferences

---

## Deliverables

1. **mziki.html** - Single-file application
2. **README.md** - User and developer documentation
3. **PROJECT_SPEC.md** - This specification document
4. **Screenshots** - UI examples for documentation

---

## Maintenance Plan

### Regular Updates
- Monitor Deezer API for changes
- Update browser compatibility list
- Fix bugs reported by users

### Version Control
- Semantic versioning (MAJOR.MINOR.PATCH)
- Changelog for each release
- Git tags for versions

### Support
- GitHub Issues for bug reports
- Community-driven feature requests
- Monthly review of open issues

---

## Conclusion

Mziki represents a focused, disciplined approach to music player design. By limiting scope to essential features and embracing minimalist aesthetics, the application delivers a fast, beautiful, and accessible music discovery experience. The single-file architecture ensures simplicity in deployment and maintenance, while the JSONP integration guarantees cross-origin compatibility without server-side dependencies.

---

**Document Version:** 1.0  
**Last Updated:** February 2026  
**Author:** Mziki Development Team
